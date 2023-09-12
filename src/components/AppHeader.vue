<script>
import axios from "axios";
export default {
	data() {
		return {
      title:'hellos',s
			cards: [],
		};
	},

	created() {
		axios.get("https://db.ygoprodeck.com/api/v7/cardinfo.php").then((response) => {
			this.cards = response.data.results;
		});
	},
};
</script>

<template>
	<h1>{{ title }}</h1>
</template>

<style lang="scss" scoped></style>
