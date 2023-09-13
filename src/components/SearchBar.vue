<script>
import axios from "axios";
export default {
	data() {
		return {
			title: "Yu-Gi-Ho- Api",
			archetypes: [],
		};
	},
	props: {
		placeholder: String,
		select: String,
	},

	methods: {
		featchType() {
			axios.get("https://db.ygoprodeck.com/api/v7/cardinfo.php?num=20&offset=0").then((response) => {
				this.archetypes = response.data.data[0].archetype;
				// console.log(response.data.data[0].archetype);
			});
		},
	},
	created() {
		this.featchType();
	},
};
</script>

<template>
	<form action="">
		<h1>{{ title }}</h1>
		<div class="input-group mb-3">
			<input type="text" class="form-control" :placeholder="placeholder || 'search'" />
		</div>
		<select class="form-select mb-4 w-25">
			<option selected>Open this select menu</option>
			<option value="1">Alien</option>
			<option value="2">Noble Knight</option>
			<option value="3">Tainted Treasure</option>
		</select>
	</form>
</template>

<style lang="scss" scoped>
h1 {
	margin-bottom: 20px;
	text-align: center;
}
</style>
