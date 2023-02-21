<template>
  <Header />

  <main>
    <section class="main">
      <div class="container mx-auto">

      </div>
    </section>
  </main>
  <Footer />
</template>
<script>
import Footer from '../src/components/Footer/Footer.vue'
import Header from '../src/components/Header/Header.vue'
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
<style lang="scss">
  
</style>