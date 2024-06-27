<template>
	<input
		min="0"
		type="number"
		@input="changeAmount($event.target.value)"
		placeholder="Введите число"
	/> <br>
    <button @click="convert()">Конвертировать</button>
</template>

<script>
export default {
	props: {
		changeAmount: {
			type: Function,
			required: true,
		},
		convert: {
			type: Function,
			required: true,
		},
	},
}
</script>

<style scooped>
input {
	outline: none;
	border-radius: 3px;
	width: 500px;
	position: relative;
	top: -50px;
	font-size: 1.2em;
	border: 0;
	padding: 10px 15px;
	background: rgb(219, 219, 219);
}
button{
    position: relative;
    top: -20px;
    padding: 15px 20px;
    color: #fff;
    text-transform: uppercase;
    cursor: pointer;
    background: #310353;;
    border: 0;
    border-radius: 3px;
}
button:hover,
button.active {
	background: #24043e;
	cursor: pointer;
}
</style>
