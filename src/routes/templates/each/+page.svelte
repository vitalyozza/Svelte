<script lang="ts">
    let numbers = [
        1,2,3,4,5,6,7
    ]

    let words = [
        "first","second","third","fourth","fiveth","sixth", "seventh"
    ]

    let users = [
        {id: 2, name: "Alex", words: words},
        {id: 1, name: "Be", words: words},
        {id: 3, name: "Le", words: words},
    ]

</script>

<h3>Example with simple list</h3>
<ul>
    {#each numbers as number}
        <li>{number}</li>
    {:else}
	    <p>No data!</p>
    {/each}
</ul>

<h3>Example with list and indexes</h3>
<ul> 
    {#each words as word, index}
        <li>{index}: {word}</li>
    {:else}
	    <p>No data!</p>
    {/each}
</ul>

<h3>Example with keys</h3>

<ul>
    {#each users as user (user.id)}
        <li>
            <b>{user.name}</b>
            <ul>
            {#each user.words as word}
                <li>{word}</li>
            {/each}
            </ul>
        </li>
    {/each}
</ul>

<h3>Each blocks without an item</h3>

<ul>
    {#each { length: 3 }, userNum }
        {#if userNum > 0}
            <li>
                <b>{userNum}</b>
                <ul>
                {#each { length: 3 }, detailNum}
                    <li>{detailNum}</li>
                {/each}
                </ul>
            </li>
        {/if}
    {/each}
</ul>