<script lang="ts">
	let num = $state(1);

	// Simple work of $state

	let plus = () => {
		num += 1;
	};

	let minus = () => {
		num -= 1;
	};

	// Extended

	let todos = $state([
		{
			done: false,
			title: 'Some todo'
		}
	]);

	let newTodo = (title) => {
		todos.push({
			done: false,
			title: title
		});
	}; 

	class Todo {
		clicks = $state(0); 
		done = $state(false);
		hidden = $state(false);

		constructor(title) {
			this.text = $state(title);
            this.log("Todo is created: "+$state.snapshot(this))
		}

		click() {
			this.clicks += 1;
            this.log("Todo is clicked: "+$state.snapshot(this.clicks))
		}

        changeStatus() {
            if (this.done) {
                this.incomplete()
            } else {
                this.complete()
            }
        }

        complete() {
            this.done = true
            this.log("Todo is completed: "+$state.snapshot(this.done))
        }

        incomplete() {
            this.done = false
            this.log("Todo is incompleted: "+$state.snapshot(this.done))
        }

		hide() {
			this.hidden = true;
            this.log("Todo is hidden: "+$state.snapshot(this.hidden))
		}

        log(message) {
            console.log(message);
        }
	}

	let todoList = $state([]);

	let newTodoClass = (text) => {
		const todo = new Todo(text);
		todoList.push(todo);
	};
</script>

<button onclick={minus}>-</button>
{num}
<button onclick={plus}>+</button>

<hr />

<h3>Created on simple methods</h3>

<ul>
	{#each todos as todo}
		<li>
			<label for="todo" class={{ completed_todo: todo.done }}>
				<input type="checkbox" bind:checked={todo.done} />
				<span>{todo.title}</span>
			</label>
		</li>
	{/each}
</ul>

<button onclick={() => newTodo('New todo')}>Add</button>

<hr />

<h3>Created on Classes</h3>

<ul>
	{#each todoList as todo}
		{#if todo.hidden == false}
			<li onclick={() => todo.click()}>
				<label for="todo" class={{ completed_todo: todo.done }}>
					<input type="checkbox" bind:checked={todo.done} onclick={() => todo.changeStatus()} />
					<span>{todo.text} ({todo.clicks})</span>
					<button onclick={() => todo.hide()}>hide</button>
				</label>
			</li>
		{/if}
	{/each}
</ul>

<button onclick={() => newTodoClass('New todo')}>Add</button>

<style>
	.completed_todo {
		text-decoration: line-through;
		color: #ccc;
	}

	.completed_todo:hover {
		color: #777;
		cursor: pointer;
	}
</style>
