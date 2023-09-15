<script>
import { store } from "../components/data/store";
export default {
	data() {
		return {
			store,
			title: "list-card",
		};
	},
};
</script>

<template>
	<div class="container">
		<h1>
			{{ title }}
		</h1>
		<div class="row g-4 text-center mb-4">
			<div class="col-2" v-for="card in store.cards" :key="card.id">
				<img :src="card.card_images[0].image_url" class="image-card" />
				{{ card.name }}
				{{ card.archetype }}
			</div>
		</div>
	</div>
</template>
<style lang="scss" scoped>
.image-card {
	width: 100%;
}
</style>
