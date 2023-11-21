<script>
let list = ['Make poop', 'Fart',]
let text = ''
function updateText(textChars) {
  text = textChars
}
function addToList() {
    list = [...list, text]
    text = ''
}
</script>

<h1>Todo App</h1>
<h3>{text}</h3>
<ul>{list}</ul>
<input bind:value={text} type="text"/>
<button on:click={addToList}>Add Todo</button>
