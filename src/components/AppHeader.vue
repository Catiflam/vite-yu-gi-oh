<script>
import axios from "axios";
export default {
	data() {
		return {
			cards: [],
		};
	},
	methods: {
		fetchData() {
			axios.get("https://db.ygoprodeck.com/api/v7/cardinfo.php?num=20&offset=0").then((response) => {
				this.cards = response.data.data;
				// console.log(response.data.data);
			});
		},
	},
	created() {
		this.fetchData();
	},
};
</script>

<template>
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
