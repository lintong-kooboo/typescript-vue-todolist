<template>
  <div id="index">
      <h1>{{ message }}</h1>
      <g-todolist></g-todolist>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
import Component from 'vue-class-component'
import TodoList from './TodoList.vue'
@Component({
  components: {
    'g-todolist': TodoList
  }
})
export default class Index extends Vue {
  message: string = 'TodoList'
  created () {
    console.log('created')
  }
  mounted () {
    console.log('mounted')
  }
  getMessage () {
    return this.message
  }
}
</script>

<style>
  h1 {
    font-size: 48px;
    color: #0dbc79
  }
</style>
