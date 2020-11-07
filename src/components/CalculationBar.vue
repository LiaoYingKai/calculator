<template>
  <div class="calculation-bar">
    <div class="calculation-bar__formula"> {{ formula.join(' ') }} </div>
    <div class="calculation-bar__number"> {{format(number) || 0}} </div>
  </div>
</template>
<script>
import { defineComponent } from 'vue'

export default defineComponent({
  props: {
    formula: {
      type: Array,
      default: () => [],
    },
    number: {
      type: [ Number, String ],
      default: '',
    }
  },
  setup(props) {
    function format() {
      // TODO 貨幣格式
      return props.number
    }

    const formatNumber = format()

    return {
      formatNumber,
      format
    }
  }
})
</script>
<style lang="scss" scoped>
.calculation-bar {
  width: 100%;
  box-sizing: border-box;
  padding: 8px 16px;
  height: 109px;
  text-align: right;
  white-space:nowrap;

  &__formula {
    height: 22px;
    widows: 100%;
    color: #00C4FF;
    overflow-x: scroll;
  }
  &__number {
    font-size:56px ;
    color: #FFFFFF;
    overflow-x: scroll;
  }
}

</style>