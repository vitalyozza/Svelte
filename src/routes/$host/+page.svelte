<script lang="ts">
	import '$lib/components/CustomElement.svelte';

	let count = $state(0);
</script>

<my-stepper 
    ondecrement={() => (count -= 1)} 
    onincrement={() => (count += 1)}
></my-stepper>

<p>Count: {count}</p>
