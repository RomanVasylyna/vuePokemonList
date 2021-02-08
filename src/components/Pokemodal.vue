<template>

<div class="pokemodal" v-if="showModal">

<!-- Card itself -->
<div class="pokemodal-body">

<!-- Pokemon Image -->
<div class="img-wrapper">
<img :src="this.pokemon.sprites.front_default" alt="" width="100" height="100">
</div>

<!-- Pokemon's Name -->
<h2 class="name">{{ toUpperCase(pokemon.name) }}</h2>

<!-- Stats -->
<div class="stats">

<!-- Experience -->
<div class="exp">      
<p>Base Experience</p>  
<p>{{ pokemon.base_experience }}xp</p>
</div>  

<!-- Height -->
<div class="height">      
<p>Height</p>  
<p>{{ pokemon.height / 10 }}m</p>
</div> 

<!-- Weight -->
<div class="weight">      
<p>Weight</p>  
<p>{{ pokemon.weight / 10 }}kg</p>
</div> 

</div>

<!-- Pokemon Types -->
<div class="types-title">
<p>Pokemon Types</p>
</div>

<!-- Buttons for Types -->
<div class="types-buttons">
<button class="type-btn" 
v-for="(type, index) in pokemon.types" 
:key="type+index">
{{ toUpperCase(pokemon.types[index].type.name)}}
</button>
</div>

<!-- Pokemon Abilities -->
<div class="abilities-title">
<p>Abilities</p>
</div>

<!-- Buttons for Abilities -->
<div class="abilities-buttons">
<button class="ability-btn" 
v-for="(ability, index) in pokemon.abilities" 
:key="ability+index">
{{ toUpperCase(pokemon.abilities[index].ability.name)}}
</button>
</div>  


<!-- Close Modal -->
<button class="modal-close" @click="modalClose">Close</button>


</div>

</div>


<!-- Error Modal -->
<!-- <div class="error-modal" v-else>
<div class="error-body">  
<h1>Test</h1>
<button class="modal-close" @click="modalClose">Close</button>
</div>
</div> -->





    





</template>




<script>
export default {
name: 'Pokemodal',

props: [
 "showModal",
 "imageUrl",
 "pokemonUrl",
 "pokemon"
],

data() {
return {
image: '',
name: '',
}
},
// this.pokemonUrl
methods: {

// Make first letter uppercase
toUpperCase(str) {
return str.charAt(0).toUpperCase() + str.slice(1);
},

// Emitting an event to parent element
modalClose() {
this.$emit('removeModal'); 
},


},

}
</script>


<style scoped>

/* All Screen Sizes */
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
width: 36vw;
margin: 100px auto;
padding-bottom: 6vh;
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
top: 7px;
}

.pokemodal-body .name{
font-weight: 900;
font-size: 1.5rem; 
margin-top: -1px; 
padding-top: 10px;
}

.pokemodal .pokemodal-body .stats .exp, .height, .weight{  
width: 30vw; 
margin: auto;
display: flex;
justify-content: space-between;
font-weight: bold;
border-bottom: 1px solid rgb(90, 90, 90); 
}

.pokemodal .pokemodal-body .types-title, .abilities-title{ 
width: 30vw; 
margin: auto;
display: flex;
justify-content: start;
border-bottom: 1px solid rgb(170, 169, 169); 
height: 6.5vh;
font-weight: 900;    
font-size: 1.2rem;
}

.types-buttons, .abilities-buttons{
width: 30vw; 
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


/* Phones */
@media (max-width: 690px) {

.pokemodal .pokemodal-body{
background: #fff;
color: black;
width: 80vw;
margin: 100px auto;
padding-bottom: 1vh;
border-radius: 5px;
}   

.pokemodal .pokemodal-body .stats .exp, .height, .weight{  
width: 55vw; 
margin: auto;
display: flex;
justify-content: space-between;
font-weight: bold;
border-bottom: 1px solid rgb(90, 90, 90); 
}

.pokemodal .pokemodal-body .types-title, .abilities-title{ 
width: 55vw; 
margin: auto;
display: flex;
justify-content: start;
border-bottom: 1px solid rgb(170, 169, 169); 
height: 6.5vh;
font-weight: 900;    
font-size: 1.2rem;
}

.types-buttons, .abilities-buttons{
width: 60vw; 
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
padding:7px 15px;
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
margin-top: 10px;
}

}    

/* Ipad and other tablets*/
@media only screen and (max-width: 800px) and (min-width: 700px) {

.pokemodal .pokemodal-body{
background: #fff;
color: black;
width:70vw;
margin: 100px auto;
padding-bottom: 1vh;
border-radius: 5px;
}   

.pokemodal .pokemodal-body .stats .exp, .height, .weight{  
width: 55vw; 
margin: auto;
display: flex;
justify-content: space-between;
font-weight: bold;
border-bottom: 1px solid rgb(90, 90, 90); 
}

.pokemodal .pokemodal-body .types-title, .abilities-title{ 
width: 55vw; 
margin: auto;
display: flex;
justify-content: start;
border-bottom: 1px solid rgb(170, 169, 169); 
height: 6.5vh;
font-weight: 900;    
font-size: 1.2rem;
}

.types-buttons, .abilities-buttons{
width: 55vw; 
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
padding:7px 15px;
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
margin-top: 10px;
}    
}    


/* Ipad Pro */
@media only screen and (max-width: 1100px) and (min-width: 1000px) {

.pokemodal .pokemodal-body{
background: #fff;
color: black;
width:60vw;
margin: 100px auto;
padding-bottom: 1vh;
border-radius: 5px;
}   

.pokemodal .pokemodal-body .stats .exp, .height, .weight{  
width: 50vw; 
margin: auto;
display: flex;
justify-content: space-between;
font-weight: bold;
border-bottom: 1px solid rgb(90, 90, 90); 
}

.pokemodal .pokemodal-body .types-title, .abilities-title{ 
width: 50vw; 
margin: auto;
display: flex;
justify-content: start;
border-bottom: 1px solid rgb(170, 169, 169); 
height: 4vh;
font-weight: 900;    
font-size: 1.2rem;
}

.types-buttons, .abilities-buttons{
width: 50vw; 
margin: auto;
display: flex;
}

.types-buttons .type-btn{
border-radius: 50px;   
background-color: rgb(22, 22, 82);
color: #fff;
border:none;
outline: none;
padding:7px 15px;
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
margin-top: 10px;
}        
}    

</style>
