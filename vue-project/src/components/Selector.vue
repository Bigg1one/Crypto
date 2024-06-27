<template>
	<ul>
		<li @click="selectItem('BTC')" :className="current == 'BTC'? 'active' : ''">Bitcoin</li>
		<li @click="selectItem('ETH')" :className="current == 'ETH'? 'active' : ''">ETH</li>
		<li @click="selectItem('USDT')" :className="current == 'USDT'? 'active' : ''">USDT</li>
	</ul>
</template>

<script>
export default {
    props:{
        setCrypto:{
            type:Function,
            required:true
        }
    },
    data(){
        return{
            current:''
        }
    },
    methods:{
        selectItem(val){
            this.setCrypto(val);
            this.current = val;
        }
    }
}
</script>

<style scooped>
ul {
	list-style: block;
	width: 200px;
	padding: 0;
	border-radius: 3px;
	border: 3px solid #270236;
}
li {
	display: block;
	background: #310353;
	color: #fff;
	padding: 20px 0;
}
li:hover,
li.active {
	background: #24043e;
	cursor: pointer;
}
</style>
