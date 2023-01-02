<template>
	<div></div>
</template>

<script>
import { watch, ref, reactive } from "vue";
export default {
	setup() {
		const person = reactive({
			name: "홍길동",
			age: 30,
			hobby: "운동",
			obj: {
				count: 0,
			},
		});

		watch(
			() => person.obj,
			newValue => {
				console.log("newValue: ", newValue);
			},
		);
		return { person };
	},
};
</script>

<style lang="scss" scoped></style>
