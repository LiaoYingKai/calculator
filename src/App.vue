<template>
  <div class="calculator">
    <CalculationBar :formula="['3000', '+', '1000']" :number="4000"/>
    <CalculationButton :value="1" @onClick="handleClickNumber"> 1 </CalculationButton>
    <CalculationButton value="/" @onClick="handleClickNumber" type="operator"> / </CalculationButton>
    <FeatureButton> AC </FeatureButton>
    <FeatureButton type="two"> = </FeatureButton>

  </div>
</template>

<script>
import { defineComponent  } from 'vue'
import CalculationButton from '@/components/CalculationButton.vue' 
import CalculationBar from '@/components/CalculationBar.vue' 
import FeatureButton from '@/components/FeatureButton.vue' 

export default defineComponent({
  name: 'App',
  components: {
    CalculationButton,
    CalculationBar,
    FeatureButton
  },
  setup() {
    function handleClickNumber(number) {
      console.log(number)
    }
    return {
      handleClickNumber
    }
  }
})
</script>

<style lang="scss">
html, body {
  margin: 0;
  padding: 0;
  background-color: #E8E8E8;
  width: 100%;
  height: 100%;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  width: 100%;
  height: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
}

.calculator {
  width: 350px;
  height: 525px;
  background-color: #062145;
  box-shadow: 0px 20px 40px #00000066;
  border-radius: 20px;
}
</style>
