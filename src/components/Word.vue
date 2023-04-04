<template>
  <div class="word-container">

    <div class="word-letters">
      <div class="word-letter" v-for="(letter,key) in word" :key="key">
        {{ (verificarLetra(letter) || stage === "enforcado" ) ? letter : '' }}
      </div>
    </div>

    <div class="word-tip">
      {{tip}}
    </div>

  </div>
</template>

<script>
export default {
  props: {
    word: String,
    tip: String,
    verificarLetra: Function,
    stage: String
  },
  data(){
    return {

    }
  }
}
</script>

<style scoped>
  .word-container{
    text-transform: uppercase;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
  }
  .word-letters {
    display: flex;
    margin-bottom: 1.25rem;
  }
  .word-letter {
    width: 1.875rem;
    height: 1.875rem;
    margin: 0 0.3125rem;
    border-bottom: 2px solid var(--green-300);
    font-weight: bold;
    display: flex;
    justify-content: center;
    align-items: center;
  }
</style>