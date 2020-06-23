<template>
	<!--  -->
	<div class="todo-item" v-bind:class="{'is-complete':todo.completed}">
		<p>
			<input type="checkbox" v-on:change="markComplete">
			{{todo.title}}
			<!-- emit: to send the data back to where it came from -->
			<button @click="$emit('del-todo', todo.id)" class="del">x</button>
		</p>
	</div>
</template>

<script>
//export default mostly used for initialization	
export default{
	name: 'Todoitem',
	props:["todo"],
	methods:{
		markComplete(){
			this.todo.completed = !this.todo.completed;
		}
	}
}	
</script>

<style scoped>
	.todo-item{
		background: #f4f4f4;
		padding: 10 px;
		border-bottom: 10px solid black;
	}
	.is-complete{
		text-decoration: line-through;
	}
	.del{
		color: red;
	}
</style>