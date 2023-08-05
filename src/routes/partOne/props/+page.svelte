<script lang="ts">
	import Nested from './Nested.svelte';

    	import PackageInfo from './PackageInfo.svelte';

	const pkg = {
		name: 'svelte',
		speed: 'blazing',
		version: 4,
		website: 'https://svelte.dev'
	};
</script>

<h1>Props</h1>
<Nested answer={43} />
<hr>
<Nested/>
<hr>
<PackageInfo {...pkg}/>
