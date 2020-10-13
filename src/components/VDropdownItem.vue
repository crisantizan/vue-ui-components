<script>
export default {
	functional: true,

	props: {
		tag: { type: String, default: 'div' },
	},

	render(createElement, ctx) {
		return createElement(
			ctx.props.tag,
			{
				...ctx.data,
			},
			ctx.children,
		);
	},
};
</script>
