<script lang="ts">
class Unit {
    value = $state(0)

    constructor(name) {
        this.name = $state(name)
    }

    increase() {
        this.value += 1
    }

    decrease() {
        this.value -= 1
    }
}

let a = new Unit("a")
let b = new Unit("b")

let sum = $derived(a.value + b.value)
let complexSum = $derived.by(() => {
    return sum * sum
})
</script>

<button onclick="{() => a.decrease()}">-</button>
<span>a: {a.value}</span>
<button onclick="{() => a.increase()}">+</button>

<button onclick="{() => b.decrease()}">-</button>
<span>a: {b.value}</span>
<button onclick="{() => b.increase()}">+</button>

<br>

<span>Sum: {sum}</span>
<span>complexSum: {complexSum}</span>