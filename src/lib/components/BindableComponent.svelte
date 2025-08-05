<script>
    let { name = $bindable() } = $props()
</script>

<label for="componentName">
    Component Name <input type="text" bind:value={name}>
</label>