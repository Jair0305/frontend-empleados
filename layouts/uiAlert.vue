<script lang="ts">

export default {
  props: {
    color: {
      type: String,
      default: 'green'
    },
    type: {
      type: String,
      default: 'success'
    },
    icon: {
      type: String,
      default: ''
    },
    message: {
      type: String,
      default: ''
    },
    showAlert: {
      type: Boolean,
      default: false
    }
  }

}

</script>

<template>
  <v-alert v-if="showAlert" :color="color" :type="type">
    <v-icon>
      {{icon}}
    </v-icon>
    {{message}}
  </v-alert>
</template>

<style scoped>

</style>
