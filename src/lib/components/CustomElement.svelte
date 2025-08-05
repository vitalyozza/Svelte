<svelte:options customElement="my-stepper"/>

<script lang="ts">
    function dispatch(type) {
        $host().dispatchEvent(new CustomEvent(type))
    }
</script>

<button onclick={() => dispatch('decrement')}>decrement</button>
<button onclick={() => dispatch('increment')}>increment</button>