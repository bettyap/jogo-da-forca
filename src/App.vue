<template>
  <div class="container">
    <h1> Jogo da forca</h1>
    <section v-if="screen === 'inicio'">

      <Forms v-if="stage === 'palavra'"
        title="Defina a palavra"
        button="Próximo"
        :action="setPalavra"
      />

      <Forms v-else-if="stage === 'dica'"
        title="Defina a dica"
        button="Iniciar jogo =)"
        :action="setDica"
      />

    </section>

    <section v-else-if="screen === 'jogo'">

      <Game 
        :errors="errors"
        :word="word"
        :tip="tip"
        :verificarLetra="verificarLetra"
        :stage="stage"
        :letters="letters"
        :jogar="jogar"
        :jogarNovamente="jogarNovamente"
      />

    </section>
  </div>
  
</template>

<script>
import Forms from './components/Forms.vue'
import Game from './components/Game.vue'

  export default {
    data() {
      return {
        screen: 'inicio',
        stage: 'palavra',
        word: '',
        tip: '',
        errors: 0,
        letters: []
      }
    },
    components: { 
      Forms, 
      Game
    },
    methods: {
      setPalavra(palavra) {
        this.word = palavra;
        this.stage = 'dica'
      },
      setDica(dica) {
        this.tip = dica;
        this.screen = 'jogo'
        this.stage = 'jogo'
      },
      verificarLetra(letter) {
        return this.letters.find(item => item.toLowerCase() === letter.toLowerCase());
      },
      jogar(letter) {
        this.letters.push(letter);

        this.verificarErros(letter)
      },
      verificarErros(letter) {
        if(this.word.toLowerCase().indexOf(letter.toLowerCase()) >= 0 ){
          return this.verificarAcertos();
        }

        this.errors++;

        if(this.errors === 6){
          this.stage = 'enforcado'
        }
      },
      verificarAcertos() {
        let letrasUnicas = [...new Set(this.word.split(''))];
        if(letrasUnicas.length === (this.letters.length - this.errors)){
          this.stage = 'ganhador'
        }
      },
      jogarNovamente() {
        this.word = '';
        this.tip = '';
        this.errors = 0;
        this.letters = [];
        this.screen = 'inicio';
        this.stage = 'palavra';
      }
    }
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
