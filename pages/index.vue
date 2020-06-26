<template>
  <section class="container mx-auto text-center">
    <div class="text-white">
      <!-- <Logo /> -->
      <Header />
      <Downloader/>
      <Footer/>
      <Revenue/>
    </div>
  </section>
</template>

<script>
import Downloader from '~/components/Downloader.vue'
import Revenue from '~/components/Revenue.vue'
import Header from '~/components/Header.vue'
import Footer from '~/components/Footer.vue'

export default {
  components: {
    // Logo,
    Downloader,
    Revenue,
    Header,
    Footer
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css?family=PT+Sans:400,400i,700');

html,
#__nuxt,
#__layout {
  height: 100%;
}

body {
  font-family: "PT Sans", -apple-system, BlinkMacSystemFont, 'Segoe UI',
    Roboto, 'Helvetica Neue', Arial, sans-serif;
  background: black;
  height: 100%;
}

.btn {
  border-radius: 0;
}

@media (min-width: 768px) {
  .container {
    max-width: 1140px;
  }
}
</style>
