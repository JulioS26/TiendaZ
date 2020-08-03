<template>
	<div>
		<b-container>

			<b-row>
				<b-col cols="3" class="">
					<div class="text-center">
						<b-button variant="primary" @click="habilitar">
							Buscqueda por filtro
						</b-button>
					</div>

					<div v-if="(disabled==false)">
						<b-form-group label="Categoria" >
							<b-form-radio v-model="selected2" name="some-radios" value="Todos">Todos</b-form-radio>
							<b-form-radio v-model="selected2" name="some-radios" value="Damas">Damas</b-form-radio>
							<b-form-radio v-model="selected2" name="some-radios" value="Caballeros">Caballeros</b-form-radio>
							<b-form-radio v-model="selected2" name="some-radios" value="Niños">Niños</b-form-radio>
						</b-form-group>
					</div>
								
					<div v-if="(disabled==false)">
						<b-form-group label="Talla">
							<template>

								<div >
									<b-form-group >
										<b-form-checkbox-group
										v-model="selected"
										:options="options"
										stacked
										buttons
										class="px-1"
										></b-form-checkbox-group>

										<b-form-checkbox-group
										v-model="selected"
										:options="options2"
										stacked
										buttons
										class="px-1"
										></b-form-checkbox-group>

										<b-form-checkbox-group
										v-model="selected"
										:options="options3"
										stacked
										buttons
										class="px-1"
										></b-form-checkbox-group>

										<b-form-checkbox-group
										v-model="selected"
										:options="options4"
										stacked
										buttons
										class="px-1"
										></b-form-checkbox-group>
									</b-form-group>
								</div>
								<div class="mt-3">Selected: <strong>{{ selected }}</strong></div>

							</template>
						</b-form-group>
					</div>

					<div v-if="(disabled==false)">
						<b-form-group label="Categoria">
							<template>
								<div>
									<b-form-select v-model="selected3" :options="options5"></b-form-select>
									<div class="mt-3">Selected: <strong>{{ selected3 }}</strong></div>
								</div>
							</template>
						</b-form-group>
					</div>
					
					<div v-if="(disabled==false)">
					<b-form-group label="Marcas">

					</b-form-group>
					</div>
				</b-col>
				<b-col cols="9">
					<b-row>
						<b-col>
							<b-form-group label="Buscar por categorias">
								<div>
									<b-nav tabs >
										<b-nav-item @click="todos">Todos</b-nav-item>
										<b-nav-item @click="damas">Damas</b-nav-item>
										<b-nav-item @click="caballeros">Caballeros</b-nav-item>
										<b-nav-item @click="ninos">Niños</b-nav-item>
									</b-nav>
									<div v-if="(todo==true)" class="row">
										<div class="col tabs">							
											<img src="@/assets/zapatos/category_sp_01.svg">
										</div><div class="col tabs">							
											<img src="@/assets/zapatos/category_sp_01.svg">
										</div><div class="col tabs">							
											<img src="@/assets/zapatos/category_sp_01.svg">
										</div>
									</div>
									<div v-if="(dama==true)" class="tabs">
										Damas
									</div>
									<div v-if="(caballero==true)" class="tabs">
										Caballeros
									</div>
									<div v-if="(nino==true)" class="tabs">
										Niños
									</div>
								</div>
						</b-form-group>
						</b-col>
					</b-row>
					<!-- <b-row>
						<b-col cols="9">
							<b-form-group label="Buscar por marca">
								<div class="row">
									<Carousel/> 
								</div>
							</b-form-group>
						</b-col>
					</b-row> -->
					<b-row>
						<b-col>
							<b-form-group label="Buscar por popular">
								<b-nav tabs>
									<b-nav-item @click="todos2">Todos</b-nav-item>
									<b-nav-item @click="damas2">Damas</b-nav-item>
									<b-nav-item @click="caballeros2">Caballeros</b-nav-item>
									<b-nav-item @click="ninos2">Niños</b-nav-item>
								</b-nav>
								<div v-if="(todo2==true)">
									<V-main>									
										<b-row>
											<b-col cols="2" v-for="producto in productos" :key="producto.id">
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
														<label v-if="producto.cantidad==0">Sin stock</label>
														<b-button v-if="producto.cantidad >= 1" @click="agregarCarrito(producto)" variant="info">Agregar al carrito</b-button>
													</v-card-actions>
												</v-card>
												</template>
											</b-col>
										</b-row>	
										
									</V-main>
								</div>
								<div v-if="(dama2==true)">
									Popular Damas
								</div>
								<div v-if="(caballero2==true)">
									Popular Caballeros
								</div>
								<div v-if="(nino2==true)">
									Popular Niños
								</div>
							
							</b-form-group>
						</b-col>
					
					</b-row>
				</b-col>
			</b-row>




	
		</b-container>
	</div>

