<template>
  <div class="container">
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
      </div>
    </div>
    <Bottom :btn_1=button1 :btn_2=button2 :link_1=link_edit :link_2=link_delete />
  </div>
</template>

<script>
import axios from "axios";
import ride_detail from "@/layouts/ride_detail";
import Bottom from "@/components/Bottom";
export default {
  components: {
    Bottom,
  },
  layout: "ride_detail",
  async asyncData({params}) {
    const ride = await axios.get(`http://127.0.0.1:8000/rides/${params.id}/`);
    return {
      ride: ride.data,
      button1: 'Корректировка заказа',
      button2: 'Удалить заказ',
      link_edit: `/rides/ride_edit`,
      link_delete: '/rides_all'
    }
  }
}
</script>

<style>

</style>
