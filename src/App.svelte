<!-- Sepreration of concerns now not so serpate! -->
<!-- Top level component direct injected into the DOM -->

<!-- Component Logic -->
<!-- Loops with id (needed for looping in Svelte) -->
<script>
	let people = [
		{ name: 'steve', colorEl: 'yellow', age: 30, id: 1 },
		{ name: 'philip', colorEl: 'orange', age: 45, id: 2 },
		{ name: 'harry', colorEl: 'green', age: 20, id: 3 },
	];

	const handleClick = (id) => {
		// Delete the person from people (arrow function)
		people = people.filter((person) => person.id != id)
	}
</script>


<!-- HTML template inserted into the dom -->
<!-- Svelte Syntax similar to blade, jinja etc templating syntax -->
<!-- For looping with svelte and template syntax -->
<main>
	{#each people as person (person.id)}
		<div>
			<h6>{person.name}</h6>
			<p>{person.age} years old, {person.colorEl} color.</p>
			<button on:click={() => {handleClick(person.id)}}>Delete</button>
		</div>
		{:else}
			<p>There are no people to show!</p>
	{/each}
</main>


<!-- Styling -->
<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h6 {
		color: #ff3e00;
		text-transform: lowercase;
		font-size: 1em;
		font-weight: 100;
	}

	p {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>