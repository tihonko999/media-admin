<template lang="pug">
  div
    a(@click="logOut") Logout
    div {{$auth.user}}
    nuxt
</template>

<script>
export default {
  head () {
    return {
      htmlAttrs: {
        class: this.$device.isMobile ? '' : '__desktop',
      },
    }
  },
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
