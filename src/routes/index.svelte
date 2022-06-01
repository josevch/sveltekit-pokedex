<script>
	import { pokemon } from '../stores/pokestore';
	import PokemanCard from '../components/pokemanCard.svelte';
</script>

<svelte:head>
	<title>Pokedex</title>
</svelte:head>

<h1 class="text-4xl text-center my-8 uppercase">Sveltekit Pokedex</h1>

{#each $pokemon as pokeman}
	<PokemanCard {pokeman} />
{/each}
