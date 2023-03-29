<template>
  <div class="container">
    <h1> Jogo da forca</h1>
    <section v-if="screen === 'inicio'">
      <Forms />

    </section>

    <section v-else-if="screen === 'jogo'">
      Jogo
    </section>
  </div>
  
</template>

<script>
import Forms from './components/Forms.vue'

  export default {
    data() {
      return {
        screen: 'inicio'
      }
    },
    components: { Forms }
  }
</script>

<style scoped>
  .container {
    width: 100%;
    height: 100vh;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
  }
</style>
