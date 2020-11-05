<template>
  <button @click="handleClick" :class="`${type}-column-button`">
    <slot/>
  </button>
</template>
<script>
import { defineComponent }from 'vue'

export default defineComponent({
  props: {
    type: {
      validator: function (value) {
        return ['one', 'two'].includes(value)
      },
      default: 'one'
    }
  },
  setup(props, { emit }) {
    function handleClick() {
      emit('on-click')
    }

    return {
      handleClick
    }
  }
})
</script>
<style lang="scss" scoped>
button {
  font-size: 24px;
  box-shadow: 0px 20px 40px #00000066;
  border-radius: 20px;
  border: none;
  cursor: pointer;
  width: 72px;
  height: 64px;
  padding: 0;
}
.one-column-button {
  background-color: #041936;
  color: #00C4FF;
}
.two-column-button {
  background: transparent linear-gradient(90deg, #00C4FF 0%, #6C00FF 100%) 0% 0% no-repeat padding-box;
  color: #fff;
  text-align: right;
  width: 144px;
  font-size: 16px;
  padding: 18px 30px;
  box-sizing: border-box;

}
</style>