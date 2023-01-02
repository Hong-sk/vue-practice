<template>
	<div>
		<h3>v-text는 mustache 사용 방법과 일치합니다</h3>
		<p v-text="exampleRef"></p>
		<p>{{ exampleRef }}</p>
	</div>

	<h3>v-memo 사용법</h3>
	<div v-memo="[exampleNum]">바뀌는 숫자 : {{ exampleNum }}</div>
	<div v-memo="[exampleRef]">바뀌지 않는 숫자 : {{ exampleNum }}</div>
	<button @click="exampleNum++">증가</button>

	<hr />
	<div>
		<div class="loading">v-cloak는 로딩 등의 특수 상황에서 사용합니다.</div>
	</div>

	<hr />
	<p>v-pre는 해당 엘리먼트의 컴파일을 생략합니다.</p>
	<div v-pre>{{ exampleNum }}</div>
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
