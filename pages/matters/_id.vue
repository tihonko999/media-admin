<template lang="pug">
  .matter
    h1 {{item.title}}
    p {{item.text}}
</template>

<script>
export default {
  async asyncData ({ $axios, params, error }) {
    try {
      const { data } = await $axios.get(`matters/${params.id}`)
      return { item: data }
    } catch (e) {
      error(e)
    }
  },
}
</script>

<style lang="sass" scoped>
.matter
  padding: 10px
</style>
