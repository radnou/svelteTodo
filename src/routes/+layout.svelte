<script lang="ts">
	import '../app.css';
	import Navbar from '$lib/components/navbar.svelte';

	let menu = [
		{
			path: '',
			label: 'Home'
		},
		{
			path: 'partOne',
			label: 'Part 1 : Basic Svelte'
		},
		{
			path: 'partTwo',
			label: 'Part 2 : Advanced Svelte'
		},
		{
			path: 'partThree',
			label: 'Part 3 : Basic SvelteKit'
		},
		{
			path: 'partFour',
			label: 'Part 4 : Advanced SvelteKit'
		}
	];
</script>

<Navbar {menu} />
<slot />
