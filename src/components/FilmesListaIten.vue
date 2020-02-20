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
export default {
	props: {
		filme: {
			type: Object,
			required: true
		}
	},
	methods: {
		selecionar: function() {
			console.log(this.filme.titulo);
			this.$emit("selecionarFilme", this.filme);
		}
	}
};
</script>