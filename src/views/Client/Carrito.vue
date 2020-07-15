<template>
	<div>
		<b-container>
			<b-row>
				<b-col cols="3" v-for="(producto, index) in productos" :key="index">
					<template>
						<v-card
						class="mx-auto px-0"
						max-width="200"
						outlined
						>
						<v-img
						height="200"
						width="200"
						src="https://cdn.vuetifyjs.com/images/cards/store.jpg"
						></v-img>
						<v-list-item three-line>
							<v-list-item-content>
								<div class="overline mb-4">{{producto.name}}</div>
								<v-list-item-title class="headline mb-1">{{producto.precio}} Bs</v-list-item-title>
							</v-list-item-content>
							<v-list-item-avatar
							tile
							size="80"
							color="grey"
							></v-list-item-avatar>
						</v-list-item>
						<v-card-actions>
							<b-button @click="agregarCarrito" variant="info">Agregar al carrito</b-button>
						</v-card-actions>
					</v-card>
				</template>
				</b-col>
			</b-row>
			<b-row>
			carrito: {{ carrito }}
			</b-row>
		</b-container>
	</div>
</template>

<script>
	export default{
		name: 'Carrito',
		data(){
			return{
				carrito:[],
				productos:[
				{id:1, name:'manzana', precio:50},
				{id:2, name:'cambur', precio:100},
				{id:3, name:'pera', precio:75},
				{id:4, name:'naranja', precio:90},
				{id:4, name:'fresa', precio:30},
				{id:4, name:'uvas', precio:25},
				{id:4, name:'kiwi', precio:125},
				{id:4, name:'Sandia', precio:200},
				{id:4, name:'Carne', precio:700},
				]
			}
		},
		methods:{
			agregarCarrito(index){
				let i = this.productos[index]
				this.carrito.push(i)
			}
		}
	}
</script>