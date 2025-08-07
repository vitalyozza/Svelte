<script>
	import { slide, fade } from 'svelte/transition';

	let count = $state(0);
	let countShow = $state(true);

	let increase = () => {
		count += 1;
	};

	let decrease = () => {
		count -= 1;
	};
</script>

{#if countShow}
	<span transition:fade>
		<button onclick={decrease}>-</button>
		{#key count}
			<div style="width: 18px; text-align: center;" transition:slide>{count}</div>
		{/key}
		<button onclick={increase}>+</button>
	</span>
{/if}
<br />
<label for="countShow">
	<input type="checkbox" name="countShow" id="countShow" bind:checked={countShow} /> show count
</label>
