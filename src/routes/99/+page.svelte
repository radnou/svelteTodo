<script>
	import { fade } from 'svelte/transition';
	import { elasticOut } from 'svelte/easing';

	let visible = true;

	function spin(node, { duration }) {
		return {
			duration,
			css: t => {
				const eased = elasticOut(t);

				return `
					transform: scale(${eased}) rotate(${eased * 1080}deg);
					color: hsl(
						${Math.trunc(t * 360)},
						${Math.min(100, 1000 * (1 - t))}%,
						${Math.min(50, 500 * (1 - t))}%
					);`
			}
		};
	}

	function typewriter(node,{speed=1}) {
		const valid = node.childNodes.length === 1 && node.childNodes[0].nodeType === Node.TEXT_NODE;
		if (!valid) {
			throw new Error(`this transition only works on elements with a single text node child `);
		}
		const text = node.textContent;
		const duration = text.length / (speed *0.01);
		return {
			duration,
			tick:(t)=> {
				const i = Math.trunc(text.length * t);
				node.textContent = text.slice(0,i);
			}
		};
	}
</script>

<label>
	<input type="checkbox" bind:checked={visible} />
	visible
</label>

{#if visible}
	<p transition:typewriter>
		The quick brown fox jumps over the lazy dog
	</p>
<div class="centered"
in:spin={{duration:800}}
out:fade>
	<span>transition</span>
</div>

{/if}

<style>
	.centered{
		position: absolute;
		left: 50%;
		top: 50%;
	}
</style>