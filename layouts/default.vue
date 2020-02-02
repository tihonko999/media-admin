<template lang="pug">
  div
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
}
</script>
