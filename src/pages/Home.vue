<template>
  <div class="home">
    <TodoList />
  </div>
</template>

<script>
import TodoList from '../components/TodoList.vue'

export default {
  name: 'Home',
  components: {
    TodoList,
  },
  data() {
    return {
      list: []
    }
  }
}
</script>

<style lang="scss" scoped>
.home {
  margin-top: 36px;
}
</style>