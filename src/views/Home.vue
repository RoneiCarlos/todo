<template>
    <div class="container grid-xs py-2">
      <form @submit.prevent="addTodo(todo)">
        <div class="input-group">
          <input
            type="text"
            v-model="todo.description"
            class="form-input"
            placeholder="New Todo"
          />
          <button class="btn btn-primary input-group-btn">Add</button>
        </div>
      </form>
      <div class="todo-list">
        <Todo
          v-for="todo in todos"
          :key="todo.id"
          @done="doneTodo"
          @remove="removeTodo"
          :todo="todo"
        />
      </div>
    </div>
</template>

<script>
import Todo from "@/components/Todo";
export default {
  name: "App",
  components: { Todo },
  data() {
    return {
      todos: [],
      todo: {
        checked: false,
      },
    };
  },
  methods: {
    addTodo(todo) {
      todo.id = Date.now();
      this.todos.push(todo);
      this.todo = {
        checked: false,
      };
    },

    doneTodo(todo) {
      const index = this.todos.findIndex((item) => item.id === todo.id);
      if (index >= 0) {
        const checked = !this.todos[index].checked;
        this.$set(this.todos, index, { ...this.todos[index], checked });
      }
    },

    removeTodo(todo) {
      const index = this.todos.findIndex((item) => item.id === todo.id);
      if (index >= 0) {
        this.$delete(this.todos, index)
      }
    },
  },
};
</script>

<style scoped>
.todo-list {
  padding-top: 2rem;
}
</style>
