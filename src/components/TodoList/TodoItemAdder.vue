<template>
  <div class="todo-item-adder">
    <input
      class="adder-input"
      type="text" 
      v-model="input" 
    />

    <Button 
      class="adder-button"
      label="adicionar" 
      @click="add"
    />
  </div>
</template>

<script>
import Button from '../Button.vue'
export default {
  name: 'TodoItemAdder',
  components: {
    Button
  },
  data() {
    return {
      input: ''
    }
  },
  methods: {
    add() {
      if (this.input) {
        this.$emit('add', this.input)
        this.input = ''
      }
    }
  }
}
</script>

<style lang="scss" scoped>
.todo-item-adder {
  height: 25px;
  display: flex;

  .adder-input {
    width: 40%;
    border-radius: 5px;
    border-color: transparent;
    height: 100%;
    margin-right: 20px;
    background: #F2F2F2;
    padding: 0 5px;
  }

  .adder-button {
    height: 100%;
  }
}
</style>