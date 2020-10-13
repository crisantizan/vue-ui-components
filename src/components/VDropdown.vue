<template>
	<div class="VDropdown">
		<slot v-bind:show="show" v-bind:toggleFn="toggleFn"></slot>
	</div>
</template>

<script>
export default {
	name: 'Dropdown',
	data: () => ({
		show: false,
	}),

	methods: {
		toggleFn() {
			this.show = !this.show;
		},
	},
};
</script>

<style scoped>
.VDropdown {
	position: relative;
}
</style>
