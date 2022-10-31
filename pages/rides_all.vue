<template>
  <div>
    <button @click.prevent="showRides">FIRE</button>
    <Rides v-bind:user="user" v-bind:rides="rides" />
    <Bottom :btn_1=prev_page :btn_2=next_page :link_1=p_link :link_2=n_link />
  </div>

</template>

<script>
import axios from "axios";
import Rides from "@/components/Rides";
import Bottom from "@/components/Bottom";
export default {
  components: {
    Bottom,
    Rides,
  },
  data() {
    return {
      rides: this.showRides()
    }
  },
  methods: {
    async showRides() {
      const {data} = await this.$axios.get(`/rides/`);
      console.log(data.results)
      return {
        rides: data.results
      }
    }
  },
  // async asyncData(ctx) {
  //   const {data} = await axios.get(`http://127.0.0.1:8000/rides/`);
  //   console.log(data);
  //   return {
  //     rides: data.results,
  //     prev_page: '<<<',
  //     next_page: '>>>',
  //     p_link: data.previous,
  //     n_link: data.next
  //   }
  // },
  computed: {
    loggedIn() {
      return this.$auth.loggedIn
    },
    user() {
      return this.$auth.user
    },
  }
}
</script>

<style>

</style>
