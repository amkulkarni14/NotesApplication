<script setup>
import { defineProps } from 'vue';
const props = defineProps({
    note:Object,  
    
    
});
const deleteNote=()=>{
    props.note=''; 
}
</script>

<template>
     <div class="bg-white rounded-xl shadow-md relative">
            <div class="p-4">
              <div class="mb-6">
                <div class="text-2xl font-bold mb-4"> {{ note?.noteHeading }}</div>
               
              </div>

              <div class="mb-5">
                
                {{ note?.note }}
              </div>

            

              <div class="border border-gray-100 mb-5"></div>

              <div class="flex flex-col lg:flex-row justify-between mb-4">
                <div class="text-sky-700 mb-3">
                  <i class="pi pi-date"></i>
                 {{ note?.date }}
                </div>
                <button @click="deleteNote()"
                  class="h-[36px] bg-red-500 hover:bg-red-600 text-white px-4 py-2 rounded-lg text-center text-sm"
                >
                  Delete
                </button>
              </div>
            </div>
          </div>
</template>