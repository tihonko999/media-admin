<template lang="pug">
  .navbar
    nuxt-link(to="/") Index
    .username Username: {{$auth.user.name}}
    .logout(@click="logOut") Logout
</template>

<script>
export default {
  data () {
    return {
      busy: false,
    }
  },
  methods: {
    async logOut () {
      if (this.busy) return
      this.busy = true
      try {
        await this.$auth.logout()
        this.$router.push('/')
      } catch (e) {
        this.error(e)
      }
      this.busy = false
    },
  },
}
</script>

<style lang="sass" scoped>
.navbar
  display: flex
  border-bottom: 1px solid #ccc
  > *
    padding: 10px
  .logout
    color: cadetblue
    cursor: pointer
    border-left: 1px solid #ccc
  .username
    margin-left: auto
</style>
