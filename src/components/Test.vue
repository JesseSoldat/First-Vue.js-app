<template>
	<div class="test">
		<span v-html="title">{{title}}</span>
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
	</div>
	
</template>

<script>
	export default {
		name: 'test',
		data () {
			return {
				title: "<h2>Hello World</h2>",
				user: {
					fName: 'Jesse',
					lName: 'Soldat',
					age: 36,
					hobby: 'Programming'
				},
				showName: false,
				items: [
					{title: 'Learn React'},
					{title: 'Learn Angular 2'},
					{title: 'Learn Graph QL'},
					{title: 'Learn Node'},
					{title: 'Learn Vue'}
				]
			}
		}
	}
</script>

<style scoped>
	
</style>