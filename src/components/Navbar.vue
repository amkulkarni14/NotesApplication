<script setup>
import {ref,defineProps } from 'vue'
import NoteListing from './NoteListing.vue';



//for overlay
const addNoteOverlay = ref(false);
const addNotes = () =>{
    addNoteOverlay.value = !addNoteOverlay.value;
};

// overlay Cancel Button
const cancelAddNote = ()=>{
    addNoteOverlay.value = !addNoteOverlay.value;
}

// Add Note Text
const notes =ref([]);
//const notess = ref([]);

const newNote = ref('');
const newNoteHeading = ref('');
var today = new Date();
var dd = String(today.getDate()).padStart(2, '0');
var mm = String(today.getMonth() + 1).padStart(2, '0'); //January is 0!
var yyyy = today.getFullYear();

today = mm + '/' + dd + '/' + yyyy;
const newNoteDate = ref(today);
const addNote=()=>{

    const newNotes={
        noteHeading : newNoteHeading.value,
        note : newNote.value,
        date : newNoteDate.value
    }
    notes.value.push(newNotes);
    //console.log(notess)
newNote.value = '';
newNoteHeading.value = '';


    //console.log(newNotes);
    //console.log(notes)
}


</script>

<template>
    <nav class="bg-yellow-600 border-b border-yellow-500">
      <div class="mx-auto max-w-7xl px-2 sm:px-6 lg:px-8">
        <div class="flex h-20 items-center justify-between">
          <div
            class="flex flex-1 items-center justify-center md:items-stretch md:justify-start"
          >
            <!-- Logo -->
            <a class="flex flex-shrink-0 items-center mr-4" href="/src/assets/img/NotesLogo.png">
              <img class="h-10 w-auto" src="/src/assets/img/NotesLogo.png" alt="Vue Jobs" />
              <span class="hidden md:block text-white text-2xl font-bold ml-2 text-center"
                >Notes</span
              >
            </a>
            <div class="md:ml-auto">
              <div class="flex space-x-2">
                <button @click="addNotes"
                  
                  class="py-3 px-4 inline-flex items-center gap-x-2 text-sm font-medium rounded-lg border border-gray-200 bg-white text-gray-800 shadow-sm hover:bg-gray-50 focus:outline-none focus:bg-gray-50 disabled:opacity-50 disabled:pointer-events-none dark:bg-neutral-800 dark:border-neutral-700 dark:text-white dark:hover:bg-neutral-700 dark:focus:bg-neutral-700" aria-haspopup="dialog" aria-expanded="false" aria-controls="hs-basic-modal" data-hs-overlay="#hs-basic-modal"
                  >Add Note
                  </button
                >  
              </div>
            </div>
          </div>
        </div>
      </div>
    </nav>

    <div v-if="addNoteOverlay"class="fixed inset-0 flex items-center justify-center bg-black bg-opacity-50 z-50">
    <div >
    <h2 class="text-3xl font-bold mb-4">Add Note</h2>

    <div class="relative">
        <input 
        v-model="newNoteHeading"
        type="text"
        placeholder="Note Heading .."
        class="w-full px-4 py-2 rounded-lg border-2 border-gray-300 focus:outline-none focus:border-blue-500"
      
        />
        
      <textarea
        v-model="newNote"
        type="text"
        placeholder="Enter your note..."
        class="w-full px-4 py-2 rounded-lg border-2 border-gray-300 focus:outline-none focus:border-blue-500"
      ></textarea>
      
    </div>

    <button @click="addNote"
      
      class="mt-4 px-6 py-2 bg-blue-500 text-white rounded-lg hover:bg-blue-600 focus:outline-none focus:bg-blue-600"
    >
      Add Note
    </button>
    <button @click="cancelAddNote"
       
        class=" mt-4 px-6 py-2 bg-gray-500 text-white rounded-lg hover:bg-gray-600 focus:outline-none focus:bg-gray-600"
      >
        Cancel
      </button>
</div>
</div>
<section class="bg-green-50 px-4 py-10">
      <div class="container-xl lg:container m-auto">
        <h2 class="text-3xl font-bold text-green-500 mb-6 text-center">
          Yours Notes
        </h2>
        <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
          
            <NoteListing v-for="(note,index) in notes"  :key="note.id" :note="note"/>
            

          </div>
          </div>
          </section>

</template>