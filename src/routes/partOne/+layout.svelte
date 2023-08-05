<script lang="ts">
	import Navbar from '$lib/components/navbar.svelte';

	let menu = [
		{
			path: 'partOne/introduction',
			label: 'a - Introduction'
		},
		{
			path: 'partOne/reactivity',
			label: 'b - Reactivity'
		},
		{
			path: 'partOne/props',
			label: 'c - Props'
		},
		{
			path: 'partOne/logic',
			label: 'd - logic '
		}
	];
</script>

<Navbar {menu} />
<slot />
