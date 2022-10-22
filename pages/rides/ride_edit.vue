<template>
  <div class="container">
    <div class="row">
      <div class="col-md-8 mx-auto">
        <h3>Редактирование заказа XX:</h3>
        <form name="contact-form">
          <div class="mb-3">
            <input type="text" id="user" class="form-control" v-model="form.user" placeholder="USER">
            <input type="text" id="id" class="form-control" v-model="form.id" placeholder="ID">
            <input type="text" id="number" class="form-control" v-model="form.number" placeholder="Номер">
            <input type="text" id="car" class="form-control" v-model="form.car" placeholder="Авто">
            <input type="text" id="driver" class="form-control" v-model="form.driver" placeholder="Водитель">
            <input type="text" id="price" class="form-control" v-model="form.price" placeholder="Стоимость">
            <input type="text" id="cash" class="form-control" v-model="form.cash" placeholder="Нал">
            <input type="text" id="toll" class="form-control" v-model="form.toll" placeholder="ЗСД">
            <input type="text" id="tip" class="form-control" v-model="form.tip" placeholder="Чаевые">
            <input type="text" id="comment" class="form-control" v-model="form.comment" placeholder="Комментарий">
          </div>
          <button class="btn btn-primary" type="submit" @click.prevent="submitForm" :disabled="!isComplete">Сохранить</button>
        </form>
      </div>
    </div>
  </div>
</template>


<script>
import axios from "axios";
export default {
  layout: "ride_detail",
  data() {
    return {
      form: {
        user: '',
        id: '',
        number: '',
        car: '',
        driver: '',
        price: '',
        cash: '',
        toll: '',
        tip: '',
        comment: '',
      }
    }
  },
  methods: {
    submitForm() {
      let rideFormData = new FormData();
      rideFormData.set('user', this.form.user);
      rideFormData.set('id', this.form.id);
      rideFormData.set('number', this.form.number);
      rideFormData.set('car', this.form.car);
      rideFormData.set('driver', this.form.driver);
      rideFormData.set('shift', this.form.shift);
      rideFormData.set('price', this.form.price);
      rideFormData.set('cash', this.form.cash);
      rideFormData.set('toll', this.form.toll);
      rideFormData.set('extra_tax', this.form.extra_tax);
      rideFormData.set('tip', this.form.tip);
      rideFormData.set('comment', this.form.comment);
      console.log('submitting data...');
      axios({
        method: 'patch',
        url: `http://127.0.0.1:8000/rides/${this.form.id}/`,
        data: rideFormData
      }).then(function (response){
        console.log(response);
      }).catch(function (response){
        console.log(response);
      });
      this.$router.push(`/rides/${this.form.id}/`);
    }
  },
  computed: {
    isComplete() {
      return this.form.id && this.form.number && this.form.price;
    }
  }
}
</script>


<style>

</style>
