<template>
	<header class="header">
	<h1>TODOLISTS</h1>
	<div id='nav'>
        <router-link to="/">Home</router-link><span>|</span>
        <router-link to="/about"> About </router-link>
    </div>
    <router-view />	
	</header>
</template>

<script>
export default{
	name: 'Header'
}
</script>

<style scoped>
	
</style>