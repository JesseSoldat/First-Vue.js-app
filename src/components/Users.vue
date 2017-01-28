<template>
	<div class="users">
		<h2>Users</h2>
		<form v-on:submit="addUser">
			<input type="text" v-model="newUser.name" placeholder="Enter name">
			<input type="text" v-model="newUser.email" placeholder="Enter email">
			<button type="submit">Submit</button>
		</form>
		
		<ul>
			<li v-for="user in users">
				<input type="checkbox" class="toggle" v-model="user.contacted">
				<span :class="{contacted: user.contacted}">
					{{user.name}}: {{user.email}} 
				</span>
				<button v-on:click="deleteUser(user)">X</button>
			</li>
		</ul>
	</div>
</template>

<script>
	export default {
		name: 'users',
		data () {
			return {
				newUser: {},
				users: [
					{
						name: 'John Doe',
						email: 'jdoe@gmail.com',
						contacted: false
					},
					{
						name: 'Jane Smith',
						email: 'jsmith@gmail.com',
						contacted: true
					},
					{
						name: 'Mike Miller',
						email: 'mmiller@gmail.com',
						contacted: false
					},
					{
						name: 'Betty Davis',
						email: 'bdavis@gmail.com',
						contacted: true
					},
					{
						name: 'Arron Frost',
						email: 'afrost@gmail.com',
						contacted: false
					},
					{
						name: 'Sam Nugget',
						email: 'snuggete@gmail.com',
						contacted: false
					},
					{
						name: 'Kim Courter',
						email: 'kcourter@gmail.com',
						contacted: true
					}
				]

			}
		},
		methods: {
			addUser: function(e){
				e.preventDefault()
				this.users.push({
					name: this.newUser.name,
					email: this.newUser.email,
					contacted: false

				});
			},
			deleteUser: function(user){
				this.users.splice(this.users.indexOf(user), 1);
			}
		},
		created: function(){
			this.$http.get('https://jsonplaceholder.typicode.com/users')
				.then(function(res){
					// console.log(res.data)
					var tempUsers = res.data;
					for(var i = 1; i < res.data.length; i++){
						tempUsers[i]
						tempUsers[i].contacted = false;
						this.users.push(res.data[i])
					}
					

				})
		}
	}
</script>

<style scoped>
	.contacted {
		text-decoration: line-through;
	}
</style>