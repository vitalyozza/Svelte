<script lang="ts">
    let size = $state(50);
	let color = $state('#ff3e00');

	let canvas;

    let increase = () => {
        size+=10;
    }

    let decrease = () => {
        size-=10;
    }

    let reset = () => {
        size=0
    }

	$effect(() => {
		const context = canvas.getContext('2d');
		context.clearRect(0, 0, canvas.width, canvas.height);

		// this will re-run whenever `color` or `size` change
		context.fillStyle = color;
		context.fillRect(0, 0, size, size);
	});

    let count = $state(0)
    let miliseconds = $state(1000)

    $effect(() => {

        const interval = setInterval(() => {
            count += 1
        }, miliseconds)

        return () => {
            clearInterval(interval)
        }

    })

</script>

<h3>Example with canvas</h3>

<canvas bind:this={canvas}></canvas>

<button onclick={() => decrease()}>
-
</button>

<button onclick={() => increase()}>
+
</button>

<button onclick={() => reset()}>
reset
</button>

<hr>

<h3>Example with timer</h3>

{count} (pase: {miliseconds})

<button onclick={miliseconds-=100}>faster</button>
<button onclick={miliseconds+=100}>slower</button>