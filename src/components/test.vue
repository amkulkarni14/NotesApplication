<template>
    <div class="max-w-xl mx-auto mt-8 p-6 bg-gray shadow-md rounded-lg">
    <h2 class="text-2xl font-bold mb-4">Add Note</h2>

    <div class="relative">
      <input
        
        type="text"
        placeholder="Enter your note..."
        class="w-full px-4 py-2 rounded-lg border-2 border-gray-300 focus:outline-none focus:border-blue-500"
      />
      <button
       
        class="absolute inset-y-0 right-0 px-3 py-2 bg-gray-200 hover:bg-gray-300 text-gray-600 hover:text-gray-800 rounded-r-lg"
      >
        Cancel
      </button>
    </div>

    <button
      
      class="mt-4 px-6 py-2 bg-blue-500 text-white rounded-lg hover:bg-blue-600 focus:outline-none focus:bg-blue-600"
    >
      Add Note
    </button>
  </div>
</template>