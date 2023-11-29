<script setup>
import { ref, computed } from 'vue';
	// const miNombre = "Jesus"
	// const stylesInVue = "color: cyan"
	// const arrayObjects = ["Vue", "React", "Svelte", "Blue"]
	// const active = 2
	// const fruits = ["Apple", "Coconut", "Pineapple", "Barry"]
	// const arrayFrutas = [
    //     {
    //         name: "Manzana",
    //         price: "$1.00",
    //         description: "Una manzana",
	// 		id: "A"
    //     },
    //     {
    //         name: "Pera",
    //         price: "$2.00",
    //         description: "Una pera",
	// 		id: "B"
    //     },
    //     {
    //         name: "Naranja",
    //         price: "$3.00",
    //         description: "Una naranja",
	// 		id: "C"
    //     },
    // ];
	// const list = {
	// 	work: "dev",
	// 	set: "home",
	// 	guide: "1",
	// 	id: "only"
	// }
// 	const arrayFrutas = [
//     {
//         name: "Manzana",
//         price: "$1.00",
//         description: "Una manzana",
//         stock: 0,
//     },
//     {
//         name: "Pera",
//         price: "$2.00",
//         description: "Una pera",
//         stock: 10,
//     },
//     {
//         name: "Naranja",
//         price: "$3.00",
//         description: "Una naranja",
//         stock: 20,
//     },
// ];

const undClick = (message) => {
	console.log(message)
}
const count = ref(0);

const decrement = () => (count.value --);
const increment = () => (count.value ++);
const reset = () => (count.value = 0);
const add = () => favoriteArray.value.push(count.value)
const remove = () => favoriteArray.value.pop(count.value)
const blockAdd = computed(() => {
	const numSearch = favoriteArray.value.find(num => num === count.value)
	console.log(numSearch)
	// if (numSearch === 0) return true;
	// return numSearch ? true : false;
	return numSearch || numSearch === 0;
})

const classCounter = () =>{
	if (count.value === 0) {
		return 'zero'
	} else if (count.value > 0) {
		return 'positive'
	} else return 'negative'
}
const favoriteArray = ref([])

</script>

<!-- <h1>Hola {{ miNombre.toLowerCase() }}, esto es vue.js!</h1><br>
	<p>Sub de vue, mantente constante</p> -->
	<!-- <h2>{{ arrayObjects }}</h2> -->
	<!-- También en su versión abreviada queda de la siguiente manera :style en vez de v-bind:style, ambas expresiones son compilables -->
	<!-- <h2 :style = "`color: ${arrayObjects[3]}}`">Probando los estilos</h2> -->

	<!-- <h2 v-if="active === true">I'm active</h2>
		<p v-else-if="active === false">I'm best</p>
		<p v-else-if="active == '2'">I'm gold</p>
		<p v-else>I'm indeciso</p><br> -->
	<!-- Today learn v-for!
		delete the previous, now you know-->

		<!-- <ul>
			<li v-for="fruit, index in fruits"
			:key="index"
			>
			{{index}} - {{ fruit }}
        </li>
	</ul> -->

	<!-- <ul>
		<li v-for="Fruit in arrayFrutas"
			:key="fruit"
		>
			{{ Fruit.name }} - {{ Fruit.price }} - {{ Fruit.description }}
		</li>
	</ul> -->
	
	<!-- in this order quick access to, first the value, second the property nd finally the index -->
	<!-- <ul>
		<li v-for="value, property, i in list" :key="value"
		
		>
		{{ i }} - {{ property }}: {{ value }} 
	</li>
</ul> -->

<!-- <ul>
	<template
	v-for="item in arrayFrutas"
	:key="item.name">
	<li
	v-if="item.stock > 0">
	{{ item.name }}: {{ item.price }}
</li>
</template>
</ul> -->

<!-- <button v-on:click.middle="undClick('CMid')">Middle</button>
	<button @click.right.prevent="undClick('CRight')">Right</button>
	<button @click.left="undClick('CLeft')">Left</button>
	<br><br> -->

<template>
	<div class="container text-center mt-3" >
		
		<h1>Choose your number</h1>
		
		<div class="btn-group">
			<button @click="increment" class="btn btn-success">Increase</button>
			<button @click="decrement" class="btn btn-warning">Diminish</button>
			<button @click="reset" class="btn btn-secondary">Reset</button>
			<button @click="add" :disabled="blockAdd" class="btn 	btn-primary">Add</button>
			<button @click="remove" class="btn btn-danger">Remove</button>
		</div>
					<ul class="list-group mt-4">
						<li v-for="(num, index) in favoriteArray"
						:key="index"
						class="list-group-item"
							>
							{{ num }}
						</li>
					</ul>
		<h2 :class="classCounter()"> {{ count }} </h2>
	</div>
</template>

<style>
.positive {
	color: green;
}

.negative {
	color: red;
}

.zero {
	color: rgb(196, 185, 44);
}
h1  {
    color: rgb(44, 135, 100)
}
</style>