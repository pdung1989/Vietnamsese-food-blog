<template>
  <div>
    <TheHeader />
    <main class="main">
      <nuxt/>
    </main>
  </div>
</template>

<script>
import TheHeader from '@/components/TheHeader/TheHeader'

export default {
  components: {
    TheHeader: TheHeader
  }
}
</script>


<style>
* {
  box-sizing: border-box;
}

body {
  font-family: 'Lora', serif;
  margin: 0;
}

.main {
  margin-top: 100px;
}
</style>