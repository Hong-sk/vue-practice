<template>
	<div>
		<p>{{ state }}</p>
		<p>{{ lastName }}</p>
		<p>{{ firstName }}</p>
		<p>{{ name }}</p>
		<button @click="changeFirstName">성 바꾸기</button>
		<button @click="changeLastName">이름 바꾸기</button>
	</div>
</template>

<script>
import { reactive, toRef, toRefs } from "vue";

export default {
	setup() {
		const state = reactive({
			lastName: "홍",
			firstName: "성권",
		});

		let { lastName, firstName } = toRefs(state);
		const name = toRef(state, "lastName");
		function changeFirstName() {
			firstName.value = firstName.value + "!";
		}
		function changeLastName() {
			lastName.value = lastName.value + "!";
		}
		return {
			state,
			lastName,
			firstName,
			name,
			changeFirstName,
			changeLastName,
		};
	},
};
</script>

<style lang="scss" scoped></style>
