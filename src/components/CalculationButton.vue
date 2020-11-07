<template>
  <button @click="handleClick" :class="`${type}-button`">
    <slot/>
  </button>
</template>
<script>
import { defineComponent }from 'vue'

export default defineComponent({
  props: {
    value: {
      required: true,
      type: [String, Number] ,
    },
    type: {
      validator: function (value) {
        return ['operator', 'default'].includes(value)
      },
      default: 'default'
    }
  },
  setup(props, { emit }) {
    function handleClick() {
      const { value } = props
      emit('on-click', value)
    }

    return {
      handleClick
    }
  }
})
</script>
<style lang="scss" scoped>
button {
  color: #fff;
  font-size: 24px;
  box-shadow: 0px 20px 40px #00000066;
  border-radius: 20px;
  opacity: 1;
  border: none;
  cursor: pointer;
  width: 72px;
  height: 64px;
  padding: 0;
  margin-bottom: 16px;
}
.operator-button {
  background-color: #041936;
}
.default-button {
  background-color: transparent;
  box-shadow: 0px 0px 0px;
}
</style>