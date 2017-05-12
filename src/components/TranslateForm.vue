<template>
  <div id="translateForm">
    <form @submit="formSubmit">
      <md-card style="padding: 10px;">
        <md-input-container>
          <label>Enter a Word</label>
          <md-input placeholder="Enter a Word" v-model="textToTranslate"></md-input>
        </md-input-container>
        
        
        <md-layout md-gutter>
          <md-layout md-flex-xsmall="100" md-flex-small="33" md-flex-medium="33">
            <md-input-container>
              <label for="lang">Language</label>
              <md-select name="lang" v-model="language">
               <md-option v-for="l in [{ id: 'ru', title: 'Russian' }, { id: 'el', title: 'Greek' }, { id: 'es', title: 'Spanish' }, { id: 'fr', title: 'French' }, { id: 'zh', title: 'Chinese' }, { id: 'hi', title: 'Hindi' }, { id: 'te', title: 'Telugu' }]" v-bind:value=" l.id " id="lang">{{ l.title }}</md-option>
              </md-select>
            </md-input-container>

          </md-layout>
          <md-layout md-flex-xsmall="100" md-flex-small="33" md-flex-medium="33">
            <md-button class="md-raised" style="width: 100%" type="submit">Translate</md-button>
          </md-layout>
          <md-layout md-flex-xsmall="100" md-flex-small="3" md-flex-medium="33">
            <md-button class="md-raised md-warn" style="width: 100%" type="reset">Clear</md-button>
          </md-layout>
        </md-layout>
      </md-card>
    </form>
  </div>
</template>

<script>
export default {
  name: 'translateForm',
  data: {
      textToTranslate: '',
      language: '' 
  },
  created() {
    this.language = 'ru'
  },
  methods: {
    formSubmit(e) {
      e.preventDefault()
      this.$emit('formSubmit', this.textToTranslate, this.language)
      //alert(this.textToTranslate)
    }
  }
}
</script>

<style>
.md-theme-default.md-button:not([disabled]).md-raised:not(.md-icon-button) {
  background: #35495e !important;
  color: #fff !important;
}
.md-theme-default.md-button:not([disabled]).md-raised:not(.md-icon-button):hover {
  background: #41b883 !important;
  color: #fff !important;
}
</style>
