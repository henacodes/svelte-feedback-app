<script>
  import FeedBack from "./FeedBack.svelte";
  import { fade, scale } from "svelte/transition";
  export let list = [];
</script>

<div class="feedbackList">
  {#each list as feedback (feedback.id)}
    <div in:scale out:fade={{ duration: 500 }}>
      <FeedBack {feedback} on:remove-feedback />
    </div>
  {/each}
</div>

<style>
  .feedbackList {
    height: 72vh;
    overflow-y: scroll;
    width: 100%;
    -webkit-mask-image: linear-gradient(to top, transparent 0%, black 20%);
    mask-image: linear-gradient(to top, transparent 0%, black 20%);
  }
</style>
