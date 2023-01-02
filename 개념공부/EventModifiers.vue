<template>
	<div>알트와 엔터가 동시에 눌러졌을 때만 할일목록에 추가됩니다.</div>
	<input @keyup.enter.alt.exact="addTodo" />
	<ul v-for="(todo, idx) in todos" :key="idx">
		<li>{{ todo }}</li>
	</ul>
	<h3>modifiers 테스트</h3>
	<div class="box" id="big" @click="consoleBig">
		<div class="box" id="middle" @click.self="consoleMiddle">
			<div class="box" id="small" @click="consoleSmall"></div>
			<!--.stop을 명시해주면 이벤트 버블링 효과 해제-->
			<!--.self를 명시해주면 본인을 호출하는 효과에만 반응
				즉 여기서 제일 작은 상자를 눌렀을 때 본인을 누른 것이 아니므로 작동 x-->
			<!--.capture을 명시해주면 캡처모드로 작동-->
		</div>
	</div>
</template>

<script>
import { reactive } from "vue";

export default {
	setup() {
		const todos = reactive([]);
		const addTodo = e => {
			console.log(e.target.value);
			todos.push(e.target.value);
		};
		const consoleBig = () => {
			console.log("큰 상자가 눌렸습니다");
		};
		const consoleMiddle = () => {
			console.log("중간 상자가 눌렸습니다");
		};
		const consoleSmall = () => {
			console.log("작은 상자가 눌렸습니다");
		};
		return { addTodo, todos, consoleBig, consoleMiddle, consoleSmall };
	},
};
</script>

<style scoped>
.box {
	border: 2px solid black;
	display: flex;
	justify-content: center;
	align-items: center;
}

#big {
	width: 200px;
	height: 200px;
}
#middle {
	width: 150px;
	height: 150px;
}
#small {
	width: 80px;
	height: 80px;
}
</style>
