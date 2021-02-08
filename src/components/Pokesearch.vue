<template>
  <div class="searchbar">
    <form @submit.prevent="findPokemon">
      <input type="text" class="poke-search" placeholder="Search Pokemon" v-model="searchVal">
    </form>
    <i class="fas fa-search"></i>
  </div>
</template>


<script>
export default {
name: 'Pokesearch',

props: ["apiUrl"],

data() {
return {
searchVal: '',  
}  
},

methods: {
  
// Transferring the search value to Parent Elem  
findPokemon() {
if(this.searchVal !== '') { //Making sure string is not empty
this.$emit('setPokemon', this.apiUrl + this.searchVal.toLowerCase()); 
this.searchVal = '';
} else {
alert('Value cannot be empty');  
} 
}

},

}
</script>


<style scoped>

/* All Screen Sizes */
.searchbar .poke-search{
position: relative;
width: 35vw;
padding: 10px 4px;
font-size: 16px;
border-radius: 5px;
border: 0;
outline: none;
}

.searchbar .fa-search{
position: absolute;
top: 90px;
right: 500px;
color: black;
cursor: pointer;
}

/* Phones */
@media (max-width: 690px) {

.searchbar .poke-search{
position: relative;
width: 70vw;
padding: 10px 5px;
font-size: 16px;
border-radius: 5px;
border: 0;
outline: none;
}

.searchbar .fa-search{
position: absolute;
top: 90px;
right: 65px;
color: black;
}

}

/* Ipad and other tablets*/
@media only screen and (max-width: 800px) and (min-width: 700px) {
.searchbar .poke-search{
position: relative;
width: 70vw;
padding: 12px 5px;
font-size: 16px;
border-radius: 5px;
border: 0;
outline: none;
}

.searchbar .fa-search{
position: absolute;
top: 90px;
right: 126px;
color: black;
}
}

/* Ipad Pro */
@media only screen and (max-width: 1100px) and (min-width: 1000px) {

.searchbar .poke-search{
position: relative;
width: 61.5vw;
padding: 13px 5px;
font-size: 16px;
border-radius: 5px;
border: 0;
outline: none;
}

.searchbar .fa-search{
position: absolute;
top: 92px;
right: 210px;
color: black;
}

}



</style>
