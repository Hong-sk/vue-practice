<template>
	<div @click="consoleD">ddd</div>
</template>

<script>
import { reactive, toRefs } from "vue";

export default {
	setup() {
		const state = reactive({
			count: 0,
			name: "홍성권",
		});
		const consoleD = () => {
			console.log(state);
		};

		return {
			...toRefs(state),
			consoleD,
		};
	},
};
</script>

<style lang="scss" scoped></style>
