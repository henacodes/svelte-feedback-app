<script>
  import { createEventDispatcher } from "svelte";
  export let value = 0;
  export let id = "";
  export let rating;
  const dispatch = createEventDispatcher();
</script>

<input
  class="rating"
  type="radio"
  name="rating"
  {id}
  {value}
  checked="true"
  on:change={(e) => dispatch("set-rating", e.currentTarget.value)}
/>

<style>
  input[type="radio"] {
    appearance: none;
    background-color: #cacaca;
    border-radius: 50%;
    border: 2px solid #ccc;
    box-sizing: border-box;
    height: 20px;
    width: 20px;
    margin-right: 10px;
    vertical-align: middle;
  }

  input[type="radio"]:checked {
    background-color: #ff5733;
    border-color: #ff5733;
  }
</style>
