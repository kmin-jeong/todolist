<template>
    <div class="todo-container">
      
        <h2>Todo List</h2>
        <form class="input-todo-form">
            다크모드:<input type="checkbox">
            <input type="text" class="InputTodo" placeholder="입력하기"/>
            <button type="submit" @click="addTodo">Add</button>
        </form>
        <ul>
        <li class="todo" v-for="(todo,index) in todos" :key="index" :class="{completed: compeleteTodo, editing: todo == deleteTodo}">
			<div class="view">
				<input class="toggle" type="checkbox" v-model="compeleteTodo">
				<label @dblclick="deleteTodo(todo)">{{todo.title}}</label>
				<button class="destroy" @click="deleteTodo(todo)"></button>
			</div>
		</li>
        </ul>  
    </div>
</template>

<script>
  export default {
    name: 'App',
    methods: {
      addTodo(e) {
        e.preventDefault();
        const todo = {
          text: document.querySelector('input.InputTodo').value,
          completed: false
        };
        this.todos.push(todo);
      },
      compeleteTodo(index) {
        console.log(this.todos[index].completed);
        this.todos[index].completed = !this.todos[index].completed;
      },
      deleteTodo(index) {
        this.todos.splice(index, 1);
      }
    },
    data() {
      return {
        todos: [
          {
            text: '',
            completed: true
          }
        ]
      }
    }
  }
</script>

<style>
   
</style>