<template>
<div class="pokemodal" v-if="showModal">

<!-- Card itself -->
<div class="pokemodal-body">

<!-- Pokemon Image -->
<div class="img-wrapper">
<img src="https://pokeres.bastionbot.org/images/pokemon/5.png" alt="" width="65" height="65">
</div>

<!-- Pokemon's Name -->
<h2 class="name">Bulbasaur</h2>

<!-- Stats -->
<div class="stats">

<!-- Experience -->
<div class="exp">      
<p>Base Experience</p>  
<p>64xp</p>
</div>  

<!-- Height -->
<div class="height">      
<p>Height</p>  
<p>0.7m</p>
</div> 

<!-- Weight -->
<div class="weight">      
<p>Weight</p>  
<p>6.9kg</p>
</div> 

</div>

<!-- Pokemon Types -->
<div class="types-title">
<p>Pokemon Types</p>
</div>

<!-- Buttons for Types -->
<div class="types-buttons">
<button class="type-btn">Grass</button>
<button class="type-btn">Poison</button>
</div>

<!-- Pokemon Abilities -->
<div class="abilities-title">
<p>Abilities</p>
</div>

<!-- Buttons for Abilities -->
<div class="abilities-buttons">
<button class="ability-btn">Overgrow</button>
<button class="ability-btn">Chlorophyll</button>
</div>

<!-- Close Modal -->
<button class="modal-close" @click="modalClose">Close</button>


</div>

</div>
</template>


<script>
export default {
name: 'Pokemodal',

props: [
 "showModal",
 "imageUrl"
],

data() {
return {
pokemon: {} //Individual Pokemon
}
},

methods: {
// Getting Pokemons from API    
fetchData() {

},

modalClose() {
this.$emit('removeModal', 'showModal'); 
}

},

// Run Fetch request as soon as the element is created
created() {
this.fetchData();    
}

}
</script>


<style scoped>

.pokemodal{
background: rgba(0, 0, 0, 0.7);
position: fixed;
width: 100%;
height: 100vh;
color: #fff;
text-align: center;
}

.pokemodal .pokemodal-body{
background: #fff;
color: black;
width: 40vw;
margin: 100px auto;
padding-bottom: 7vh;
border-radius: 5px;
}

.pokemodal-body .img-wrapper{
background: rgb(44, 43, 43);
display: inline-block;
align-items: center;
justify-content: center;
border-radius: 50%;
width: 120px;
height: 120px;
margin-top: -70px;
}

.pokemodal-body .img-wrapper img{
position: relative;    
top: 20px;
}

.pokemodal-body .name{
font-weight: 900;
font-size: 1.5rem; 
margin-top: -1px; 
padding-top: 10px;
}

.pokemodal .pokemodal-body .stats .exp, .height, .weight{  
width: 35vw; 
margin: auto;
display: flex;
justify-content: space-between;
font-weight: bold;
border-bottom: 1px solid rgb(90, 90, 90); 
}

.pokemodal .pokemodal-body .types-title, .abilities-title{ 
width: 35vw; 
margin: auto;
display: flex;
justify-content: start;
border-bottom: 1px solid rgb(170, 169, 169); 
height: 6.5vh;
font-weight: 900;    
font-size: 1.2rem;
}

.types-buttons, .abilities-buttons{
width: 35vw; 
margin: auto;
display: flex;
}

.types-buttons .type-btn{
margin-top: 15px; 
border-radius: 50px;   
background-color: rgb(22, 22, 82);
color: #fff;
border:none;
outline: none;
padding:7px 10px;
font-size: 16px;
font-weight: bold;
margin:10px 5px;
}

.abilities-buttons .ability-btn{
margin-top: 15px; 
border-radius: 50px;   
background-color: rgb(206, 10, 20);
color: #fff;
border:none;
outline: none;
padding:7px 10px;
font-size: 16px;
font-weight: bold;
margin:10px 5px;
}

.modal-close{
background: rgb(53, 53, 53); 
color: #fff;   
border: none;
outline: none;
padding:10px 15px;
font-size: 16px;
border-radius: 5px;
cursor: pointer;
margin-top: 30px;
}

</style>
