<template>
	<div>
		<SearchJokes @search-joke='searchJoke'></SearchJokes>
		<Joke v-for='joke in jokes' :key='joke.id' :joke='joke.joke' :id='joke.id' ></Joke>		
	</div>
</template>

<script>

import Joke from '../../components/Joke'; 
import axios from 'axios';
import SearchJokes from '../../components/SearchJokes';

export default {
	components: {
		Joke,
		SearchJokes
	},
	data() {
		return {
			jokes: []
		}
	},
	head() {
	  return {
	     title: 'Dad Jokes',
	     meta: [
	       { 
	          hid: 'description',
	          name: 'description',
	          content: 'Best place for corny dad jokes'
	        }  
	     ]
	  }
	},
	async created() {
		const config = {
			headers: {
				'Accept': 'application/json'
			}
		}
		try {
			const res = await axios.get('https://icanhazdadjoke.com/search', config);
			this.jokes = res.data.results;
		}	
		catch (err) {
			console.log(err);
		}
	},
	methods: {
		searchJoke(text) {
			const config = {
				headers: {
					'Accept' : 'application/json'
				}
			}
			axios.get(`https://icanhazdadjoke.com/search?term=${text}`, config).then(res => {
				this.jokes = res.data.results;
			})
		}
	}
};
</script>

<style lang="css" scoped>
</style>