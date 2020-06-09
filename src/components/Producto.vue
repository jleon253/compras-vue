<template>
	<div class="card">
		<img :src="prod.imagen" class="card-img-top" alt="Imagen" />
		<div class="card-body">
			<h5 class="card-title">
        {{ prod.titulo }}
      </h5>
			<p class="card-text">
				Precio: ${{ prod.precio }}
			</p>
			<button @click="agregarACarro(prod)" :disabled="existe" class="btn btn-success btn-sm btn-block">
        {{ existe ? "Agregado" : "Agregar a Carrito"}}
      </button>
		</div>
	</div>
</template>
<script>
	export default {
		name: 'Producto',
    props: {
      prod: Object,
      existe: Boolean
    },
    methods: {
       agregarACarro: function(prod){
         this.$emit('agregarACarro', prod);
       }
    }
	}
</script>
<style scoped>
  .btn:disabled{
    cursor: no-drop;
  }
</style>