</template>

<script>
	// import Carousel from './Carousel.vue'
	export default {
		data() {
			return {
				productos:[
				{id:1, name:'manzana', precio:50, cantidad:20, carrito:false},
				{id:2, name:'cambur', precio:100, cantidad:20, carrito:false},
				{id:3, name:'pera', precio:75, cantidad:20, carrito:false},
				{id:4, name:'naranja', precio:90, cantidad:20, carrito:false},
				{id:5, name:'fresa', precio:30, cantidad:20, carrito:false},
				{id:6, name:'uvas', precio:25, cantidad:20, carrito:false},
				{id:7, name:'kiwi', precio:125, cantidad:0, carrito:false},
				{id:8, name:'Sandia', precio:200, cantidad:20, carrito:false},
				{id:9, name:'Carne', precio:700, cantidad:20, carrito:false},
				],
				disabled:true,
				selected: [],
				selected2: '',
				selected3: '',
				dialog: false,
				options: [
				{ text: '25', value: 25 },
				{ text: '26', value: 26 },
				{ text: '27', value: 27 },
				{ text: '28', value: 28 },
				{ text: '29', value: 29 }
				],
				options2 : [
				{ text: '30', value: 30 },
				{ text: '31', value: 31 },
				{ text: '32', value: 32 },
				{ text: '33', value: 33 },
				{ text: '34', value: 34 }
				],
				options3 : [
				{ text: '35', value: 35 },
				{ text: '36', value: 36 },
				{ text: '37', value: 37 },
				{ text: '38', value: 38 },
				{ text: '39', value: 39 }
				],
				options4 : [
				{ text: '40', value: 40 },
				{ text: '41', value: 41 },
				{ text: '42', value: 42 },
				{ text: '43', value: 43 },
				{ text: '44', value: 44 }
				],
				options5 : [
				{ text: 'Zapatos', value: 'Zapatos' },
				{ text: 'Cholas', value: 'Cholas' },
				{ text: 'Sandalias', value: 'Sandalias' },
				{ text: 'Deportivos', value: 'Deportivos' },
				{ text: 'Mas', value: 'Mas' }
				],
				todo:true,
				dama:false,
				caballero:false,
				nino:false,
				todo2:true,
				dama2:false,
				caballero2:false,
				nino2:false,
				show: false,
				model: null,
				images:[
				{url:'@/assets/apolo.png', value:'Apolo'}
				]
			}
		},
		computed: {

		},
		components:{
			// Carousel
		},
		methods:{
			habilitar(){
				this.disabled=!this.disabled
			},
			damas(){
				this.dama=true, this.todo=false, this.caballero=false, this.nino=false 
			},
			todos(){
				this.todo=true, this.dama=false, this.caballero=false, this.nino=false 
			},
			caballeros(){
				this.caballero=true, this.dama=false, this.todo=false, this.nino=false 
			},
			ninos(){
				this.nino=true, this.dama=false, this.todo=false, this.caballero=false 
			},
			damas2(){
				this.dama2=true, this.todo2=false, this.caballero2=false, this.nino2=false 
			},
			todos2(){
				this.todo2=true, this.dama2=false, this.caballero2=false, this.nino2=false 
			},
			caballeros2(){
				this.caballero2=true, this.dama2=false, this.todo2=false, this.nino2=false 
			},
			ninos2(){
				this.nino2=true, this.dama2=false, this.todo2=false, this.caballero2=false 
			}
		}
	}
</script>

<style type="text/css">
	.container{
		width: 100%;
	}
	.tabs{
		width:15%;

	}

	.tabs:hover{
		background: rgba(0,0,0,0.4);
	}
</style>	