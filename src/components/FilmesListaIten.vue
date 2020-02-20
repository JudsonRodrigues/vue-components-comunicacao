<template>
	<!-- <div>
		<input type="text" :value="titulo" :placeholder="$attrs.placeholder" />
	</div>-->
	<li class="list-group-item">
		<span>{{filme.titulo}} | {{filme.ano}}</span>
		<button @click="selecionar()" class="btn btn-secondary float-right">Selecionar</button>
	</li>
</template>

<script>
import { eventBus } from "./../main.js";

export default {
	props: {
		filme: {
			type: Object,
			required: true
		}
	},
	methods: {
		selecionar: function() {
			//this.$emit("selecionarFilme", this.filme);
			eventBus.$emit("selecionarFilme", this.filme);
		}
	}
};
</script>