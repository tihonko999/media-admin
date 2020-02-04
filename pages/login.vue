<template lang="pug">
  form(@submit.prevent="signIn")
    h1 login
    div {{$auth.user}}
    input(placeholder="Email" v-model="username" required)
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
