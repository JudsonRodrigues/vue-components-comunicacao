<template>
	<div class="row">
		<!-- coluna 1 -->
		<div class="col-8">
			<h2>Filmes</h2>

			<ul class="list-group list-group-flush">
				<filmes-lista-iten
					v-for="filme in filmes"
					:key="filme.id"
					:filme="filme"
					:class="aplicarClasseActive(filme)"
					@selecionarFilme="filmeSelecionado = $event"
				/>
			</ul>
		</div>
		<!-- coluna 2 -->
		<div class="col-4">
			<FilmesListaItenInfo v-if="!editar" :filme="filmeSelecionado" @editarFilme="editarFilme" />

			<FilmesListaItenEditar v-else :filme="filmeSelecionado" />
		</div>
	</div>
</template>

<script>
import { eventBus } from "./../main.js";

import FilmesListaIten from "./FilmesListaIten.vue";
import FilmesListaItenInfo from "./FilmesListaItenInfo.vue";
import FilmesListaItenEditar from "./FilmesListaItenEditar.vue";

export default {
	components: {
		FilmesListaIten,
		FilmesListaItenInfo,
		FilmesListaItenEditar
	},
	data() {
		return {
			filmes: [
				{
					id: 1,
					titulo: "Vingadores: Guerra Infinita",
					ano: 2018,
					diretor: "Stan Lee"
				},
				{ id: 2, titulo: "Pantera Negra", ano: 2018, diretor: "Stan Lee" },
				{
					id: 3,
					titulo: "Homem Formiga e Vespa",
					ano: 2018,
					diretor: "Stan Lee"
				},
				{ id: 4, titulo: "Deadpool", ano: 2018, diretor: "Stan Lee" },
				{ id: 5, titulo: "Superman DC", ano: 2018, diretor: "Stan Lee" }
			],
			filmeSelecionado: undefined,
			editar: false
		};
	},

	methods: {
		aplicarClasseActive(filmeIterado) {
			return {
				active:
					this.filmeSelecionado && this.filmeSelecionado.id === filmeIterado.id
			};
		},
		editarFilme(filme) {
			this.editar = true;
			this.filmeSelecionado = filme;
		}
	},

	created() {
		eventBus.$on("selecionarFilme", filmeSelecionado => {
			this.filmeSelecionado = filmeSelecionado;
		});
	}
};
</script>
