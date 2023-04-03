<template>
  <div class="game-container">

    <Gibbet 
      :errors="errors"
    />

    <Word 
      :word="word"
      :tip="tip"
      :verificarLetra="verificarLetra"
      :stage="stage"
    />

    <Keyboard 
      v-if="stage === 'jogo'"
      :letters="letters"
      :verificarLetra="verificarLetra"
      :jogar="jogar"
    />

    <Finale 
      v-if="stage != 'jogo'"
      :stage="stage"
      :text="stage === 'ganhador' ? 'Parabéns =)' : 'Que pena, você perdeu =('"
      :jogarNovamente="jogarNovamente"
    />

  </div>
</template>

<script>
import Gibbet from './Gibbet.vue'
import Word from './Word.vue'
import Keyboard from './Keyboard.vue'
import Finale from './Finale.vue'

export default {
  props: {
    errors: Number,
    word: String,
    tip: String,
    verificarLetra: Function,
    stage: String,
    letter: Array,
    jogar: Function,
    jogarNovamente: Function
  },
  data(){
    return {

    }
  },
  components: {
    Gibbet, 
    Word, 
    Keyboard,
    Finale
  }
}
</script>

<style scoped>
  .game-container{
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
  }
</style>