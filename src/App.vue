<template>
  <Header />

  <main>
    <section class="main">
      <RouterView />
    </section>
  </main>
  <Footer />
</template>
<script>
import Footer from '../src/components/Footer/Footer.vue'
import Header from '../src/components/Header/Header.vue'
import { RouterView } from 'vue-router'
export default {
    name:'App',
    data(){
      return {

      }
    },
    components:{
      Header,   
      Footer
    },
    methods:{},
    computed:{},

}
</script>
<style scoped>
  main {
    min-height: calc(100vh - 75px - 75px);
  }
</style>