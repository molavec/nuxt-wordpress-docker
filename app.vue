<script setup lang="ts">
const wp = await useFetch('http://wordpress/wp-json/wc/v3')
</script>



<template>
  <div>
    <NuxtRouteAnnouncer />
    <p>Data wsssdd</p>
    <p> {{ wp.data }}</p>
    <NuxtWelcome />
  </div>
</template>
