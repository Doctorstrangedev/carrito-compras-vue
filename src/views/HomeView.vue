<template>
  <Layout>
    <h3>Contenido de los productos</h3>
    <div class="row d-flex justify-content-between">
      <!-- cards de bootstrap -->
      
         <CardProducto v-for="producto of getProductos" :key="producto.id" :productoCard="producto"/>
      
     
      
    </div>
  </Layout>
</template>

<script>
//acceso al store
import {useStore} from 'vuex';
import {computed, onMounted} from 'vue';
// componentes
import Layout from '../layout/Layout.vue'
import CardProducto from '../components/CardProducto.vue'

export default {
  name: 'HomeView',
  components: {
    Layout,
    CardProducto
  },
  setup(){
    const store = useStore();
    //onMounted se ejecuta antes del template
    onMounted(()=>{
      store.dispatch('getProductoApi')
    });
    //vamos a mapear el state
    const getProductos = computed(()=>store.state.productos);
    return{
      getProductos
    }
  }
}
</script>
