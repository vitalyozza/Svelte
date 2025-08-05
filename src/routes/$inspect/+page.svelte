<script>
    let name = $state("Vitaly")

    // $inspect(name)

    $inspect(name).with((type, name) => {
        console.log(type, name, `(${name.length})`)
    })
</script>

<label for="name">
    Name: <input type="text" id="name" bind:value={name}>
</label>