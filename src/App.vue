<template>
	<div>
		<h2>ref 사용됨</h2>
		<button @click="changeFirst">실험해보기</button>
		<p>{{ refMessage }}</p>
		<hr />
		<h2>reactive 사용됨</h2>
		<button @click="changeSecond">실험해보기</button>
		<p>{{ reactiveMessage.message }}</p>
		<hr />
		<h2>참조타입인데 그럼 ref 사용이 가능할까?</h2>
		<button @click="changeThird">실험해보기</button>
		<p>{{ refUseReactiveMessage.message }}</p>
		<hr />
		<h2>반대의 경우는?</h2>
		<button @click="changeFourth">실험해보기</button>
		<p>{{ reactiveUsePrimitiveMessage }}</p>
		<hr />
	</div>
	<button @click="seeResult">
		{{ resultOpened ? "돌아가기" : "결과보기" }}
	</button>
	<div v-if="resultOpened">
		<p>
			number나 string 등 원시타입 형태의 경우 ref를 사용하고, 객체나 배열 등
			참조타입 형태의 경우 reactive를 사용하면 역시 잘 수행됨.
		</p>
		<p>
			참조타입의 경우 ref를 사용했을 때 화면 상의 변화는 발생하지만, 접근할 때
			`${변수이름}.value.${key이름}` 으로 접근해야 하므로 번거로움 발생. 따라서
			그냥 reactive 쓰는게 편한 듯 싶음.
		</p>
		<p>
			원시타입 형태를 reactive 함수에 때려넣었을 때 값은 바뀌지만 화면 상의
			변화가 발생하지 않음. 사용하지 말 것.
		</p>
	</div>
</template>

<script>
import { ref, reactive } from "vue";
export default {
	setup() {
		const refMessage = ref("ref는 원시타입의 반응형 상태를 생성하기 위한 함수");
		const changeFirst = () => {
			refMessage.value = refMessage.value + "!";
		};
		const reactiveMessage = reactive({
			message: "reactive는 참조타입의 반응형 상태를 생성하기 위한 함수",
		});
		const changeSecond = () => {
			reactiveMessage.message = reactiveMessage.message + "!";
		};
		const refUseReactiveMessage = ref({
			message: "참조타입인데 그럼 ref 사용이 가능할까?",
		});
		const changeThird = () => {
			refUseReactiveMessage.value.message =
				refUseReactiveMessage.value.message + "!";
		};
		let reactiveUsePrimitiveMessage = reactive("이거는 될까?");
		const changeFourth = () => {
			reactiveUsePrimitiveMessage = reactiveUsePrimitiveMessage + "!";
		};

		let resultOpened = ref(false);
		const seeResult = () => {
			resultOpened.value = !resultOpened.value;
		};
		return {
			refMessage,
			reactiveMessage,
			refUseReactiveMessage,
			reactiveUsePrimitiveMessage,
			changeFirst,
			changeSecond,
			changeThird,
			changeFourth,
			resultOpened,
			seeResult,
		};
	},
};
</script>

<style lang="scss" scoped></style>
