<template>
  <div id="app">
    <app-todo/>
  </div>
</template>

<script>
import todo from '@/components/todo.vue'
export default {
  components:{
    'app-todo' : todo
}
}
</script>

<style>

</style>
