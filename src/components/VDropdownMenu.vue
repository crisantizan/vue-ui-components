<template>
	<div
		v-show="$props.show"
		class="VDropdown__menu"
		:class="{
			'VDropdown__menu--right': $props.alignRight,
			'VDropdown__menu--submenu': $props.submenu,
		}"
		:style="{ transform: transform }"
		:ref="id"
	>
		<slot></slot>
	</div>
</template>

<script>
export default {
	props: {
		show: { type: Boolean, default: false },
		alignRight: { type: Boolean, default: false },
		top: {
			type: String,
			default: '28px',
		},
		submenu: { type: Boolean, default: false },
	},

	data: () => ({
		id: `menu${Date.now()}`,
	}),

	computed: {
		translateX() {
			return this.$props.submenu ? 'translateX(100%)' : '';
		},

		translate3d() {
			return `translate3d(0px, ${this.$props.top}, 0px)`;
		},

		transform() {
			if (this.$props.submenu) {
				return this.translateX;
			}

			return `${this.translate3d} ${this.translateX}`;
		},
	},

	destroyed() {
		document.removeEventListener('click', this.handleClickOutside);
	},

	watch: {
		show(val, oldVal) {
			if (val) {
				setTimeout(() => {
					document.addEventListener('click', this.handleClickOutside);
				}, 10);
			} else {
				document.removeEventListener('click', this.handleClickOutside);
			}
		},
	},

	methods: {
		handleClickOutside(event) {
			// console.log(this.$refs[this.id]);
			// clicked outside
			if (this.$refs[this.id] && !this.$refs[this.id].contains(event.target)) {
				console.log('close');
				this.$emit('onclose', true);
			}
		},
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
	margin: 0.125rem 0 0;
	font-size: 1rem;
	color: #212529;
	text-align: left;
	list-style: none;
	background-color: #fff;
	background-clip: padding-box;
	border: 1px solid rgba(0, 0, 0, 0.15);
	border-radius: 0.25rem;
	/*transform: translate3d(0px, 28px, 0px);*/
	will-change: transform;

	top: 0px;
	left: 0px;
}

.VDropdown__menu--right {
	right: 0px;
	left: auto;
}

.VDropdown__menu--submenu {
	transform: translateX(100%);
}
</style>
