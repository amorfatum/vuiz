<template>
    <div class="questionCard">
        <p id="question">{{ question["question"] }}</p>
        <div class="answers">
            <div class="col1 row1">
                <label for="questionA">{{ question["answers"][0]["option"] }}: </label>
                <button id="questionA" class="questionButton" value="A" @click="checkAnswer($event)">{{ question["answers"][0]["text"] }}</button>
            </div>
            <div class="col2 row1">
                <label for="questionB">{{ question["answers"][1]["option"] }}: </label>
                <button id="questionB" class="questionButton" value="B" @click="checkAnswer($event)">{{ question["answers"][1]["text"] }}</button>
            </div>
            <div class="col1 row2">
                <label for="questionC">{{ question["answers"][2]["option"] }}: </label>
                <button id="questionC" class="questionButton" value="C" @click="checkAnswer($event)">{{ question["answers"][2]["text"] }}</button>
            </div>
            <div class="col2 row2">
                <label for="questionD">{{ question["answers"][3]["option"] }}: </label>
                <button id="questionD" class="questionButton" value="D" @click="checkAnswer($event)">{{ question["answers"][3]["text"] }}</button>
            </div>
        </div>
    </div>
  </template>
  
  <script>
  import { computed, ref, onMounted, onUnmounted } from 'vue'
  import questionsJson from '@/assets/questions.json'
  import {findHighestNumber} from '@/components/QuestionsGetHighestNumber.vue'
  import Counter from '@/components/Counter.vue'
  import { incCount } from '@/components/Counter.vue'
  
  export default {
    setup() {
      const count = ref(0)

      const selectedAnswer = ref(null)
      const questionNumber = ref(null)
  
      const highestNumber = ref(null)

      highestNumber.value = findHighestNumber()

      const question = computed(() => {
        if (questionNumber.value === null) {
          questionNumber.value = Math.floor(Math.random() * highestNumber.value) + 1
        }
        return questionsJson.questions[questionNumber.value]
      })

      function checkAnswer(event) {
        let selectedAnswer = event.target.value
        let answer = question.value.answers.filter(a => a.option === selectedAnswer)
  
        if (selectedAnswer === null) {
          alert('Please select an answer.')
          return
        }
  
        if (answer[0].correct) {
          //alert('Correct!')
          incCount()
          console.log(count)
          console.log('correct')
        } else {
          console.log('wrong')
          console.log(answer[0].correct)
          //alert('Incorrect.')
        }
  
        questionNumber.value = Math.floor(Math.random() * highestNumber.value) + 1
        selectedAnswer = null
      }
  
      return {
        question,
        selectedAnswer,
        checkAnswer,
        count,
        incCount
      }
    },
    methods:{
        resolveQuestion(event){
          console.log(event);
        }
      }
  }
  </script>

<style>
    .questionCard{
      top: 25%;
      left: 25%;
      color: white;
      font-family: Cambria, Cochin, Georgia, Times, 'Times New Roman', serif;
      font-size: large;
    }

    .answers{
      display: grid;
      grid-auto-flow: column;
      grid-row-gap: 20px;
    }

    .questionButton{
      font-size: large;
    }

    .col1{
        grid-column-start: 1;
        grid-column-start: 1;
    }

    .col2{
        grid-column-start: 2;
        grid-column-start: 2;
    }

    .row1{
        grid-row-start: 1;
        grid-row-end: 1;
    }

    .row2{
        grid-row-start: 2;
        grid-row-end: 2;
    }
</style>