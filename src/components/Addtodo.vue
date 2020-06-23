<template>
	<div>
		<form @submit="addtodo">
			<!-- v-model:to add data -->
			<input type="text" v-model="title" name="title" placeholder="Add todo....">
			<input type="submit" name="Submit" class="btn">
		</form>
	</div>
</template>

<script>
	//import { uuid } from 'vue-uuid';
	export default{
		name:'Addtodo',
		data(){
			return{
				title:''
			}
		},
		methods:{
			// newTodo: new object constructed ; uuid: automatic id generator
			addtodo(e){
				e.preventDefault();
				const newTodo ={

					//id : uuid.v4(),
					title: this.title,
					completed: false
				}
				// send to parent by emitting an event
				this.$emit('add-todo', newTodo);
				this.title = '';
			}
		}
	}	
</script>

<style scoped>
	form{
		display: flex;
	}

	input[type="text"]{
		flex: 10;
		padding: 5px;
	}

</style>