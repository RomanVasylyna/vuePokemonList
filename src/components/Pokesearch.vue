<template>
<div>
<input type="text" placeholder="Type Pokemon's name" class="pokemon-search">
</div>
</template>


<script>
export default {
name: 'Pokesearch',

props: ["apiUrl"],

}
</script>


<style scoped>

.pokemon-search{
width: 30vw;
padding: 10px 5px;
font-size: 16px;
border-radius: 5px;
border: 0;
outline: none;
}

</style>