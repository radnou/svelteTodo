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
		},
		{
			id: 2,
			description: 'chores',
			completed: false
		},
		{
			id: 3,
			description: 'shopping',
			completed: false
		},
		{
			id: 4,
			description: 'svelte tuto',
			completed: false
		}
	];
	$: totalTodos = todos.length;
	$: completedTodos = todos.filter((todo) => todo.completed);

	let newItem = '';

	function newTodo() {
		newItem = newItem.trim();
		if (!newItem) return;
		todos = [...todos, { id: todos.length + 1, description: newItem, completed: false }];
		newItem = '';
		OrderTodo();
	}

	function removeTodo(todo: todo) {
		todos = todos.filter((t) => t.id !== todo.id);
		OrderTodo();
	}

	function completeTask(index) {
		todos[index].completed = !todos[index].completed;
		OrderTodo();
		return;
	}

	function OrderTodo() {
		todos.sort((a, b) => {
			return a.completed > b.completed;
		});
	}
</script>

<title>Todo List</title>
<h1>Todos list</h1>
<h3>Number of todo: {totalTodos}</h3>
<ul role="list">
	{#each todos as todo, index}
		<li class:checked={todo.completed}>
			<input on:click={() => completeTask(index)} type="checkbox" />
			{todo.description}
			<!-- svelte-ignore a11y-click-events-have-key-events -->
			<!-- svelte-ignore a11y-no-static-element-interactions -->
			<span on:click={() => removeTodo(todo)}>❌</span>
		</li>
	{/each}
</ul>

<!-- {JSON.stringify(todos)} -->

<h2 class="text-3xl font-bold underline">Add todo:</h2>
<label for="todoInput">Description </label><input
	type="text"
	bind:value={newItem}
	placeholder="What do you want to list ?"
/>
<button class="btn btn-primary" on:click|preventDefault={newTodo}>Add todo</button>

<style>
	.checked {
		text-decoration: line-through;
	}
</style>
