<script>
  import Radio from "./Radio.svelte";
  import { createEventDispatcher } from "svelte";
  let radioArray = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];
  let feedbackText = "";
  let rating = null;
  const dispatch = createEventDispatcher();
  const handleChange = (e) => {
    feedbackText = e.target.value;
  };

  const handleSubmit = () => {
    if (rating) {
      dispatch("add-feedback", {
        text: feedbackText,
        rating,
        id: Math.random(),
      });
      feedbackText = "";
    } else {
      dispatch("notify", {
        type: "error",
        text: "You have to set your rating",
      });
      setTimeout(() => {
        dispatch("remove-notifiction");
      }, 2000);
    }
  };
</script>

<form class="feedbackForm" on:submit|preventDefault={handleSubmit}>
  <div class="radios">
    {#each radioArray as rad}
      <Radio
        on:set-rating={(e) => (rating = e.detail)}
        {rating}
        value={rad}
        id={`rad-${rad}`}
      />
    {/each}
  </div>
  <div class="feedback-input">
    <input type="text" on:input={handleChange} value={feedbackText} />
    <button type="submit">done</button>
  </div>
</form>

<style>
  .feedbackForm {
    display: flex;
    flex-direction: column;
    align-items: center;
    margin-top: 10vh;
    width: 70%;
  }
  .feedbackForm > .radios {
    width: 100%;
    display: flex;
    justify-content: space-between;
  }
  .feedbackForm > div {
    margin-top: 20px;
  }
  input {
    outline: none;
  }
  input[type="text"]:focus-visible {
    border: 1px solid #ff5733;
  }

  .feedback-input {
    width: 100%;
    display: flex;
  }
  .feedback-input > input {
    flex: 0.9;
    border-radius: 5px 0 0 5px;
  }
  .feedback-input > button {
    flex: 0.1;
    background: #ff5733;
    border-radius: 0 5px 5px 0;
  }
</style>
