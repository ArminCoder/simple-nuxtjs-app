<template>
	<div>
		<nuxt-link to='/jokes'>Back to jokes</nuxt-link>
		<br>
		{{ joke }}
		<hr>
		<h6>Joke Id: {{ $route.params.id }}</h6>
	</div>
</template>

<script>
import axios from 'axios';

export default {
	data() {
		return {
			joke: ''
		}
	},
	created() {
		console.log('ROUTE ID', this.$route.params.id);
		const config = {
			headers: {
				'Accept': 'application/json'
			}
		}
		axios.get(`https://icanhazdadjoke.com/j/${this.$route.params.id}`, config).then(res => {
			console.log(res);
			this.joke = res.data.joke;
		})
	},
	head() {
		return {
			title: this.joke,
			meta: [ 
				{
				name: 'description',
				content: 'Best corny dad jokes',
				hid: 'description',
				}
			]
		}
	}
};
</script>

<style scoped>
</style>