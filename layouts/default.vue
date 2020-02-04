<template lang="pug">
  div
    navbar
    nuxt
</template>

<script>
import Navbar from '~/components/navbar'

export default {
  components: { Navbar },
  head () {
    return {
      htmlAttrs: {
        class: this.$device.isMobile ? '' : '__desktop',
      },
    }
  },
}
</script>
