<template>
  <div id="app">
    <md-card style="padding: 10px;">
      <h1>Word Translator</h1>
      <h5>created with vue.js, vue-resource, vue-material, yandex api by &lt;Jesse /&gt;</h5>
    </md-card>
    <TranslateForm v-on:formSubmit="translateText"></translateForm>
    <TranslateOutput v-text="translatedText"></TranslateOutput>
  </div>
</template>

<script>
import TranslateForm from './components/TranslateForm'
import TranslateOutput from './components/TranslateOutput'

export default {
  name: 'app',
  components: {
    TranslateForm,
    TranslateOutput
  },
  data: function() {
    return{
      translatedText: ''
    }
  },
  methods: {
    translateText: function(text, language) {
      //alert(text)
      this.$http.get(`https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20170511T124317Z.2dcd73ec1f0d442f.7527058f74c8b4a075d94671cafb1c207de3ea8c&lang=${language}&text=${text}`)
        .then( response => {
          if(text) this.translatedText = response.body.text[0]
          console.log(this.translatedText)
        })
    }
  }
}
</script>

<style>
#app {

}
</style>
