<template>
  <div class="home">
    <Header />
    <Banner />
  </div>
</template>

<script>
// @ is an alias to /src
import Banner from '@/components/banner.vue'
import Header from '@/components/header.vue'

export default {
  name: 'Home',
  components: {
    Banner,
    Header
  }
}
</script>
<style scoped>
  
</style>>
