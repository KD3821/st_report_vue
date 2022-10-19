<template>
  <div>
    <Navbar />
    <User />
    <div class="container">
      <Nuxt />
    </div>
    <Footer />
  </div>
</template>


<script>
import Navbar from "~/components/Navbar";
import User from "@/components/User";
import Footer from "@/components/Footer";
export default {
  components: {
    Navbar,
    User,
    Footer,
  }
};
</script>


<style>

</style>
