<script>
import AppHeader from "./components/AppHeader.vue";
import SearchBar from "./components/SearchBar.vue";

export default {
	data() {
		return {};
	},
	components: { AppHeader, SearchBar },

	methods: {
		andleSearch(term) {
			console.log("serced term" + term);
		},
	},
};
</script>

<template>
	<div class="container">
		<SearchBar @form-submit="andleSearch()" placeholder="Search attribute" select="attribute" />
	</div>
	<AppHeader />
</template>

<style lang="scss">
@use "./assets/scss/style.scss";
</style>
