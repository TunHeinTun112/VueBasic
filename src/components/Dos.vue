<template>
  <div>
    <h1 class="text-secondary text-center">Hello Vue</h1>
    <div class="container">
      <div class="row">
        <AddTodo/>
      </div>
      <div class="row">
        <div class="col-md-4 my-4" v-for="todo in myTodos" :key="todo.id">
          <b-card bg-variant="dark" text-variant="white" class="text-center">
            <b-card-text>{{ todo.title }}</b-card-text>
          </b-card>
        </div>
      </div>
    </div>
  </div>

</template>

<script>
import { mapActions, mapGetters } from 'vuex';
import AddTodo from './AddTodo.vue';

export default {
    computed: {
        myLocalComputedProp() {
            return "smth";
        },
        ...mapGetters([
            "myTodos"
        ])
    },
    methods: mapActions(["getTodos"]),
    mounted() {
        this.getTodos();
    },
    components: { AddTodo },
}
</script>

<style>

</style>