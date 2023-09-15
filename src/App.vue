<script>
import axios from "axios";
import { store } from "./components/data/store";

import cardList from "./components/cardList.vue";
import SearchBar from "./components/SearchBar.vue";

export default {
	data() {
		return {
			store,
		};
	},
	components: { cardList, SearchBar },

	methods: {
		fetchCard(endpoint) {
			axios.get(endpoint).then((response) => {
				// console.log(response.data.data);
				store.cards = response.data.data.map((card) => {
					const { id, archetype, name, card_images } = card;
					return { id, archetype, name, card_images };
				});
			});
		},

		fetchArchetypes(endpoint) {
			axios.get(endpoint).then((response) => {
				store.archetypes = response.data.map((archetype) => {
					// console.log(archetype);
					return archetype.archetype_name;
				});
			});
		},

		filter(term) {
			// console.log("searched term" + term);
			this.fetchCard(store.uriCardFilter + term);
		},
	},

	created() {
		this.fetchCard(store.apiUri);
		this.fetchArchetypes(store.uriArchetypes);
	},
};
</script>

<template>
	<div class="container">
		<SearchBar :data="store.archetypes" @change-selection="filter" />
		<cardList />
	</div>
</template>

<style lang="scss">
@use "./assets/scss/style.scss";
</style>
