<template>
<div class="pokewrapper">

<div class="pokelist" v-for="pokemon in pokemons" :key="pokemon.name">
    <img src="https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/10001.png" width="50" height="50">
    <h3>
    {{ toUpperCase(pokemon.name) }}
    </h3>

</div>

</div>
</template>


<script>
export default {

name: 'Pokelist',

props: [
 "apiUrl",
 "imageUrl"
],

data() {
return {
pokemons: [],
}
},

methods: {

// Get data from API
fetchData() {

fetch(this.apiUrl)
.then(data => data.json())

.then(dataJson => {
this.pokemons = dataJson.results;
})

.catch(err => console.log(err))

},

// Make first letter uppercase
toUpperCase(str) {
return str.charAt(0).toUpperCase() + str.slice(1);
}

},

// Assigning api values to array
mounted() {
this.fetchData();
}



}
</script>


<style scoped>

.pokewrapper{
color: black;
border-radius: 5px;
margin: 20px auto;
display: flex;
flex-wrap: wrap;
width: 40vw;
background: green;
text-align: center;
}

.pokewrapper .pokelist{
text-align: center;
width: 10vw;
background: #fff;
padding: 10px;
margin: 5px;
border-radius: 5px;
cursor: pointer;
}

.pokewrapper .pokelist:hover{
background: red;
color: #fff;
}



</style>