<template lang="pug">
  form.login(@submit.prevent="signIn")
    h1 Авторизация
    .form-input
      .input-title Email
      input(placeholder="Email" v-model="username" required)
    .form-input
      .input-title Пароль
      input(placeholder="Пароль" v-model="password" required)
    button Войти
</template>

<script>
export default {
  data () {
    return {
      username: '',
      password: '',
      busy: false,
    }
  },
  methods: {
    async signIn () {
      if (this.busy) return
      this.busy = true
      try {
        await this.$auth.login({
          username: this.username,
          password: this.password,
        })
      } catch (e) {
        this.error(e)
      }
      this.busy = false
    },
  },
  layout: 'login',
}
</script>

<style lang="sass" scoped>
.login
  padding: 10px
  margin: 0 auto
  max-width: 300px
.form-input
  margin-bottom: 15px
  input
    display: block
    width: 100%
    border-radius: 4px
    border: 1px solid #ccc
    padding: 7px 10px
    background: transparent
    box-sizing: border-box
  .input-title
    font-weight: bold
    margin-bottom: 5px
button
  width: 100%
  display: block
  box-sizing: border-box
  border-radius: 4px
  padding: 7px 0
  color: white
  cursor: pointer
  background: cornflowerblue
  border: none
  margin-top: 20px
</style>
