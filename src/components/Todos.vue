<template>
	<div>
		<!-- v-for sanga v-bind always needed;   emit: lai catch garnu parxa paxi; its the catching the returned value -->
		<div v-bind:key = "todo.id" v-for="todo in todos">
			<TodoItem v-bind:todo = "todo" v-on:del-todo = "$emit('del-td', todo)"/>
		</div>
	</div>
</template>

<script>
import TodoItem from './Todoitem'
export default{
	name:"Todos",
	components:{
		TodoItem
	},
	// need to define props before using the object 
	props: ["todos"]
}
</script>
<style scoped>
	
</style>