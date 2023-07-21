<script>
  import Form from "./Form.svelte";
  import FeedbackList from "./FeedbackList.svelte";
  import Notification from "./Notification.svelte";
  let data = [
    {
      id: 1,
      text: ` Lorem ipsum dolor sit amo
   `,
      rating: 6,
    },
  ];

  let notificationData = {
    text: null,
    type: null,
  };

  const handleAdd = (event) => {
    data = [event.detail, ...data];
  };
</script>

<main class="container">
  <div class="app">
    <Form
      on:add-feedback={handleAdd}
      on:remove-notifiction={() => (notificationData = { text: null })}
      on:notify={(e) => (notificationData = e.detail)}
    />
    <FeedbackList
      list={data}
      on:remove-feedback={(e) => (data = data.filter((x) => x.id !== e.detail))}
    />
  </div>
  {#if notificationData.text}
    <Notification {notificationData} />
  {/if}
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
