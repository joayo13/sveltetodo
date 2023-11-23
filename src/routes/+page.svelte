<script>
let list = []
let text = ''
let time = null
function updateText(textChars) {
  text = textChars
}
function addToList() {
  if(text && time) {
    const item = { id: list.length, title: text, time: time}
    list = [...list, item]
    text = ''
    time = null
  }
}
function removeFromList(item) {
  list = list.filter((listItem) => listItem.id !== item.id)
}
</script>
<style>
  .app-container {
    position: absolute;
    left: 50%;
    transform: translateX(-50%);
  }
  .todo-list {
    list-style-type: none;
  }
  .todo-item {
    padding: 1rem;
    width: 12rem;
    display: flex;
    flex-direction: column;
  }
  .todo-form {
    padding: 1rem;
    width: 12rem;
    display: flex;
    flex-direction: column;
    gap: 1rem;
  }
</style>
<section class="app-container">
  <h1>Todo App With Svelte</h1>
  <ul class="todo-list">
    {#each list as item}
    <li class="todo-item">
      <p>{item.title}</p>
      <p>{item.time}</p>
      <button on:click={removeFromList(item)}>Remove</button>
    </li>
    {/each}
  </ul>
  <form on:submit={addToList} class="todo-form">
  <input placeholder="Todo Title" bind:value={text} type="text"/>
  <input bind:value={time} type="datetime-local"/>
  <button>Add Todo</button>
</form>
</section>