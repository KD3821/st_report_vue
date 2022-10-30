<template>
  <div class="col-md-5 mx-auto">
    <div class="text-center">
      <form class="form-signin" @submit.prevent="userLogin">
        <h3>Войдите в систему</h3>
        <label for="inputUsername" class="sr-only">Имя пользователя:</label>
        <input id="inputUsername" class="form-control" v-model="login.username">
        <label for="inputPassword" class="sr-only">Пароль:</label>
        <input id="inputPassword" class="form-control mt-2" v-model="login.password" type="password">
        <button class="btn mt-2 btn-lg btn-primary btn-block" type="submit">Войти</button>
      </form>
    </div>
  </div>
</template>

<script>
export default {
  layout: "ride_detail",
  data() {
    return {
      login: {
        username: '',
        password: ''
      }
    }
  },
  methods: {
    async userLogin() {
      try {
        let response = await this.$auth.loginWith('local', {data: this.login});
        console.log(response);
        this.$router.push('/')
      } catch (err) {
        console.log(err)
      }
    }
  }
}
</script>

<style>

</style>
