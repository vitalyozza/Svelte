<script lang="ts">
    let showData = $state(true)
    let num = $state(0)

    let increase = () => {
        num += 1
    }

    let decrease = () => {
        num -= 1
    }

    console.log($inspect(showData))
</script>
<h3>Example with if/else</h3>
<p>
    <span>showData is <b>{showData}</b></span>
    {#if showData == true}
        <span>(is here)</span>
    {:else}
        <span>(is not here)</span>
    {/if}
</p>
<p>
    <label for="showData">
        <input type="checkbox" id="showData" bind:checked={showData}> Showdata
    </label>
</p>

<h3>Example with if/elseif</h3>
<button onclick={decrease}>-</button>
{num}
<button onclick={increase}>+</button>
<p>
    {#if num < 0}
    It's less than zero
    {:else if num == 0}
    It's zero
    {:else if num > 0 && num < 10}
    It's more than zero
    {:else}
    It's too much
    {/if}
</p>