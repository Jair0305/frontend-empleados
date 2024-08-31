<script lang="ts">
export default {
  data (){
    return {
      showAlert: false,
      color: '',
      type: '',
      icon: '',
      message: ''
    }
  },
  created () {
    this.$nuxt.$on('show-alert', (data) => {
      console.log('@@@ layout =>', data)
      this.showAlert = data.showAlert
      this.color = data.color
      this.type = data.type
      this.icon = data.icon
      setTimeout(() => {
        this.showAlert = false
      }, 2000)
    })
  },
  beforeDestroy() {
    this.$nuxt.$off('show-alert')
  }

}
</script>

<template>
  <v-app>
    <v-main>
      <ui-alert
        v-if="showAlert"
        :color="color"
        :type="type"
        :icon="icon"
        :message="message"
      />
      <v-row align="center" justify="center" class="login">
        <Nuxt/>
      </v-row>
    </v-main>
  </v-app>
</template>

<style scoped>
.login
{
  width: 100%;
  height: 100vh;
  background-color: #BBDEFB;
}
.alert
{
  position: absolute;
  top: 10px;
  right: 10px;
}
</style>
