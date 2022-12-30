<template>
	<div>
		<!-- 일반적인 사용형태 -->
		<ul>
			<li v-for="(userName, idx) in users" :key="idx">{{ userName }}</li>
		</ul>
	</div>
	<div>
		<!-- 객체 사용형태 -->
		<ul>
			<li v-for="(value, key, idx) in info" :key="idx">
				{{ key }} : {{ value }}
			</li>
		</ul>
	</div>
</template>

<script>
import { reactive } from "vue";

export default {
	setup() {
		const users = reactive(["홍", "성", "권"]);
		const info = reactive({
			name: "홍성권",
			age: 25,
			gender: "male",
		});
		return { users, info };
	},
};
</script>

<style scoped></style>
