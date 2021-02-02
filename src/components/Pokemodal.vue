<template>
<div class="pokemodal" v-if="showModal">

<div class="pokemodal-body">
<h1>fsfdfdsf</h1>
</div>

<h1>Pokemodal</h1>
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
show: false,
}
},

methods: {

},

}
</script>


<style scoped>

.pokemodal{
background: rgba(0, 0, 0, 0.7);
position: absolute;
width: 100%;
height: 190vh;
color: #fff;
text-align: center;
}

.pokemodal .pokemodal-body{
background: red;
}

</style>