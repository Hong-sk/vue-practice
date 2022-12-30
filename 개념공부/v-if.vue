<template>
	<div>
		<button @click="changeActive">클릭</button>
		<template v-if="isActive">
			<p>여러 요소를 if 처리 하고 싶으면</p>
			<p>해당 요소들을 template으로 감싸요</p>
			<p>그리고 한 요소에 v-for과 v-if를 동시 사용하지 마세요</p>
			<p>computed를 쓰거나 template을 사용하면 돼요!</p>
		</template>
	</div>
</template>

<script>
import { ref } from "vue";
export default {
	setup() {
		const isActive = ref(false);
		const changeActive = () => {
			isActive.value = !isActive.value;
		};
		return { isActive, changeActive };
	},
};
</script>

<style scoped></style>
