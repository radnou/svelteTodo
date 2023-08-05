<script lang="ts">
	let numbers = [1, 2, 3, 4, 5];

	function addNumber() {
		numbers = [...numbers, numbers.length + 2];
	}

	$: sum = numbers.reduce((t, c) => t + c, 0);
</script>

<h1>Arrays Update</h1>
<p>{numbers.join(' + ')} = {sum}</p>
<button class="btn btn-info" on:click={addNumber}>Add A number</button>
