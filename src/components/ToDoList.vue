<template>
  <div>
    <h1>Lista zadań</h1>
    <div>
      <input
        class="todoInput"
        v-model="newTodo"
        placeholder="Dodaj nowe zadanie"
      />
      <button class="todoButton" @click="addTodo">Dodaj</button>
    </div>
    <ul>
      <li class="list" v-for="(todo, index) in todos" :key="index">
        <TodoItem
          :title="todo.title"
          :completed="todo.completed"
          @toggle-complete="toggleComplete(index)"
          @remove="removeTodo(index)"
        />
      </li>
    </ul>
  </div>
</template>

<script>
import TodoItem from "./ToDoItem.vue";

export default {
  name: "TodoList",
  components: {
    TodoItem,
  },
  data() {
    return {
      newTodo: "",
      todos: [],
    };
  },
  methods: {
    addTodo() {
      if (this.newTodo.trim() !== "") {
        this.todos.push({ title: this.newTodo, completed: false });
        this.newTodo = "";
      }
    },
    toggleComplete(index) {
      this.todos[index].completed = !this.todos[index].completed;
    },
    removeTodo(index) {
      this.todos.splice(index, 1);
    },
  },
};
</script>

<style scoped>
input {
  margin-bottom: 10px;
}
</style>
