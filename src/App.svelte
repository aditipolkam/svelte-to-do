<script>
	let todos = [
		{done:false, text:'Make a todo app.'}
	];
	function add(){
		todos = todos.concat({done:false, text:''});
	}
	function clear(){
		todos = todos.filter(t=>!t.done);
	}
	$: remaining = todos.filter(t=>!t.done).length;
</script>

<main>
	<h1>Todos</h1>
	{#each todos as todo}
		<div class:done = {todo.done}>
			<input type=checkbox bind:checked={todo.done}>
			<input placeholder="Enter task..." value={todo.text}>
		</div>
	{/each}
	<p>{remaining} remaining.</p>
	<button on:click={add}>Add new item</button>
	<button on:click={clear}>Clear completed</button>
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}
	.done{
		opacity:0.4;
	}
</style>