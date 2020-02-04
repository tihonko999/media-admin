<template lang="pug">
  ul
    li(v-for="item in matters")
      nuxt-link(:to="`/matters/${item.id}`") {{item.title}}
</template>

<script>
export default {
  async asyncData ({ $axios, error }) {
    try {
      const { data } = await $axios.get('matters')
      return { matters: data }
    } catch (e) {
      error(e)
    }
  },
}
</script>

<style lang="sass" scoped>
li
  margin-bottom: 10px
</style>
