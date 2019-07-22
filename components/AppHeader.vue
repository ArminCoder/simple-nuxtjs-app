<template>
	<header class="header">
		<h1 class="title">Dad Jokes</h1>
		<ul>
			<li>
				<nuxt-link to='/'>Home</nuxt-link>	
			</li>
			<li>
				<nuxt-link to='/jokes'>Jokes</nuxt-link>	
			</li>

			<li>
				<nuxt-link to='/about'>About</nuxt-link>	
			</li>
		</ul>
	</header>
</template>

<script>

export default {
  	name: 'AppHeader',
};
</script>

<style scoped>
	.header {
		display: flex;
		justify-content: space-between;
		align-items: center;
		margin-bottom: 1rem;
		padding-bottom: 1rem;
		border-bottom: 1px dotted #ccc;
	}
	.header .title {
		font-size: 3rem;
		color: #526488
	}
	.header ul {
		display: flex;
		list-style: none;
	}
	.header ul li {
		margin: 0 10px;
	}
	.header a {
		display: inline-block;
		background: #333;
		padding: 5px;
		border-radius: 5px;
	}
</style>