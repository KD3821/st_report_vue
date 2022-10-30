<template>
  <div>
    <div class="my_user" v-if="user">
      <strong>
        Вы вошли как:  <span style="color: green;">{{ user.username }}</span>
      </strong><br>
    </div>
    <div class="my_user" v-else>
      <strong>
        Вы не авторизованы
      </strong><br>
    </div>
  </div>
</template>


<script>
export default {
  name: "User",
  computed: {
    user() {
      return this.$auth.user
    }
  }
}
</script>


<style>

</style>
