<template>
	<div class="user">
        <button class="dada" @click="deleteUser(index)">delete </button>
		<h3>{{ user.name }}</h3>
		<p>
			{{ user.email }} - <b>{{ user.pass }}</b>
		</p>
	</div>
</template>

<script>
export default {
	props: {
		user: {
			type: Object,
			required: true,
		},
        index:{
            type:Number,
            required:true
        },
        deleteUser:{
            type:Function,
            required:true
        },
	},
}
</script>

<style scooped> 
.dada{
    background-color: rgb(0, 0, 0);
    color: rgb(66, 0, 0);
}
</style>
