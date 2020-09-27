<template>
  <div style="color:white">
    <vs-row>
      <vs-col>
        <div align="center">
          <img :src="this.$route.params.id.image_url">
          <!-- <h1>สินค้าหมายเลข {{ this.$route.params.id.image_url }}</h1> -->
          <h1>{{ this.$route.params.id.title }}</h1>
        </div>
        <div align="left">
          <h3>{{ this.$route.params.id.synopsis }}</h3>
          <h3>Episode : {{ this.$route.params.id.episodes }}</h3>
          <h3>Score : {{ this.$route.params.id.score }}</h3>
          <h3>Rating : {{ this.$route.params.id.rated }}</h3>
          <h3>Start Date : {{ this.$route.params.id.start_date }}</h3>
          <h3>End Date : {{ this.$route.params.id.end_date }}</h3>
          <h3>Click link : {{ this.$route.params.id.url }}</h3>
        </div>
      </vs-col>
    </vs-row>
  </div>
</template>

<script>
export default {

}
</script>

<style>
</style>
