<template>
	<div>
		<h3>v-text는 mustache 사용 방법과 일치합니다</h3>
		<p v-text="exampleRef"></p>
		<p>{{ exampleRef }}</p>
	</div>

	<h3>v-memo 사용법</h3>
	<div v-memo="[exampleNum]">{{ exampleNum }}</div>
	<button @click="() => (exampleNum = exampleNum++)">증가</button>
</template>

<script>
import { reactive, ref } from "vue";

export default {
	setup() {
		const exampleNum = ref(0);
		const exampleRef = ref("hong");
		const exampleObject = reactive({
			first: "first",
			second: "second",
		});
		const exampleArray = reactive([true, false, 1]);
		return {
			exampleNum,
			exampleRef,
			exampleObject,
			exampleArray,
		};
	},
};
</script>

<style lang="scss" scoped></style>
