<template>
  <!-- here is the skeleton design of the calculator -->
  <div class="m-auto mt-10 rounded-lg w-[300px] h-[480px] bg-black">
    
    <!-- here goes the form and inputs -->
  <div class="flex flex-col">

   <!-- display -->
   
    <input class="bg-gray-900 border-transparent rounded-lg pb-2 pt-2 text-white text-2xl text-right flex items-center cursor-text" v-model="operationField">
    <p class="bg-gray-900 pt-5 text-white text-2xl text-right">{{result}}</p>
    <p>{{percentage}}</p>

  
   <hr class="">

   <!-- here go the buttons -->
   <div class="bg-black"> 
    <!-- here go the first row buttons -->
    <div class="flex justify-around items-center mt-2">
      <button class="bg-black text-rose-600 text-3xl" @click="clearField">C</button>
      <button class="bg-black text-green-600 text-3xl" @click="confirmNum('%')">%</button>
      <button class="bg-black text-green-600 text-5xl" @click="confirmNum('/')">&divide</button>
      <button class="bg-black text-green-600 text-3xl" @click="backspace"><svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-10 mt-2 h-6 font-bold">
        <path stroke-linecap="round" stroke-linejoin="round" d="M12 9.75L14.25 12m0 0l2.25 2.25M14.25 12l2.25-2.25M14.25 12L12 14.25m-2.58 4.92l-6.375-6.375a1.125 1.125 0 010-1.59L9.42 4.83c.211-.211.498-.33.796-.33H19.5a2.25 2.25 0 012.25 2.25v10.5a2.25 2.25 0 01-2.25 2.25h-9.284c-.298 0-.585-.119-.796-.33z" />
      </svg>
      </button>
    </div>
     
    <!-- here go the second row buttons -->
    <div class="flex justify-around items-center mt-6">
      <button class="bg-black text-white text-3xl" @click="confirmNum(7)">7</button>
      <button class="bg-black text-white text-3xl" @click="confirmNum(8)">8</button>
      <button class="bg-black text-white text-3xl" @click="confirmNum(9)">9</button>
      <button class="bg-black text-green-600 text-4xl" @click="confirmNum('*')">
        &#215;
      </button>
    </div>

    <!-- here go the third row -->
    <div class="flex justify-around items-center mt-6">
      <button class="bg-black text-white text-3xl" @click="confirmNum(4)">4</button>
      <button class="bg-black text-white text-3xl" @click="confirmNum(5)">5</button>
      <button class="bg-black text-white text-3xl" @click="confirmNum(6)">6</button>
      <button class="bg-black text-green-600 text-4xl" @click="confirmNum('-')">
        &minus;
      </button>
    </div>

    <!-- here go the fourth row -->
    <div class="flex justify-around items-center mt-6">
      <button class="bg-black text-white text-3xl" @click="confirmNum(1)">1</button>
      <button class="bg-black text-white text-3xl" @click="confirmNum(2)">2</button>
      <button class="bg-black text-white text-3xl" @click="confirmNum(3)">3</button>
      <button class="bg-black text-green-600 text-4xl" @click="confirmNum('+')">
        &plus;
      </button>
    </div>

    <!-- here go the fourth row -->
    <div class="flex justify-around items-center mt-6">
      <button class="bg-black text-white text-sm font-bold" @click="">+/-</button>
      <button class="bg-black text-white text-3xl mr-2" @click="confirmNum(0)">0</button>
      <button class="bg-black text-white text-3xl" @click="confirmNum('.')">.</button>
      <button class="bg-black rounded-full text-green-600 text-4xl" @click="computeResult">
        &equals;
      </button>
    </div>

    <!-- here goes the footer for credit  -->
   <div class="bg-black pb-2 rounded-full mt-6 mx-3 border-t-2 border-rose-500">
    <p class="text-white text-sm italic ml-5">mock-up samsung note 10+ calculator crafted by <span class="text-rose-600 font-bold"><a href="wa.link/15nbq7">jabir khalif</a> </span></p>

   </div>
   </div>

  </div>


  </div>
</template>

<script setup>
  // imports
  import { ref, computed} from 'vue'

  const operationField = ref('');
  
  const result = ref(0)
 
  
   // methods

  // getting the clicked numbers on the operationField
  const confirmNum = (num) => {
   operationField.value += num;    
  }
  // clear the operationField on click of C
   const clearField = () => {
    operationField.value = ''
    result.value = 0;
   }

  //  backspace by one character
  const backspace = () => {
   operationField.value = operationField.value.slice(0, operationField.value.length - 1)
   }
// compute result
const computeResult  =  () => {
  result.value =  eval(operationField.value)  
}




// computed
const percentage =  computed( () => {
  if (operationField.value.endsWith('%')) {
     result.value = parseInt(operationField.value)/100
  }
})

 
  
   
</script>

