<script>
	import { pokemon } from '../stores/pokestore';
	import PokemanCard from '../components/pokemanCard.svelte';

	let searchTerm = '';
	let filteredPokemon = [];

	$: {
		console.log(searchTerm);
		if (searchTerm) {
			//search logic reactivity
			filteredPokemon = $pokemon.filter((pokeman) =>
				pokeman.name.toLowerCase().includes(searchTerm.toLocaleLowerCase())
			);
		} else {
			filteredPokemon = [...$pokemon];
		}
	}
</script>

<svelte:head>
	<title>Pokedex</title>
</svelte:head>

<h1 class="text-4xl text-center my-8 uppercase">Sveltekit Pokedex</h1>

<div class="px-4 ">
	<input
		class="flex mx-auto my-0 px-8 w-full rounded-md text-lg p-4 border-2 border-gray-200"
		type="text"
		bind:value={searchTerm}
		placeholder="Search Pokemon"
	/>
</div>

<div class=" py-4 px-4 grid gap-4 md:grid-cols-3 grid-cols-1">
	{#each filteredPokemon as pokeman}
		<PokemanCard {pokeman} />
	{/each}
</div>
