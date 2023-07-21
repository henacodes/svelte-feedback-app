<script>
  import FeedBack from "./FeedBack.svelte";
  export let list = [];

  const removeFeedback = (e) => {
    list = list.filter((x) => x.id !== e.detail);
  };
</script>

<div class="feedbackList">
  {#each list as feedback (feedback.id)}
    <FeedBack {feedback} on:remove-rating={removeFeedback} />
  {/each}
</div>

<style>
  .feedbackList {
    height: 72vh;
    overflow-y: scroll;
    -webkit-mask-image: linear-gradient(to top, transparent 0%, black 20%);
    mask-image: linear-gradient(to top, transparent 0%, black 20%);
  }
</style>
