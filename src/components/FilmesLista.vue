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
			<FilmesListaItenInfo />
		</div>
	</div>
</template>

<script>
import FilmesListaIten from "./FilmesListaIten.vue";
import FilmesListaItenInfo from "./FilmesListaItenInfo.vue";

export default {
	components: {
		FilmesListaIten,
		FilmesListaItenInfo
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
			filmeSelecionado: undefined
		};
	},

	methods: {
		aplicarClasseActive(filmeIterado) {
			return {
				active:
					this.filmeSelecionado && this.filmeSelecionado.id === filmeIterado.id
			};
		}
	}
};
</script>
