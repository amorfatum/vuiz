<template>
<div>
    <p>Highest referencable number: {{ highestNumber }}</p>
</div>
</template>
  
<script>
import { reactive } from 'vue'
import questionsJson from '@/assets/questions.json'

export function findHighestNumber() {
  let highestNumber = 0
  for (const questionKey in questionsJson.questions) {
    const questionNumber = parseInt(questionKey)
    if (questionNumber > highestNumber) {
      highestNumber = questionNumber 
    }
  }
  return highestNumber
}

export default {
  setup() {
    const state = reactive({
      highestNumber: null
    })

    state.highestNumber = findHighestNumber()

    return {
      highestNumber: state.highestNumber,
      findHighestNumber
    }
  }
}
</script>