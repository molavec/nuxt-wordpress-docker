<script setup lang="ts">
const wp = await useFetch('http://wordpress/wp-json')
const woo = await useFetch('http://wordpress/wp-json/wc/v3')
</script>



<template>
  <div class="content">

    <div>
      <h1>Wordpress</h1>
      <p>{{ wp.error }}</p>
      <pre class="json-content"> {{ JSON.stringify(wp.data, null, 2) }}</pre>
    </div>
    
    <div class="response-container">
      <h1>Woocommerce</h1>
      <p v-if="woo.error">Unable to access Woocommerce API. Check if the plugin is active.</p>
      <pre class="json-content"> {{ JSON.stringify(woo.data, null, 2) }}</pre>
    </div>
  
  </div>
</template>

<style>
.content {
  display: flex;
  flex: wrap;
  gap: 20px;
}

.response-container {
  max-width: 40%;
}

.json-content {
  background-color: #ccc;
  overflow: scroll;
  width: 400px;
  max-height: 600px;
}

</style>
