<template>
  <h1>Привет, это страница ВЫХОДа</h1>
</template>

<script>
export default {
  async created() {
    await this.$auth.logout()
  }
}
</script>

<style>

</style>
