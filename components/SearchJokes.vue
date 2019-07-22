<template>
	<form @submit.prevent='onSubmit'>
		<input type="text" v-model='text'>
		<button class="btn">Submit</button>
	</form>
</template>

<script>
export default {
  name: 'SearchJokes',
  data () {
    return {
    	text : ''
    }
  },
  methods: {
  	onSubmit() {
  		this.$emit('search-joke' , this.text);
  		this.text = '';
  	}
  }
};
</script>

<style lang="css" scoped>
	input {
		padding: 5px;
		border-radius: 5px;
		border-color: #ccc;
	}
	.btn {
		border: 1px solid #ccc;
		border-radius: 5px;
		padding: 5px 8px;
	}
</style>