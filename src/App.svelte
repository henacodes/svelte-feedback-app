<script>
  import Form from "./Form.svelte";
  import FeedbackList from "./FeedbackList.svelte";
  import { onMount } from "svelte";
  let data = [
    {
      id: 1,
      text: ` Lorem ipsum dolor sit amet consectetur adipisicing elit. Quibusdam optio
    neque quidem, magnam fugit pariatur exercitationem id rerum at nulla
    excepturi consequuntur, vitae, temporibus ducimus! Voluptate accusantium
    doloribus nam consequuntur.`,
      rating: 6,
    },
  ];

  onMount(() => {
    addEventListener("updatedData", (e) => {
      console.log("evevtn hapejds");
      console.log(data);
      data = [e.detail, ...data];
      console.log(data);
    });
  });
</script>

<main class="container">
  <div class="app">
    <Form />
    <FeedbackList list={data} />
  </div>
</main>

<style>
  .app {
    background: white;
    display: flex;
    flex-direction: column;
    align-items: center;
    width: 50%;
    height: 100%;
    box-shadow: 0 0 50px 10px rgb(0, 0, 0, 0.24);
  }
  .container {
    background-color: #202142;
    height: 100%;
    display: flex;
    flex-direction: column;
    align-items: center;
  }
</style>
