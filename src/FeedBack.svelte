<script>
  export let feedback;
  import { createEventDispatcher } from "svelte";

  const dispatch = createEventDispatcher();

  const handleRemove = () => {
    dispatch("remove-feedback", feedback.id);
  };
</script>

<div class="feedback">
  <p class="text">
    {feedback.text}
  </p>
  <div class="rating">
    <p class="rating">rating: {feedback.rating}</p>
    <p class="closeBtn" on:click={handleRemove}>X</p>
  </div>
</div>

<style>
  .feedback {
    margin: 10px;
    border: 1px solid #ff5733;
    border-radius: 5px;
    padding: 10px;
    display: flex;
    align-items: center;
    background: #ff58331f;
  }
  .feedback > .text {
    flex: 0.85;
  }
  .feedback > .rating {
    flex: 0.15;
    display: flex;
    justify-content: space-between;
    align-items: center;
  }

  .closeBtn {
    background: #ff5733;
    padding: 5px;
    border-radius: 50%;
    width: 30px;
    height: 30px;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    font-size: large;
    font-weight: bolder;
    color: white;
    cursor: pointer;
  }
</style>
