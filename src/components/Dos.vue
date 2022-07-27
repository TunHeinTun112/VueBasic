<template>
  <div>
    <h1 class="text-secondary text-center">Hello Vue</h1>
    <div class="container">
      <div class="row">
        <AddTodo/>
        <FilterTodos/>
      </div>
      <div class="row">
        <div class="col-md-4 my-4" v-for="todo in myTodos" :key="todo.id">
          <b-card @dblclick="toggleCompleted(todo)" :bg-variant="dynamicBackground(todo)" text-variant="white" class="text-center">
            <b-card-text class="d-flex justify-content-between">
              <span>{{ todo.title }}</span>
              <span @click="deleteTodo(todo.id)"><b-icon icon="trash-fill" variant="danger"></b-icon></span>
            </b-card-text>
          </b-card>
        </div>
      </div>
    </div>
  </div>

</template>

<script>
import { mapActions, mapGetters } from 'vuex';
import AddTodo from './AddTodo.vue';
import FilterTodos from './FilterTodos.vue';

export default {
    computed: {
        myLocalComputedProp() {
            return "smth";
        },
        ...mapGetters([
            "myTodos"
        ])
    },
  methods: {
    toggleCompleted(todo) {
      todo.completed = !todo.completed;
      this.updateTodo(todo);
    },
    dynamicBackground(todo) {
      return todo.completed ? 'primary' : 'dark';
    },
    ...mapActions(["getTodos", "deleteTodo","updateTodo"]),
  },
    mounted() {
        this.getTodos();
    },
    components: { AddTodo, FilterTodos },
}
</script>

<style>

</style>