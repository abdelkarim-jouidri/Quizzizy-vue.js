<script setup>
import Question from './components/Question.vue';
import {ref , onBeforeMount, computed} from 'vue';
let questions = ref([])
let currentQuestion = ref(1)

onBeforeMount(()=>{
  console.log('from onbeforemount')
  fetch('http://localhost:3000/data').then(res=>res.json()).then(data=>{
    questions.value = data    
  })
})


let singleQuestion = computed(()=> {
  let [result] = questions.value.filter(qst=>qst.id===currentQuestion.value)
  return result
})

</script>

<template>
  <div class="bg-white">
  <div class="mx-auto max-w-7xl py-24 sm:px-6 sm:py-32 lg:px-8">
    <div class="relative isolate overflow-hidden bg-gray-900 px-6 pt-16 shadow-2xl sm:rounded sm:px-16 md:pt-24 lg:flex lg:gap-x-20 lg:px-24 lg:pt-0 flex justify-center">
      <div class="mx-auto text-center lg:mx-0 lg:flex-auto text-white lg:py-32 lg:text-left grid col-1 gap-8">
          <Question 
            :question="singleQuestion.question"
            :answers="singleQuestion.answers"
            >
          </Question>
      </div>
      
    </div>
  </div>
</div>
</template>
<style scoped>
.box-container{
  width: 100%;
}


</style>