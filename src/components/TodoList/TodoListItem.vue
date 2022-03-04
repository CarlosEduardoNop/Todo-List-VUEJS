<template>
  <li 
    class="todo-list-item"
    :class="{'todo-list-item-completed': checked}"
  >
    <div class="id">
      {{ id+1 }}
    </div>
    
    <div class="label">
      {{ label }}
    </div>

    <div class="created-date">
      {{ createdDate.toLocaleString() }}
    </div>

    <div>
      <input 
        type="checkbox"
        :checked="checked"
        @input="check"
      />
    </div>
    
    <div>
      <Button 
        label="Deletar"
        type="delete"
        :disabled="!checked"
        @click="removeItem"
      />
    </div>
  </li>
</template>

<script>
import Button from '../Button.vue'

export default {
  name: 'TodoListItem',
  components: {
    Button
  },
  props: {
    id: {
      type: Number,
    },
    label: {
      type: String,
      required: true
    },
    createdDate: {
      type: Date,
      required: true
    },
    checked: {
      type: Boolean,
      default: false
    }
  },
  methods: {
    check() {
      this.$emit('check', !this.checked)
    },
    removeItem() {
      this.$emit('delete')
    },
  }
}
</script>

<style lang="scss" scoped>
.todo-list-item {
  padding: 24px 20px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  border-radius: 5px;
  height: 72px;
  background: #F2F2F2;

  .label {
    width: 40%;
  }

  &.todo-list-item-completed {
    text-decoration: line-through;
    font-style: italic;
  }
}
</style>