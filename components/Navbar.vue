<template>
  <nav class="navbar navbar-expand-lg navbar-light" style="background-color: lightcoral;">
    <div class="container-fluid">
      <nuxt-link class="navbar-brand" to="/" id="brand">Твой Парк</nuxt-link>
      <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse justify-content-end" id="navbarSupportedContent">
        <form class="d-flex" style="align-items: center">
          <input name="q" v-model="q" class="form-control me-2" type="text" placeholder="Поиск" aria-label="Search">
          <button class="btn btn-outline-secondary" type="submit" @click.stop.prevent="submit()">Найти</button>
        </form>
        <ul class="navbar-nav mr-auto">
          <client-only>
          <span v-if="loggedIn" style="display: flex">
            <li class="nav-item ">
              <nuxt-link class="nav-link" to="/info">Инфо</nuxt-link>
            </li>
            <li class="nav-item ">
              <nuxt-link class="nav-link" to="/change_pass" >Сменить пароль</nuxt-link>
            </li>
            <li class="nav-item">
              <nuxt-link class="nav-link" to="/logout" >Выход</nuxt-link>
            </li>
          </span>
          <span v-else style="display: flex">
            <li class="nav-item ">
              <nuxt-link class="nav-link" to="/signup" >Регистрация</nuxt-link>
            </li>
            <li class="nav-item">
              <nuxt-link class="nav-link" to="/login" >Вход</nuxt-link>
            </li>
          </span>
          </client-only>
        </ul>

      </div>
    </div>
  </nav>
</template>

<script>
export default {
  name: "Navbar",
  data() {
    return {
      q: null
    }
  },
  methods: {
    submit(){
      this.$router.push("/search?q=" + this.q);
    }
  },
  computed: {
    loggedIn() {
      return this.$auth.loggedIn
    },
    user() {
      return this.$auth.user
    }
  }
}
</script>

<style>

</style>


