<template>
  <div>
    <Navbar />
    <User />
    <Nuxt />
    <Footer />
  </div>
</template>

<script>
import Navbar from "@/components/Navbar";
import Footer from "@/components/Footer";
import User from "@/components/User";

export default {
  components: {
    Footer,
    Navbar,
    User,
  }
}
</script>

<style>

</style>
