<script>
import axios from "axios";
import SearchBar from "./SearchBar.vue";

export default {
	data() {
		return {
			cards: [],
			archetypes: [],

			api: {
				uriCardFilter: "https://db.ygoprodeck.com/api/v7/cardinfo.php?&archetype=",
			},
		};
	},

	props: {
		dataSelect: Array,
	},
	components: { SearchBar },

	emits: ["change-selection"],

	methods: {
		fetchCards() {
			axios.get("https://db.ygoprodeck.com/api/v7/cardinfo.php?num=20&offset=0").then((response) => {
				const cardsData = response.data.map((card) => {
					const { id, archetype, name, card_images } = card;
					return { id, archetype, name, image: card_images[0].image_url };
					// console.log(response.data.data);
				});
				this.cards = cardsData;
			});
		},

		fetchArchetypes() {
			axios.get("https://db.ygoprodeck.com/api/v7/archetypes.php").then((response) => {
				const archetypesData = response.data.map((archetype) => {
					return archetype.archetype_name;
					console.log(response.archetypes);
				});

				this.archetypes = archetypesData;
				// console.log(response.data.data);
			});
		},
	},

	filterCards(term) {
		this.fetchCards(this.api.uriCardFilter + term);
		this.$emit("change-selection", term);
	},
	created() {},
};
</script>

<template>
	<SearchBar data="dataSelect" @change-selection="filterCards" />
	<section class="container text-center">
		<div class="row">
			<div class="col-2" v-for="card in cards" :key="card.id">
				<img :src="card.card_images[0].image_url" class="card-img" />

				{{ card.name }}
				{{ card.archetype }}
			</div>
		</div>
	</section>
</template>

<style lang="scss" scoped>
.card-img {
	background-color: orange;
}
</style>
