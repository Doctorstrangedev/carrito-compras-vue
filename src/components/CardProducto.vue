<template>
  <div class="card mt-2" style="width: 18rem;">
  <img :src="productoCard.image" class="card-img-top mt-2" :alt="`image ${productoCard.title}`">
  <div class="card-body">
    <h5 class="card-title">{{productoCard.title}}</h5>
    <span class="text-center font-weight-bold">${{Intl.NumberFormat().format(productoCard.precio)}}</span>
    
  </div>
  <button class="btn btn-success mb-2" @click="agregar(productoCard)">Agregar al carrito</button>
</div>
</template>

<script>
import {useStore} from 'vuex'
export default {
props:{
  productoCard:Object
},
setup(){
  const store = useStore();
  const agregar = producto =>{
    store.dispatch('agregarAlCarrito', producto)
  }
  return {
    agregar
  }
}
}
</script>

<style>
img{
  width: 270px;
  height: 270px;
}

button{
  background-color: #2e6e52 !important;
  border: 1px solid gray;
  margin-bottom: 10px;
}
button:hover{
  background-color: #37976c !important;
  border: 1px solid gray;
}

span{
  font-size: 24px;
  font-weight: 700;
}
</style>