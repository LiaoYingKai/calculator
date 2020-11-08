<template>
  <div class="calculator">
    <CalculationBar :formula="formula" :number="displayNum"/>
      <div class="flex container">
        <div class="flex flex-wrap">
          <CalculationButton
            v-for="(number, index) in numbers"
            :key="index"
            :value="number"
            @onClick="handleClickNumber"
          >
            {{number}}
          </CalculationButton>
        </div>
        <div class="flex flex-column">
          <CalculationButton
            v-for="(operator, index) in operators"
            :key="index"
            :value="operator"
            type="operator"
            @onClick="handleClickOperator"
          >
            {{operator}}
          </CalculationButton>
        </div>
      </div>
      <div class="flex">
        <FeatureButton> AC </FeatureButton>
        <FeatureButton> ⌫ </FeatureButton>
        <FeatureButton type="two"> = </FeatureButton>
      </div>
    </div>
</template>

<script>
import { defineComponent, ref } from 'vue'
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
    const numbers = [7, 8, 9, 4,5,6,1,2,3,0,'00', '.'];
    const operators = ['÷','x','+','-'];
    const displayNum = ref('');
    const formula = ref([]);

    function handleClickNumber(number) {
      if (displayNum.value.includes('.') & number === '.') return 
      displayNum.value = displayNum.value + number
    }

    function handleClickOperator(operator) {
      const lastIndex = formula.value.length - 1
      const lastOperator = formula.value[lastIndex]
      if (operators.includes(lastOperator) && !displayNum.value) {
        formula.value = formula.value.map((item, index) => index === lastIndex ? operator : item)
        return
      }
      formula.value = [...formula.value, displayNum.value, operator]
      displayNum.value = ''
    }

    return {
      handleClickNumber,
      handleClickOperator,
      displayNum,
      formula,
      numbers,
      operators,
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
  padding: 8px 16px;
  box-sizing: border-box;
}
.container {
  > div {
    &:first-child {
      flex: 3;
    }
    &:last-child {
      flex: 1;
    }
  }
}

.flex {
  display: flex;
  justify-content: space-between;
  align-items: center;
}
.flex-column {
  flex-direction: column;
}
.flex-wrap {
  flex-wrap: wrap;
}
</style>
