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

<div class = "flex_X">


</div>

<div class="flex1">
	<div class="todo">
		
		<h1>Список дел</h1>
		<input bind:value={newItem} type="text" placeholder="new todo item.." />

		<button on:click={addToList}> Add </button>
		
		
		
		{#each todoList as item, index}
		<div class = "todos">
			<div class= "item">

			<input bind:checked={item.status} type="checkbox" />

			<div class:checked={item.status}>
				{item.text}
			</div>
			<!-- svelte-ignore a11y-click-events-have-key-events -->
			<div class ="del" on:click={() => removeFromList(index)}>&times;</div>
		</div>
	</div>				
		{/each}
	</div>
</div>

<style>
	.item div:nth-child(2){
width: 10em ;
display: flex;
flex-direction: row;
align-items: center;
	}
	.item {
		display: flex;
		flex-direction: row;
		justify-content: space-between;
		
	}
	.checked {
		text-decoration: line-through;
	}
	.flex1 {
		display: flex;
		height: 100vh;
		justify-content: center;
		align-items: center;
		background: #183544;
		padding: 4em ;
		margin: 4em;
	}
	.todo {
		display: flex;
		flex-direction: column;
		background: #49778f;
		color: whitesmoke;
		padding: 2em ;
	}
	.todos {
		display: flex;
		flex-direction: column;

	}
	.del {
		font-size: 1.7em;
		color: lawngreen;
	}
</style>
