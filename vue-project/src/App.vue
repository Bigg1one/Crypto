<!-- <template>
	<h3>{{ info }}</h3>
    <p>{{ someInfo }}</p>
    <button type="button" v-on:click="userData('some new')">send</button>
</template>
<script>
export default{
    data(){
        return{
            info:'Title',
            someInfo:'anons'
            
        }
    },
    methods:{
        userData(word ='new text'){
            // this.info = 'some new'
            this.someInfo = word
        }
    }
}
</script>

<style scoped>
h3{
    font-weight: lighter;
}
p{
    color: rgb(184, 58, 58);
}
</style> -->

<!-- v-for,v-model,v-if,v-if-else,v-else -->

<!-- <template>
    <input type="text" v-model="userName" placeholder="имя">
    <input type="password" v-model="userEmail" placeholder="пароль">
    <input type="email" v-model="userPass" placeholder="email">
    <p className="error">{{ error }}</p>
    <button @click="sendData()">send</button>

    <div v-if="users.length==0">
    we have not users
    </div>
    <div v-else-if="users.length==1">
    we have  1  user
    </div>
    <div v-else="users.length==1">
    we have  more then 1  user
    </div>
    <div v-for="(el, index) in users" :key="index" class="user">
        <h3>{{ el.name  }}</h3>
        <p>{{ el.email }} - <b>{{ el.pass }}</b></p>
    </div>
</template>

<script>
export default {
    data(){
        return{
            users:[],
            error:'',
            userName: '',
            userPass: '',
            userEmail: ''
        }
    },
    methods: {
        sendData(){
            if(this.userName == '') {
                this.error= 'no name';
                return;
            } else if (this.userEmail == ''){
                this.error =  'email was not added';
                return;
            }
            else if (this.userPass == ''){
                this.error =  'pass was not added';
                return;
            }
            this.error = '';

            this.users.push({
                name:this.userName,
                pass:this.userPass,
                email:this.userEmail
            })

        }

    }
}
</script>

<style scooped>
</style> -->

<!-- <template>
	<input type="text" v-model="userName" placeholder="имя" />
	<input type="password" v-model="userEmail" placeholder="пароль" />
	<input type="email" v-model="userPass" placeholder="email" />
	<p className="error">{{ error }}</p>
	<button @click="sendData()">send</button>

	<div v-if="users.length == 0">we have not users</div>
	<div v-else-if="users.length == 1">we have 1 user</div>
	<div v-else="users.length == 1">we have more then 1 user</div>
	<User
		v-for="(el, index) in users"
		:key="index"
		class="user"
		:user="el"
		:index="index"
        :deleteUser="deleteUser"
	/>
</template>

<script>
import User from './components/User.vue'

export default {
	components: { User },
	data() {
		return {
			users: [],
			error: '',
			userName: '',
			userPass: '',
			userEmail: '',
		}
	},
	methods: {
		sendData() {
			if (this.userName == '') {
				this.error = 'no name'
				return
			} else if (this.userEmail == '') {
				this.error = 'email was not added'
				return
			} else if (this.userPass == '') {
				this.error = 'pass was not added'
				return
			}
			this.error = ''

			this.users.push({
				name: this.userName,
				pass: this.userPass,
				email: this.userEmail,
			})
		},
		deleteUser(index) {
			this.users.splice(index, 1)
		},
	},
}
</script>

<style scooped></style> -->

<!-- Приложение -->

<!-- <template>
	<div class="wrapper">
		<h1>Погодное приложение</h1>
		<p>Узнать погоду в {{ city == '' ? ' вашем городе' : cityName }}</p>
		<input type=" text" v-model="city" placeholder="add city" />
		<button v-if="city != ''" @click="getWeather()">Get Info</button>
		<button disabled v-else>Add</button>
		<p class="error">{{ error }}</p>
		<div v-if="info != null">
			<p >{{showTemp }}</p>
			<p >{{showFeelsLike }}</p>
			<p >{{showMinTemp }}</p>
			<p >{{showMaxTemp }}</p>
		</div>
	</div>
</template>

<script>
import axios from 'axios'

