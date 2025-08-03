<script lang="ts">
/** @type {{ clicks: number }} */
let { clicks } = $props()

</script>

<button onclick={clicks+=1}>
    +
</button>

<span><b>{clicks}</b></span>

<button onclick={clicks-=1}>
    -
</button>