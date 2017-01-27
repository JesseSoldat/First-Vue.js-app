<template>
	<div class="test">
		<input type="text" name="" v-model="title"><br/>
		<!-- <span v-html="title">{{title}}</span> -->
		<h2>{{title}}</h2>
		<div v-if="showName">
			<p>{{user.fName}}</p>
			<p>{{user.lName}}</p>
		</div>
		<div v-else="showName">
			<p>No User Logged Available</p>
		</div>
		 
		<p>{{user.age}}</p>
		<p v-text="user.hobby"></p>

		<ul>
			<li v-for="item in items">
				{{item.title}}
			</li>
		</ul>
		<button v-on:click="greet('Hello from Vue!')">Say Greeting</button>
		<br>
		<input v-on:keyup="pressKey" type="text" v-on:keyup.enter="enterPressed">
		<hr>
		<label>First Name
		<input type="text" v-model="user.fName">
		</label>
		<br>
		<label>Last Name 
		<input type="text" v-model="user.lName">
		</label>
		<br>
		<h4>{{fullName}}</h4>
		<h4>{{msg}}</h4>
		
	</div>
	
</template>

<script>
	export default {
		name: 'test',
		props: {
			msg: {
				type: String,
				default: 'No Message'
			}
		},
		data () {
			return {
				title: "Hello World",
				user: {
					fName: 'Jesse',
					lName: 'Soldat',
					age: 36,
					hobby: 'Programming'
				},
				showName: true,
				items: [
					{title: 'Learn React'},
					{title: 'Learn Angular 2'},
					{title: 'Learn Graph QL'},
					{title: 'Learn Node'},
					{title: 'Learn Vue'}
				]
			}
		},
		methods: {
			greet: function(hello){
				alert(hello);
			},
			pressKey: function(e){
				console.log(e.target.value);
			},
			enterPressed: function(){
				console.log('You pressed the enter key!')
			}
		},
		computed: {
			fullName: function(){
				return this.user.fName+' '+this.user.lName
			}
		}
	}
</script>

<style scoped>
	
</style> 