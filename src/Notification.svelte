<script>
  import { scale } from "svelte/transition";
  export let notificationData = {};
</script>

<div
  transition:scale
  class={`notification ` +
    (notificationData.type == "error" ? "error" : "info")}
>
  <p>{notificationData.text}</p>
</div>

<style>
  .notification {
    position: fixed;
    bottom: 5%;
    right: 5%;
    padding: 10px;
    background: #f4f4f4;
    border-radius: 5px;
    transition: linear 0.2s;
  }
  .error {
    border: 2px solid lightcoral;
  }
  .info {
    border: 2px solid rgb(93, 93, 246);
  }
</style>
