<template>
  <div class="row">
    <div class="col-md-10 mx-auto mb-3">
      <h3>Все недели</h3>
      <div class="my_table">
        <div v-for="week in weeks" :key="week.id" class="mb-3">
            <nuxt-link class="btn btn-success" type="button" to="/login">{{ week.week }}</nuxt-link>
            <nuxt-link class="btn btn-info" type="button" to="/add_ride" >Добавить заказ</nuxt-link>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  async asyncData(ctx) {
    const {data} = await axios.get(`http://127.0.0.1:8000/weeks/`);
    return {
      weeks: data.results,
    }
  }
}
</script>

<style>

</style>
