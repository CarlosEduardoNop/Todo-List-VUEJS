<template>
  <div class="todo-list">
    <div class="todo-list-container">
      <ul class="list">
        <TodoListItem 
          v-for="(item, index) in list" 
          :key="index"
          :id="index"
          v-bind="item"
          @check="checkItem(index, $event)"
          @delete="deleteItem(index)"
        />
      </ul>

      <div class="control">
        <TodoItemAdder @add="add" />
      </div>
    </div>
  </div>
</template>

<script>
import TodoListItem from "./TodoList/TodoListItem.vue";
import TodoItemAdder from "./TodoList/TodoItemAdder.vue";

export default {
  name: 'TodoList',
  components: {
    TodoListItem,
    TodoItemAdder
  },
  data() {
    return {
      list: [
        { label: 'item-1', createdDate: new Date(), checked: true },
        { label: 'item-2', createdDate: new Date(), checked: false }
      ]
    }
  },
  methods: {
    checkItem(index, checked) {
      this.list[index].checked = checked
    },
    add(item) {
      this.list.push({
        label: item,
        createdDate: new Date(),
        checked: false
      })
    },
    deleteItem(index) {
      this.list.splice(index, 1)
    }
  }
}
</script>

<style lang="scss" scoped>
.todo-list {
  max-width: 1128px;
  margin: 0 auto;

  .todo-list-container {
    padding: 69px 96px;
    box-shadow: 1px 1px 7px -1px rgb(0 0 0 / 25%);
    border-radius: 8px;

    .list {
      li {
        margin-bottom: 14px;
      }
    }
  
    .control {
      margin-top: 28px;
    }
  }
}
</style>