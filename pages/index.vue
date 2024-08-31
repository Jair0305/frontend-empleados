<template>
  <div>
    <login-card @show-alert="showAlert"/>
    <ui-alert/>
  </div>
</template>

<script>
import loginCard from '@/components/empleados/loginCard.vue'

export default {
  name: 'IndexPage',
  components: {
    loginCard
  },
  layout: 'login',
  methods: {
    showAlert(data)
    {
      console.log('@@@ data =>', data)
      this.$nuxt.$emit('show-alert', data)
    }
  }
}
</script>
