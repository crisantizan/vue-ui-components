<template>
	<div
		v-show="$props.show"
		class="VDropdown__menu"
		:class="{ 'VDropdown__menu--right': $props.alignRight }"
	>
		Menu
	</div>
</template>

<script>
export default {
	props: {
		show: { type: Boolean, default: false },
		alignRight: { type: Boolean, default: false },
	},
};
</script>

<style scoped>
.VDropdown__menu {
	position: absolute;
	z-index: 1000;
	display: block;
	float: left;
	min-width: 10rem;
	padding: 0.5rem 0;
	margin: 0.125rem 0 0;
	font-size: 1rem;
	color: #212529;
	text-align: left;
	list-style: none;
	background-color: #fff;
	background-clip: padding-box;
	border: 1px solid rgba(0, 0, 0, 0.15);
	border-radius: 0.25rem;
	transform: translate3d(0px, 28px, 0px);
	will-change: transform;

	top: 0px;
	left: 0px;
	/*right: auto;*/
}

.VDropdown__menu--right {
	right: 0px;
	left: auto;
}
</style>
