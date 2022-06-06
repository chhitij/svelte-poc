<script lang="ts">
	export const prerender = true;
	import {pokemon} from "../stores/unlock-rules"; 
	// import PokemanCard from '../components/pokemanCard.svelte';
	import { JSONEditor } from 'svelte-jsoneditor'
	let serachTerm = ""
	let filteredPokemon = [];

	$: {
		// console.log(serachTerm)
		if(serachTerm) {
			// serach Pokemon
			filteredPokemon = $pokemon.filter(pokeman=> pokeman.name.toLowerCase().includes(serachTerm))
		} else {
			filteredPokemon = [...$pokemon];
		}
	}

	 let content = {
    text: undefined, // used when in code mode
    json: {
      array: [1, 2, 3],
      boolean: true,
      color: '#82b92c',
      null: null,
      number: 123,
      object: { a: 'b', c: 'd' },
      string: 'Hello World'
    }
  }
</script>


<svelte:head>
	<title>Unlock Rules</title>
	<meta name="description" content="Unlock Rules App" />
</svelte:head>

<section>
	<h1 class="text-2xl text-center my-8 uppercase">
		<div class="welcome">
           Please Paste JSON data in editior
		</div>
		
	</h1>
	<input class="w-full rounded-md text-lg p-4 border-2 border-gray-200" type="text" placeholder="Search Pkemon"
	bind:value={serachTerm}>
	<!-- <div class="py-4 grid gap-4 md:grid-cols-2 grid-cols-1">
	{#each filteredPokemon as pokeman}
	 <PokemanCard pokeman ={pokeman}></PokemanCard>
	{/each}
	<JSONEditor bind:content/>
	</div> -->
	<div class="py-4 grid gap-4 md:grid-cols-1 grid-cols-1">
		<JSONEditor bind:content/>
	</div>
</section>