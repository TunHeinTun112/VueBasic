<template>
  <div>
    <h1 class="text-secondary text-center">Hello Vue</h1>
    <div class="container">
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
import { mapGetters } from 'vuex';
export default {
  computed: {
    myLocalComputedProp() {
      return "smth";
    },
    ...mapGetters([
      "myTodos"
    ])
  },
  mounted() {
    console.log(this.myTodos,this.myLocalComputedProp);
  }
}
</script>

<style>

</style>