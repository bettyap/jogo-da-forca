<template>
  <div class="forms-container">
    <div class="forms-title">
      <p>{{title}}</p>
    </div>
    <input class="forms-input" v-maska data-maska="A" data-maska-tokens="A:[A-Za-záàâãéèêíïóôõöúçñÁÀÂÃÉÈÍÏÓÔÕÖÚÇÑ]:multiple"  v-model="inputValue"/>

    <button 
      :disabled="inputValue.length === 0"
      @click="onSubmit"
    >
      {{button}}
    </button>
  </div>
</template>

<script>
export default {
  props: {
    title: String,
    button: String,
    action: Function
  },
  data(){
    return {
      inputValue: ''
    }
  },
  methods: {
    onSubmit: function(){
      this.action(this.inputValue.toUpperCase());
      this.inputValue = '';
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
  .forms-input {
    padding: 0.5rem;
    border: 0;
    border-radius: 5px;
    margin: 1rem 0;
    font-size: 1rem;
  }
</style>