<template>
  <div class="row">
    <div class="col-md-8 mx-auto">
      <h3>Детали заказа {{ ride.number }} от {{ ride.shift.date }}:</h3>
      <hr>
      Сумма: {{ ride.price }}<br>
      Водитель: {{ ride.driver }}<br>
      Автомобиль: {{ ride.car }}<br>
      Наличные: {{ ride.cash }}<br>
      ЗСД: {{ ride.toll }}<br>
      Покуп.смены: {{ ride.save_tax }}<br>
      Чаевые: {{ ride.tip }}<br>
      Коммент: {{ ride.comment }}<br>
      <hr>
    </div>
    <div class="col-md-8 mx-auto">
      <nuxt-link class="btn btn-warning" type="button" to="/rides_all">Корректировка заказа</nuxt-link>
      <nuxt-link class="btn btn-danger" type="button" to="/rides_all">Удалить заказ</nuxt-link>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  async asyncData({params}) {
    const ride = await axios.get(`http://127.0.0.1:8000/rides/${params.id}`);
    return {
      ride: ride.data,
    }
  }
}
</script>

<style>

</style>
