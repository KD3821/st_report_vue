<template>
  <div class="row">
    <div class="col-md-11 mx-auto mb-3">
      <h3>Все заказы:</h3>
      <table class="ride_table">
        <tr>
          <th>Дата заказа</th>
          <th>Заказ: </th>
          <th>Сумма: </th>
          <th>Наличные: </th>
          <th>Водитель: </th>
          <th>А/М: </th>
          <th>П-ка смены: </th>
          <th>Доп.ком.: </th>
          <th>Режим: </th>
          <th>ЗСД: </th>
          <th>Чаевые: </th>
          <th>Коммент: </th>
        </tr>
        <tr v-for="ride in rides" :key="ride.id">
          <td>{{ride.shift.date}}</td>
          <td><nuxt-link :to="`/rides/${ride.id}`">{{ride.number}}</nuxt-link></td>
          <td>{{ride.price}}</td>
          <td>{{ride.cash}}</td>
          <td>{{ride.driver}}</td>
          <td>{{ride.car}}</td>
          <td>{{ride.save_tax}}</td>
          <td>{{ride.tax_result}}</td>
          <td>{{ride.extra_tax.mode}}</td>
          <td>{{ride.toll}}</td>
          <td>{{ride.tip}}</td>
          <td>{{ride.comment}}</td>
        </tr>
      </table>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  async asyncData(ctx) {
    const {data} = await axios.get(`http://127.0.0.1:8000/rides/`);
    return {
      rides: data.results
    }
  }
}
</script>

<style>

</style>
