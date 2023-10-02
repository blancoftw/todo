<script>
	let newItem = "";

	let todoList = [
		{ text: "Write my first post", status: true },
		{ text: "Upload the post to the blog", status: false },
		{ text: "Publish the post at Facebook", status: false },
	];

	function addToList() {
		todoList = [...todoList, { text: newItem, status: false }];
		newItem = "";
	}

	function removeFromList(index) {
		todoList.splice(index, 1);
		todoList = todoList;
	}
</script>

<div class="flex1">
	<div class="todo">
		<h1>Список дел</h1>
		<input bind:value={newItem} type="text" placeholder="new todo item.." />

		<button on:click={addToList}> Add </button>

		<br />
		{#each todoList as item, index}
			<!-- svelte-ignore a11y-click-events-have-key-events -->
			<span on:click={() => removeFromList(index)}>❌</span>
			<input bind:checked={item.status} type="checkbox" />

			<span class:checked={item.status}>
				{item.text}
			</span>
			<br />
		{/each}
	</div>
</div>

<style>
	.checked {
		text-decoration: line-through;
	}
	.flex1 {
		display: flex;
		height: 100vh;
		justify-content: center;
		align-items: center;
		background: #939358;
	}
	.todo {
		background: #1a3949;
		color: whitesmoke;
	}
</style>
