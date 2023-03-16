<script setup>
defineProps({
    question : String,
    answers : Array
})


</script>

<template>
    <div class="qst-header max-h-20 text-center text-xl">
        <p>{{ question }}</p>
    </div>
    <div class="answers-container grid grid-cols-2 gap-8">
        <button 
         v-for="(ans,index) in answers"
         class=" relative bg-transparent hover:bg-yellow-200 text-yellow-200 font-semibold hover:text-black p-6 border border-yellow-200 hover:border-transparent rounded relative">
            <div class="bg-white font-bold text-black rounded-full border-white border-2  w-8 h-8 max-w-[50%] absolute -top-3 -left-3 grid place-items-center ">{{index+1}}</div>
            {{ ans }}
        </button>
        
    </div>
    
</template>