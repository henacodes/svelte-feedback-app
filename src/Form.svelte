<script>
  import Radio from "./Radio.svelte";
  const handleSubmit = (e) => {
    e.preventDefault();
    console.log(`rating ${rating} `, `comment ${feedbackText}`);
    const event = new CustomEvent("updatedData", {
      detail: { text: feedbackText, rating: rating, id: Math.random() },
    });
    dispatchEvent(event);
    feedbackText = "";
  };

  const handleChange = (e) => {
    feedbackText = e.target.value;
  };

  let rating = 0;
  let feedbackText = "";
  const radioArray = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];

  const handleRating = (e) => {
    rating = e.detail;
  };
</script>

<form class="feedbackForm" on:submit={handleSubmit}>
  <div class="radios">
    {#each radioArray as rad}
      <Radio
        {rating}
        value={rad}
        id={`rad-${rad}`}
        on:set-rating={handleRating}
      />
    {/each}
  </div>
  <div class="feedback-input">
    <input type="text" on:change={handleChange} value={feedbackText} />
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
