<script>
	import { fade } from 'svelte/transition';
	let books = ['Learning Svelte', 'The Zen of Cooking Tea'];
	let newBook = '';
	function addBook(evt) {
	if (evt.key === 'Enter') {
	books = [...books, newBook];
	newBook = '';
	}
	}

	let todos=[];
	let newTodo = '';
function handleKeyup(evt) {
if (evt.key === 'Enter') {
todos = [...todos, newTodo];
newTodo = '';
}
}
</script>
<label>
	<h4>Add Book</h4>
	<input type="text" bind:value={newBook} on:keydown={addBook} />
	</label>
	<h4>My Books</h4>
	<ul>
	{#each books as book}
	<li transition:fade>{book}</li>
	{/each}
	</ul>

	<label>
		New To-Do
		<!-- To implement: make this update the list -->
		<input type="text" bind:value={newTodo} on:keyup={handleKeyup} />
	</label>
		{#if todos.length === 0}
		<p>What do you want to work on?</p>
		{:else}
		<ul>
		{#each todos as todo}
		<li>{todo}</li>
		{/each}
		</ul>
		{/if}


<!-- script and html code... -->
<style>
	input {
	padding: 5px 10px;
}
li {
	color: #ff4500;
	list-style: none;
	}
	ul {
	padding: 5px 0;
	}
	</style>

	