<script lang="ts">
	let string = `this string contains some <strong>HTML!!!</strong>`;
</script>

<p>{@html string}</p>
<p class="styledp">This is a paragraph.</p>

<style>
	.styledp {
		color: goldenrod;
		font-family: 'Comic Sans MS', cursive;
		font-size: 2em;
	}
</style>
