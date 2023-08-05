<script lang="ts">
	let count = 0;

	function increment() {
		count++;
	}

	// declaration
	$: doubled = count * 2;

	// statements
	$: console.log(`the count is ${count}`);

	$: if (count >= 20) {
		alert('count is dangerously high!');
		count = 0;
	}
</script>

<ul class="navbar">
	<li><a href="/reactivity/arrays" class="link link-info">Arrays Update</a></li>
</ul>
<h1 class="text-xl">Reactivity</h1>
<h3>Assignments</h3>
<button class="btn btn-primary" on:click={increment}>
	Clicked {count}
	{count === 1 ? 'time' : 'times'}
</button>

<h3>Declarations</h3>

<p>{count} doubled is {doubled}</p>

<h4>Statements</h4>
{#if count < 10}
	<p>{count} is less than 10</p>
{:else if count > 10}
	<p>{count} is <b>more</b> than 10</p>
{/if}
