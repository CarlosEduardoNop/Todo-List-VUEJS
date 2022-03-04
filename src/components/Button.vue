<template>
  <button 
    :class="[
      'button',
      `button-${type}`
    ]"
    @click="add"
    :disabled="disabled"
  >
    {{ label }}
  </button>
</template>

<script>
export default {
  name: 'Button',
  props: {
    label: {
      type: String,
      required: true
    },
    type: {
      type: String,
      default: 'add'
    },
    disabled: {
      type: Boolean,
      default: false
    }
  },
  methods: {
    add() {
      this.$emit('click')
    }
  }
}
</script>

<style lang="scss" scoped>
.button {
  cursor: pointer;
  border: none;
  padding: 5px 10px;
  border-radius: 5px;

  &:active {
    opacity: .8;
  }

  &.button-add {
    background: #3FB883;
    color: #ffffff;
  }
  
  &.button-delete {
    background: #dc3545;
    color: #ffffff;
  }

  &:disabled {
    background: #b8b8b8;
    cursor: no-drop;
  }
}
</style>