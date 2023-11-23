<script>
let list = ['Make poop', 'Fart',]
let text = ''
function updateText(textChars) {
  text = textChars
}
function addToList() {
  if(text)
    list = [...list, text]
    text = ''
}
</script>
<style>
  .app-container {
    position: absolute;
    left: 50%;
    transform: translateX(-50%);
  }
  .todo-item {
    padding: 1rem;
    width: 12rem;
    display: flex;
    justify-content: space-between;
  }
</style>
<section class="app-container">
  <h1>Todo App With Svelte</h1>
  <ul>
    {#each list as item}
    <li class="todo-item">{item}<button>Remove</button></li>
    {/each}
  </ul>
  <input bind:value={text} type="text"/>
  <button on:click={addToList}>Add Todo</button>
</section>