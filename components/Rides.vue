<template>
    <div>
      <div class="row">
        <div class="col-md-11 mx-auto mb-3">
          <h3>Все заказы:</h3>
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
    </div>
</template>

<script>
export default {
  name: "Rides",
  props: {
    rides: {
      type: Array
    }
  }
};
</script>

<style>

</style>
