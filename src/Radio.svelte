<!-- Radio.svelte -->
<script>
  import { createEventDispatcher } from "svelte";

  const dispatch = createEventDispatcher();
  export let id = "";
  export let value = "";
  let checked = false;

  const handleRadios = (e) => {
    checked = e.currentTarget.checked;
    dispatch("set-rating", e.currentTarget.value);
  };
</script>

<div class="radio-container">
  <input type="radio" name="rating" {id} {value} on:change={handleRadios} />
  <label for={id} class="radio-label">{value}</label>
</div>

<style>
  .radio-container {
    position: relative;
    display: inline-block;
    margin-right: 10px;
  }

  input[type="radio"] {
    appearance: none;
    background-color: #f2f2f2;
    border-radius: 50%;
    border: 2px solid #ccc;
    box-sizing: border-box;
    height: 50px;
    width: 50px;
    margin: 0;
    vertical-align: middle;
  }

  input[type="radio"]:checked {
    background-color: #ff5733;
    border-color: #ff5733;
  }

  .radio-label {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    font-size: 14px;
  }
</style>
