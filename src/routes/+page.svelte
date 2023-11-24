

<script>
let list = []
let text = ''
let time = null
function addToList() {
  if(text && time) {
    const item = { id: list.length, title: text, time: time, checked: false}
    list = [...list, item]
    text = ''
    time = null
  }
}
function removeFromList(item) {
  list = list.filter((listItem) => listItem.id !== item.id)
}
function editFromList(item) {
  list = list.filter((listItem) => listItem.id !== item.id)
  time = item.time
  text = item.title
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
    padding: 0;
  }
  .todo-item {
    position: relative;
    background-color: darkslategrey;
    color: rgb(218, 218, 218);
    list-style-type: none;
    padding: 1rem;
    width: 12rem;
    flex-direction: column;
  }
  .todo-item-button-container {
    display: inline;
  }
  .todo-item-checkbox {
    position: absolute;
    top: 0.5rem;
    right: 0.5rem;
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
      <span class="todo-item-button-container">
        <button on:click={editFromList(item)}>Edit Todo</button>
        <button on:click={removeFromList(item)}>Remove Todo</button>
      </span>
      <input class="todo-item-checkbox" type="checkbox"/>
    </li>
    {/each}
  </ul>
  <form on:submit={addToList} class="todo-form">
  <input placeholder="Todo Title" bind:value={text} type="text"/>
  <input bind:value={time} type="datetime-local"/>
  <button>Add Todo</button>
</form>
</section>