<script>
export default {
	data() {
		return {
			selectedData: "",
		};
	},
	props: {
		data: Array,
	},

	emits: ["change-selection"],
};
</script>

<template>
	<div class="container mt-5">
		<select v-model="selectedData" @change="$emit('change-selection', selectedData)" class="form-select mb-4 w-25">
			<option value="" selected>seleziona un tipo</option>
			<option :value="option" v-for="option in data">{{ option }}</option>
		</select>
	</div>
</template>

<style lang="scss" scoped></style>
