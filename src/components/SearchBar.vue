<script>
export default {
	data() {
		return {
			selectData: "",
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
		<select v-model="selectData" @change="$emit('change-selection', selectData)" class="form-select mb-4 w-25">
			<option value="" selected>Seleziona un Valore</option>
			<option :value="option" v-for="option in data">{{ option }}</option>
		</select>
	</div>
</template>

<style lang="scss" scoped></style>
