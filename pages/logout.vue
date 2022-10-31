<template>
  <h3>Благодарим за пользование системой!</h3>
</template>

<script>
export default {
  name: "logout",
  async created() {
    await this.$auth.logout()
  }
}
</script>

<style>

</style>
