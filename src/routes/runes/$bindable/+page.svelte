<script>
    import BindableComponent from "$lib/components/BindableComponent.svelte";

    let name = $state("Vitaly")
</script>

<h3>Example with reactive inputs</h3>

<label for="name">
    Name
    <input type="text" id="name" bind:value={name}>
</label>
<br>
<BindableComponent bind:name={name}/>