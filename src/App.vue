<script>
import AppHeader from "./components/AppHeader.vue";
import SearchBar from "./components/SearchBar.vue";

export default {
	data() {
		return {};
	},
	components: { AppHeader, SearchBar },
};
</script>

<template>
	<div class="container">
		<SearchBar />
	</div>
	<AppHeader />
</template>

<style lang="scss">
@use "./assets/scss/style.scss";
</style>
