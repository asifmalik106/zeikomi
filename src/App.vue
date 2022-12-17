<script setup>
import HelloWorld from './components/HelloWorld.vue'
import TheWelcome from './components/TheWelcome.vue'
</script>

<template>
  <div class="h-100 d-flex align-items-center justify-content-center">
    <div class="container-fluid">
      <div class="row">
        <div class="col-xl-4 offset-xl-4 col-lg-4 offset-lg-4 col-md-4 offset-md-4 col-sm-12">
          <HelloWorld msg="You did it!" />
        </div>
      </div>
    </div>
  </div>

</template>

<style scoped>

</style>
