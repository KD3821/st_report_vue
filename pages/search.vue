<template>
  <div>
    <SearchField @searchRides="rides = $event"/>
    <div class="row">
      <div class="col-md-11 mx-auto mb-3">
        <h3>Всего найдено заказов: {{ count }}</h3>
        <table class="ride_table">
          <tbody>
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
          </tbody>
        </table>
      </div>
    </div>
    <Bottom :btn_1=prev_page :btn_2=next_page :link_1=p_link :link_2=n_link />
  </div>
</template>


<script>
import axios from "axios";
import Bottom from "@/components/Bottom";
import SearchField from "@/components/SearchField";
export default {
  components: {Bottom, SearchField},
  watchQuery: ['q'],
  data() {
    return {
      rides: ''
    }
  },
  async asyncData({route}) {
    const {data} = await axios.get(`http://127.0.0.1:8000/rides/?search=${route.query.q}`);
    return {
      rides: data.results,
      count: data.count
    }
  }
}
</script>


<style>

</style>
