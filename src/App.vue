<template>
<div v-if="myshows">
  <ul>
    <li v-for="name in filteredName" :key="name" :class="{fav:name.isFav}" @click="favToggle(name)">
      <h1>{{name.book}}</h1>
      <!-- <img v-bind:src="name.imgs" :alt="alt"> -->
      <p>{{name.title}}</p>
      <p>{{name.alt}}</p>
    </li>
  </ul>
</div>
  <button @click="changeit" class="btn">
    <span v-if="myshows">Hide it</span>
    <span v-else>Open it</span>
  </button>
</template>

<script>
export default {
data() {
  return {
    myshows: true,
    names: [
      {book:'the anatomy',title:'the history of anatomy',alt:'this is anatomy',isFav: true},
      {book:'the biology',title:'the biological demand',alt:'this is biology',isFav: false},
      {book:'the physics',title:'the physics story',alt:'thsi is physics',isFav: true}
    ],
  }
},
methods: {
  changeit(){
    this.myshows = !this.myshows;
  },
  favToggle(name){
    name.isFav = !name.isFav;
  }
},
computed: {
  filteredName() {
    return this.names.filter((name)=>name.isFav);
  }
}
}
</script>

<style>
ul li{
  list-style-type: none;
  margin: 10px;
  padding: 20px;
  border: 1px solid black;
  border-radius: 10px;
  display: flex;
  justify-content: space-around;
  align-items: center;
}
.fav{
  background: orangered;
  color: white;
}
.btn{
  border: none;
  padding: 20px;
  background: orangered;
  color: white;
  width: 100%;
}
</style>