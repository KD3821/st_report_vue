<template>
  <div>
    <form class="d-flex">
      <input name="sq" v-model="sq" class="form-control me-2" type="text" placeholder="Поиск" aria-label="Поиск">
      <button class="btn btn-outline-secondary" type="submit" @click.stop.prevent="searchRides()">Поиск</button>
    </form>
  </div>
</template>

<script>
import axios from "axios";
export default {
  watchQuery: ['sq'],
  data() {
    return {
      sq: '',
      rides: ''
    }
  },
  methods: {
    async searchRides() {
      this.rides = await axios.get(`http://127.0.0.1:8000/rides/?search=${this.sq}`);
      this.$router.push("/search?q="+this.sq);
      this.$emit('searchRides', this.rides.data);
    },
  }
}
</script>

<style>

</style>
