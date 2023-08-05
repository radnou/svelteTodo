<script lang="ts">
	import type item from '$lib/type/item.svelte';
	export let menu: item[] = [];
</script>

<nav class="navbar navbar-center">
	<ul class="menu menu-horizontal">
		{#each menu as item}
			<li>
				<a href="/{item.path}" class="link link-primary">{item.label.toUpperCase()}</a>
			</li>
		{/each}

		<!--		<li>-->
		<!--			<a href="/introduction" class="link link-primary">Introduction</a>-->
		<!--		</li>-->
		<!--		<li>-->
		<!--			<a href="/reactivity" class="link link-primary">Reactivity</a>-->
		<!--		</li>-->
		<!--		<li>-->
		<!--			<a href="/props" class="link link-primary">Props</a>-->
		<!--		</li>-->
	</ul>
</nav>
