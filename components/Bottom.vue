<template>
  <div class="col-md-8 mx-auto">
    <nuxt-link class="btn btn-secondary" type="button" :to="`${link_1}`">{{ btn_1 }}</nuxt-link>
    <nuxt-link class="btn btn-secondary" type="button" :to="`${link_2}`">{{ btn_2 }}</nuxt-link>
  </div>
</template>


<script>
export default {
  name: "Bottom",
  props: ['btn_1', 'btn_2', 'link_1', 'link_2']
}
</script>

<style>

</style>
