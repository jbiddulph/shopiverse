<template>
  <div>
    <h1 class="text-5xl font-extrabold dark:text-white">Please check your email to confirm registration</h1>

  </div>
</template>

<script lang="ts" setup>
definePageMeta({
  middleware: [
    async (from, to) => {
      if(from.name !== 'register') return await navigateTo('/')
    }
  ]
})
</script>

<style>

</style>