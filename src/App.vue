<template>
  <div id="app">
    <Navbar></Navbar>
    <div class="container-fluid my-4">
      <div class="row">
        <div class="col-12 col-sm-12 col-md-8 col-lg-8">
          <div class="row">
            <div class="col-6 col-sm-6 col-md-6 col-lg-6 mb-4" v-for="prod in dataProductos" :key="prod.id">
              <Producto :prod="prod" @agregarACarro="agregarProd" :existe="existeProd(prod)"></Producto>
            </div>
          </div>
        </div>
        <div class="col-12 col-sm-12 col-md-4 col-lg-4">
          <Carrito :items="carrito" @eliminarProducto="eliminarProd" @pagar="pagarTotal"></Carrito>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import dataProductos from './assets/productos.json'
import Producto from './components/Producto'
import Carrito from './components/Carrito'
import Navbar from './components/Navbar'
export default {
  name: 'App',
  components: {
    Producto,
    Carrito,
    Navbar
  },
  data(){
    return {
      dataProductos,
      carrito: []
    }
  },
  methods:{
    agregarProd: function(prod){
      this.carrito.push(prod);
    },
    existeProd(producto){
      let existe = this.carrito.find((item) => item.id === producto.id);
      if(existe) return true;
      return false;
    },
    eliminarProd(producto){
      this.carrito = this.carrito.filter((prod) => prod.id !== producto.id);
    },
    pagarTotal(){
      this.carrito = [];
      alert('Tu compra se ha realizado!!')
    }
  }
}
</script>

<style>
</style>
