<template>
<div class="container">

<h1>Pokemons</h1>

<!-- Searchbar -->
<Pokesearch
:apiUrl="apiUrl"
@setPokemon="getPokemon"
/>

<!-- List of all pokemons -->
<Pokelist
:apiUrl="apiUrl"
:imageUrl="imageUrl"
:list="list"
@toggleModal="openModal"
@appendPokemon="addPokemon"
/>

<!-- Pokemon Modal -->
<Pokemodal
:showModal="showModal"
:pokemonUrl="pokemonUrl"
:pokemon="pokemon"
@removeModal="closeModal"
@setPokemon="getPokemon"
/>

</div>
</template>


<script>
// Importing Components
import Pokesearch from './Pokesearch.vue'
import Pokelist from './Pokelist.vue'
import Pokemodal from './Pokemodal.vue'

export default {
name: 'Pokemon',

components: {
Pokesearch,
Pokelist,
Pokemodal,
},

data(){
return {
apiUrl: 'https://pokeapi.co/api/v2/pokemon/',
imageUrl:'https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/',
showModal: false, //Toggle Modal
pokemonUrl: '',
pokemon: {},
list: [],
}
},

methods: {

addPokemon(arr) {
this.list = arr;
},

hasDuplicates(arr, obj) {
return (arr.filter(e => e.name === obj.name).length) ? true : false;
},

fetchData(url) {
fetch(url)
.then(res => {
if(res.status === 200) {
this.showModal = true;
return res.json();
}
})

.then(data => {
this.pokemon = data;

// Check if array has duplicates
if(!this.hasDuplicates(this.list, this.pokemon)) {
this.list.push(this.pokemon);
}
// console.log(this.pokemon);
// console.log(this.list);
})

.catch(err => console.log(err))
},

openModal(result) {
this.pokemonUrl = this.apiUrl + result;
this.fetchData(this.pokemonUrl);
this.showModal = true;
},

closeModal() {
this.showModal = false;
},

getPokemon(url) { // url = apiUrl + searchVal
this.pokemonUrl = url; //Mutating pokemonUrl variable for all elements
this.fetchData(this.pokemonUrl);
console.log(this.pokemonUrl);
}
},




}
</script>


<style scoped>

.container{
display: flex;
flex-direction: column;
align-items: center;

color: #fff;
background: radial-gradient(#156F99, #0A2E50);

font-family: 'Acme', arial;
font-size: 1rem;
font-weight: normal;

min-height: 100vh;
}

.pokemon-search{
width: 30vw;
padding: 10px 5px;
font-size: 16px;
border-radius: 5px;
border: 0;
outline: none;
}

</style>
