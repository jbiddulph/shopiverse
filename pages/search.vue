<template>
  <div>
    <form class="max-w-md mx-auto">   
        <label for="default-search" class="mb-2 text-sm font-medium text-gray-900 sr-only dark:text-white">Search for any product</label>
        <div class="relative">
            <div class="absolute inset-y-0 start-0 flex items-center ps-3 pointer-events-none">
                <svg class="w-4 h-4 text-gray-500 dark:text-gray-400" aria-hidden="true" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 20 20">
                    <path stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="m19 19-4-4m0-7A7 7 0 1 1 1 8a7 7 0 0 1 14 0Z"/>
                </svg>
            </div>
            <input v-model="searchInput" type="search" id="default-search" class="block w-full p-4 ps-10 text-sm text-gray-900 border border-gray-300 rounded-lg bg-gray-50 focus:ring-blue-500 focus:border-blue-500 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500" placeholder="Search Mockups, Logos..." required />
        </div>
    </form>
    <br />
    <br />
    <div class="grid grid-cols-4 gap-4">
      <div v-if="searchResults && searchInput" v-for="product in searchResults">
        <ProductComp :product="product" />
      </div>
    </div>
  </div>
</template>

<script lang="ts" setup>
const searchInput = useState(() => null)
const searchResults = useState(() => null)
const {data} = await useFetch('/api/products/search/query', {
  immediate: false,
  query: {
    input: searchInput
  },
  transform: data => {
    searchResults.value = data
  }
})
</script>

<style>

</style>