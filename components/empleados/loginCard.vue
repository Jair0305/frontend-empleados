
<template>
  <v-card elevation="0" color="blue darken-2" width="400" height="300" rounded>
    <v-card-title>
      Bienvenido
    </v-card-title>
    <v-card-text class="mt-4 mb-4 pt-4 pb-4">
      <v-form ref="form">
        <div class="textField">
          <v-row style="width: 100%">
            <v-text-field
              v-model="usuario"
              type="usuario"
              :rules="size"
              solo
            />
          </v-row>
          <v-row style="width: 100%">
            <v-text-field
              v-model="password"
              type="password"
              :rules="size"
              solo
            />
          </v-row>
        </div>
      </v-form>
    </v-card-text>
    <v-card-actions>
      <v-row align="center" justify="center">
        <v-btn block elevation="0" color="blue lighten-5" @click="loginBackend">
          <span style="text-transform: none; color: #0D47A1">
            Login
          </span>

        </v-btn>

      </v-row>
    </v-card-actions>
  </v-card>
</template>

<script lang="ts">
export default {
  data() {
    return {
      usuario: '',
      password: '',
      size: [
        v => v.trim().length !== 0 || 'Campo requerido',
      ]
    }
  },
  methods:{
    loginBackend(){
      console.log('@@@ variables', this.usuario, this.password)
      const isValid = this.$refs.form.validate()
      if(isValid)
      {
        const body = {
          usuario: this.usuario,
          password: this.password
        }
        this.$axios.post('/login', body).then((res) =>{
          console.log('@@ res =>', res)
        }).catch((error) => {
          console.log('@@@ error =>', error)
        })

        this.$router.push('/empleados')
      }else
      {
        this.$emit('show-alert', {
          showAlert: true,
          color: 'red',
          type: 'error',
          message: 'Error en el login',
          icon: 'mdi-error'
        })
      }
    }
  }
}
</script>

<style scoped>
  .textField
  {
    width: 100%;
    margin: 10px;
  }
</style>
