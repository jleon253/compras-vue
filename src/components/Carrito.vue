<template>
	<div class="sticky-top">
		<div class="card">
			<div class="card-header">
				<h3 class="text-center">
          <b>Carrito de compras</b>
        </h3>
			</div>
			<ul class="list-group list-group-flush" v-if="items.length > 0">
				<li
					class="list-group-item d-flex justify-content-between align-items-center"
					v-for="item in items"
					:key="item.id"
				>
					<button
						type="button"
						@click="eliminarProducto(item)"
						class="close text-danger"
						aria-label="Close"
					>
						<span aria-hidden="true">&times;</span>
					</button>
					{{ item.titulo }}
					<span class="badge badge-success badge-pill">
						${{ item.precio }}
					</span>
				</li>
			</ul>
			<ul class="list-group list-group-flush" v-else>
				<li class="list-group-item">
					No hay elementos
				</li>
			</ul>
			<div class="card-footer text-center" v-show="items.length > 0">
				<h4>Total: ${{ total }}</h4>
			</div>
		</div>
		<button class="btn btn-info btn-block btn-lg mt-3" v-show="items.length > 0" @click="$emit('pagar')">PAGAR</button>
	</div>
</template>
<script>
	export default {
		name: 'Carrito',
		props: {
			items: Array,
		},
		computed: {
			total() {
				return this.items.reduce(
					(acumulador, item) => acumulador + Number(item.precio),
					0
				)
			},
		},
		methods: {
			eliminarProducto(item) {
				this.$emit('eliminarProducto', item)
			},
		},
	}
</script>
<style scoped></style>