export default {
	data() {
		return {
			city: '',
			error: '',
			info: null,
		}
	},
	computed: {
		cityName() {
			return '╚' + this.city + '╚'
		},
		showTemp() {
			return 'Температура:' + this.info.main.temp
		},
		showFeelsLike() {
			return 'Ощущается как:' + this.info.main.feels_like
		},
		showMinTemp() {
			return 'Минимальная температура:' + this.info.main.temp_min
		},
		showMaxTemp() {
			return 'Максимальная температура:' + this.info.main.temp_max
		},
	},
	methods: {
		getWeather() {
			if (this.city.trim().length < 2) {
				this.error = 'need more then 1 symbol'
				return false
			}
			this.error = ''

			axios
				.get(
					`https://api.openweathermap.org/data/2.5/weather?q=${this.city}&units=metric&appid=b219673782ba3c974f6ec80a207941d8`
				)
				.then(res => (this.info = res.data))
		},
	},
}
</script>

<style scooped>
.error {
	color: #867028;
}
.wrapper {
	width: 900px;
	height: 500px;
	border-radius: 50px;
	padding: 20px;
	background: rgb(51, 68, 141);
	text-align: center;
	color: white;
	margin: 50px;
}

.wrapper h1 {
	margin-top: 50px;
	font-size: 4em;
}
.wrapper p {
	margin-top: 20px;
}

.wrapper input {
	margin-top: 30px;
	background: transparent;
	border: 0;
	border-bottom: 2px solid #311c1c;
	color: aliceblue;
	font-size: 14px;
	padding: 5px 8px;
	outline: none;
}
.wrapper input:focus {
	border-bottom-color: rgb(146, 69, 190);
}
.wrapper button {
	background: rgb(146, 69, 190);
	color: #fff;
	border-radius: 10px;
	border: 2px solid rgb(101, 69, 190);
	padding: 10px 15px;
	margin-left: 20px;
	cursor: pointer;
	transition: transform 500ms ease;
}
.wrapper button:hover {
	transform: scale(1.1) translateY(-5px);
}
.wrapper button:disabled {
	background-color: #241450;
	border-color: #241450;
	cursor: not-allowed;
}
</style> -->

<!-- крипта -->

<template>
	<h1>CRYPTO</h1>
	<Input :changeAmount="changeAmount" :convert="convert" />
	<p v-if="error != ''">{{ error }}</p>
	<p v-if="result != ''" className="result-text" >{{ result }}</p>
	<div className="selectors">
		<Selector :setCrypto="setCryptoFirst" />
		<Selector :setCrypto="setCryptoSecond" />
	</div>
</template>

<script>
import Input from './components/Input.vue'
import Selector from './components/Selector.vue'
import CryptoConvert from 'crypto-convert'
const convert = new CryptoConvert()
export default {
	components: { Input, Selector },
	data() {
		return {
			amount: 0,
			cryptoFirst: '',
			cryptoSecond: '',
			error: '',
			result:0
		}
	},
	methods: {
		changeAmount(val) {
			this.amount = val
		},
		setCryptoFirst(val) {
			this.cryptoFirst = val
		},
		setCryptoSecond(val) {
			this.cryptoSecond = val
		}, 
		async convert() {
			if (this.amount <= 0) {
				this.error = 'ВВедите число больше за ноль';
				return;
		}	 else if (this.cryptoFirst == '' || this.cryptoSecond == '') {
				this.error = 'ВЫберите валюту'
				return;
		}	else if (this.cryptoFirst == this.cryptoSecond) {
				this.error = 'ВЫберите другую валюту';
				return;
		}
		this.error = ''

		convert.BTC.USD(1);


		await convert.ready();
		if(this.cryptoFirst == 'BTC' && this.cryptoSecond == 'ETH')
			this.result = convert.BTC.ETH(this.amount);
		else if(this.cryptoFirst == 'BTC' && this.cryptoSecond == 'USDT')
			this.result = convert.BTC.USDT(this.amount);
		else if(this.cryptoFirst == 'ETH' && this.cryptoSecond == 'BTC')
			this.result = convert.ETH.BTC(this.amount);
		else if(this.cryptoFirst == 'ETH' && this.cryptoSecond == 'USDT')
			this.result = convert.ETH.USDT(this.amount);
		else if(this.cryptoFirst == 'USDT' && this.cryptoSecond == 'BTC')
			this.result = convert.USDT.BTC(this.amount);
		else if(this.cryptoFirst == 'USDT' && this.cryptoSecond == 'ETH')
			this.result = convert.USDT.ETH(this.amount);
	},
} }
</script>

<style scooped>
.selectors {
	display: flex;
	justify-content: space-around;
	width: 700px;
	margin: 0 auto;
}
</style>
