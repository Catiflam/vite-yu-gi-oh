<script>
import axios from "axios";
import { store } from "./components/data/store";

// import AppHeader from "./components/AppHeader.vue";
import cardList from "./components/cardList.vue";
// import SearchBar from "./components/SearchBar.vue";

export default {
	data() {
		return {
			store,

			// api: {
			// 	uriCards: "https://db.ygoprodeck.com/api/v7/cardinfo.php?num=20&offset=0",
			// 	uriArchetyps: "https://db.ygoprodeck.com/api/v7/archetypes.php",
			// 	uriCardFilter: "https://db.ygoprodeck.com/api/v7/cardinfo.php?&archetype=",
			// },
			// archetypes: [],
			// store,
		};
	},
	components: { cardList },
	methods: {
		fetchCard(endpoint) {
			axios.get(endpoint).then((response) => {
				console.log(response.data.data);
				store.cards = response.data.data;
			});
		},
	},
	created() {
		this.fetchCard(store.apiUri);
	},
};

// methods: {
// 	fetchCards(endPoint) {
// 		axios.get(endPoint).then((response) => {
// 			const cardsData = response.data.data.map((card) => {
// 				const { id, archetype, name, card_images } = card;
// 				return { id, archetype, name, image: card_images[0].image_url };
// 			});

// 			store.cards = cardsData;
// 			// console.log(response.data.data);
// 		});
// 	},
// 	fetchArchetypes(endPoint) {
// 		axios.get(endPoint).then((response) => {
// 			const archetypesData = response.data.map((archetype) => {
// 				return archetype.archetype_name;
// 			});

// 			this.archetypes = archetypesData;
// 			// console.log(response.data.data);
// 		});
// 	},
// 	filterCards(term) {
// 		// console.log("searched term" + term);
// 		this.fetchCards(this.api.uriCardFilter + term);
// 	},
// },

// created() {
// 	this.fetchCards(this.api.uriCards);
// 	this.fetchArchetypes(this.api.uriArchetypes);
// },
</script>

<template>
	<div class="container">
		<!-- <SearchBar :data="archetypes" @change-selection="filterCards" /> -->
		<!-- <AppHeader dataSelect="archetypes" @change-selection="filerCards" /> -->
		<cardList />
	</div>
</template>

<style lang="scss">
@use "./assets/scss/style.scss";
</style>
