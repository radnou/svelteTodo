<script lang="ts">
	interface todo {
		id: number;
		description: String;
		completed: Boolean;
	}
	let todos = [
		{
			id: 1,
			description: 'my first todo ',
			completed: false
		}
	];
	$: totalTodos = todos.length;
	$: completedTodos = todos.filter((todo) => todo.completed);

	let newItem = '';

	function newTodo() {
		todos = [...todos, { id: todos.length, description: newItem, completed: false }];
		newItem = '';
	}

	function removeTodo(todo: todo) {
		todos = todos.filter((t) => t.id !== todo.id);
	}
</script>

<title>Todo List</title>
<h1>Todos list</h1>
<h3>Number of todo: {totalTodos}</h3>

{#each todos as todo, index}
	<p>
		<input bind:checked={todo.completed} type="checkbox" />
		{todo.description}
		<button on:click={removeTodo(todo)}>❌</button>
	</p>
{/each}

{JSON.stringify(todos)}

<h2>Add todo:</h2>
<label for="todoInput">Description </label><input
	type="text"
	bind:value={newItem}
	placeholder="What do you want to list ?"
/>
<button on:click|preventDefault={newTodo}>Add todo</button>
