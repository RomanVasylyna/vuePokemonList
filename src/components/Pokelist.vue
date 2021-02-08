<template>

<div class="pokewrapper">

    <div class="pokelist"

    v-for="(pokemon, index) in pokemons"

    :key="pokemon + index"

    @click="openModal(pokemon.name, index)">

    <img

    :src="imageUrl + pokemon.id + '.png'"

    width="100" height="100"
    >

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

toUpperCase(str) {
return str.charAt(0).toUpperCase() + str.slice(1);    
},      

// Get data from API
fetchData() {

fetch(this.apiUrl)
.then(data => data.json())

.then(dataJson => {
this.pokemons = dataJson.results;
this.pokemons.forEach(elem => {
let str = elem.url.split('/');
elem.id = str[6];
})
console.log(this.pokemons);
})

.catch(err => console.log(err))

},

addId() {
this.pokemons.forEach(elem => {
return elem;
})
},

// Toggle Boolean from Parent element
openModal(index) {
this.$emit('toggleModal', index);
}


},

// Assigning api values to array
mounted() {     
this.fetchData();
this.addId();   
}



}
</script>


<style scoped>

/* All Screen Sizes */
.pokewrapper{
color: black;
border-radius: 5px;
margin: 20px auto;
display: flex;
flex-wrap: wrap;
width: 36vw;
text-align: center;
}

/* .pokewrapper{
color: black;
border-radius: 5px;
margin: 20px auto;
display: flex;
flex-wrap: wrap;
width: 39vw;
text-align: center;
} */

.pokewrapper .pokelist{
text-align: center;
width: 10vw;
background: #fff;
padding: 5px 10px;
margin: 5px;
border-radius: 5px;
cursor: pointer;
}

.pokewrapper .pokelist:hover{
background: red;
color: #fff;
}


/* Phones */
@media (max-width: 690px) {
.pokewrapper{
color: black;
border-radius: 5px;
margin: 20px auto;
display: flex;
flex-wrap: wrap;
width: 75vw;
text-align: center;
}

.pokewrapper .pokelist{
text-align: center;
width: 40vw;
background: #fff;
padding: 5px 60px;
margin: 5px;
border-radius: 5px;
cursor: pointer;
}
}

/* Ipad and other tablets*/
@media only screen and (max-width: 800px) and (min-width: 700px) {
.pokewrapper{
color: black;
border-radius: 5px;
margin: 20px auto;
display: flex;
flex-wrap: wrap;
width: 60vw;
text-align: center;
}

.pokewrapper .pokelist{
text-align: center;
width: 25vw;
background: #fff;
padding: 10px;
margin: 5px;
border-radius: 5px;
cursor: pointer;
}
}

/* Ipad Pro */
@media only screen and (max-width: 1100px) and (min-width: 1000px) {
.pokewrapper{
color: black;
border-radius: 5px;
margin: 20px auto;
display: flex;
flex-wrap: wrap;
width: 63vw;
text-align: center;
}

.pokewrapper .pokelist{
text-align: center;
width: 18vw;
background: #fff;
padding: 10px;
margin: 5px;
border-radius: 5px;
cursor: pointer;
}
}




</style>
