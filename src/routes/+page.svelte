<script>
	let todos = [
		{
			id: 1,
			description: 'my first todo ',
			completed: false
		}
	];
	let newItem = '';

	function newTodo() {
	
		todos = [...todos, { id: todos.length, description: newItem, completed: false }];
		newItem = '';
	}
</script>

<h1>Todos list</h1>

<ul>
	{#each todos as todo, index}
		<li id={index}>{todo.description}</li>
	{/each}
</ul>

<h2>Add todo:</h2>
<label for="todoInput">Description </label><input
	type="text"
	bind:value={newItem}
	placeholder="What do you want to list ?"
/>
<button on:click|preventDefault={newTodo}>Add todo</button>
