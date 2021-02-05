<template>
<div class="container">

<h1>Pokemons</h1>

<!-- Searchbar -->
<Pokesearch
:apiUrl="apiUrl"
@setPokemon="getPokemon"
/>

<!-- List of all pokemons -->
<!-- <Pokelist
:showModal="showModal" 
:apiUrl="apiUrl"
:imageUrl="imageUrl"
@toggleModal="openModal()"
/> -->

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
// import Pokelist from './Pokelist.vue'
import Pokemodal from './Pokemodal.vue'

export default {
name: 'Pokemon',

components: {
Pokesearch,
// Pokelist,
Pokemodal,
},

data(){
return {
apiUrl: 'https://pokeapi.co/api/v2/pokemon/',
showModal: false, //Toggle Modal 
pokemonUrl: '',
pokemon: {},
}
},

methods: {

fetchData() {
fetch(this.pokemonUrl)
.then(res => res.json())

.then(data => {
if(Object.keys(data).length !== 0) {
this.pokemon = data;
this.showModal = true; //Open Modal
console.log(typeof data);   
} else {
alert('Error occured');  
}  
})

.catch(err => console.log(err))
},

openModal() {
this.showModal = true;
},

closeModal() {
this.showModal = false;    
},

getPokemon(url) { // url = apiUrl + searchVal
this.pokemonUrl = url; //Mutating pokemonUrl variable for all elements
this.fetchData();
console.log(url);
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
