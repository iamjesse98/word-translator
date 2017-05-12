<template>
  <md-card style="padding: 20px; text-align: center; font-size: 35px;">
    {{ translatedText }}
  </md-card>
</template>

<script>
export default {
  name: 'translateOutput',
  props: ['translatedText']
}
</script>

<style>
</style>
