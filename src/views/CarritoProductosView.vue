<template>
  <layout>
    <h2>Detalle del carrito de compras</h2>
    <table class="table">
      <thead>
        <tr>
          <th>#</th>
          <th>Item</th>
          <th>Cantidad</th>
          <th>Acción</th>
          <th>Total</th>
        </tr>
      </thead>

      <tbody>
        <!-- Aqui se renderizaran los items (productos) -->
        <Item v-for="item in carrito" :key="item.id" :itemProp="item"/>
      </tbody>

      <tfoot>
        <tr>
          <th colspan="5" v-if="Object.keys(carrito).length ===0">Carrito Vacio, Ningún producto seleccionado</th>
          <FooterTotal />
        </tr>
      </tfoot>

    </table>
  </layout>
</template>

<script>
//vuex
import {useStore} from 'vuex';
import {computed} from 'vue'
//componentes
import Layout from '../layout/Layout.vue'
import FooterTotal from '../components/FooterTotal.vue';
import Item from '../components/Item.vue'


export default {
  components:{
    Layout,
    FooterTotal,
    Item
  },
  setup(){
    const store = useStore();
    const carrito = computed( () => store.state.carrito);
    return{
      carrito
    }
  }

}
</script>

<style>

</style>