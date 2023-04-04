<template>
  <div class="gibbet-container">
    <img 
      :src="`https://raw.githubusercontent.com/william-costa/wdev-hangman-game-resources/master/images/hangman/${errors}.svg`"
    >
  </div>
</template>

<script>
export default {
  props: {
    errors: Number
  },
  data(){
    return {

    }
  }
}
</script>

<style scoped>
  .forms-container{
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    margin-top: 1.25rem;
  }
  .gibbet-container img {
    height: 6.25rem;
  }
</style>