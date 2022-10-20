<template>
  <div class="container">
    <div class="row">
      <div class="col-md-8 mx-auto">
        <h3>Редактирование заказа {{ ride.number }}:</h3>
        <form name="contact-form">
          <div class="mb-3">
            <input type="text" id="number" class="form-control" v-model="form.number">
            <input type="text" id="car" class="form-control" v-model="form.car">
            <input type="text" id="driver" class="form-control" v-model="form.driver">
            <input type="text" id="shift" class="form-control" v-model="form.shift">
            <input type="text" id="price" class="form-control" v-model="form.price">
            <input type="text" id="cash" class="form-control" v-model="form.cash">
            <input type="text" id="toll" class="form-control" v-model="form.toll">
            <input type="text" id="extra_tax" class="form-control" v-model="form.extra_tax">
            <input type="text" id="tip" class="form-control" v-model="form.tip">
            <input type="text" id="comment" class="form-control" v-model="form.comment">
          </div>
          <button class="btn btn-primary" type="submit" @click.prevent="submitForm" :disabled="!isComplete">Сохранить</button>
        </form>
      </div>
    </div>
    <Bottom />
  </div>
</template>


<script>
import axios from "axios";
import Bottom from "@/components/Bottom";
export default {
  components: {Bottom},
  layout: "ride_detail",
  data() {
    return {
      form: {
        number: '',
        car: '',
        driver: '',
        shift: '',
        price: '',
        cash: '',
        toll: '',
        extra_tax: '',
        tip: '',
        comment: '',
      }
    }
  },
  methods: {
    submitForm() {
      let rideFormData = new FormData();
      rideFormData.set('number', this.form.number);
      rideFormData.set('car', this.form.car);
      rideFormData.set('drivr', this.form.driver);
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
        url: `http://127.0.0.1:8000/rides/${this.form.number}`,
        data: rideFormData
      }).then(function (response){
        console.log(response);
      }).catch(function (response){
        console.log(response);
      });
      this.$router.push("/success");
    }
  }
}
</script>


<style>

</style>
