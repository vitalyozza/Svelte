<script lang="ts">
    import InfoBlock from "$lib/components/InfoBlock.svelte"
    import Clicker from "$lib/components/Clicker.svelte"
    import ComID from "$lib/components/ComID.svelte"

    let clicks = $state(0)
</script>

<h3>Example with sections</h3>

<InfoBlock title="Title A" description="Some text will be here"></InfoBlock>
<InfoBlock title="Title B"></InfoBlock>
<InfoBlock title="Title C" description="Some text will be here"></InfoBlock>

<hr>

<h3>Example with clicker</h3>

<Clicker {clicks} ></Clicker>

<hr>

<h3>Example with uids</h3>

<ComID></ComID>
<ComID></ComID>