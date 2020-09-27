<template>
  <div class="row text-light">
    <div class="col-sm" align="center">
      <img
        src="https://cdn.discordapp.com/attachments/392353546332405763/757956807778893954/cropped-animeworld-01.png"
        class="img-fluid mx-auto"
      >
      <vs-row justify="center">
        <vs-input v-model="textSearch" type="text" placeholder="ค้นหาการ์ตูน" />
        <vs-button danger @click="searchData()">
          Search Anime
        </vs-button><br><br>
      </vs-row>
      <vs-row align="center" justify="space-around">
        <vs-card
          v-for="data in animeData.slice(
            (currentPage - 1) * perPage,
            (currentPage - 1) * perPage + perPage
          )"
          :key="data.mal_id"
          type="1"
          class="mb-3"
        >
          <template #title>
            <h2>{{ data.title }}</h2>
          </template>
          <template #img>
            <img :src="data.image_url">
          </template>
          <template #text />
          <template #interactions>
            <nuxt-link :to="{ name: 'product-id', params: { id: data } }">
              <vs-button primary>
                Read more!
              </vs-button>
            </nuxt-link>
          </template>
        </vs-card>
      </vs-row><br>
      <div v-if="run == true" class="center">
        <vs-pagination
          v-model="currentPage"
          :length="5"
          :per-page="perPage"
        />
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  data () {
    return {
      animeData: '',
      textSearch: '',
      perPage: 12,
      currentPage: 1,
      run: false
    }
  },
  methods: {
    searchData () {
      axios
        .get('https://api.jikan.moe/v3/search/anime?q=' + this.textSearch + '')
        .then((response) => {
          this.animeData = response.data.results
          this.run = true
        })
        .catch((err) => {
          console.log(err)
        })
    }
  }
}
</script>

<style>
body {
  padding: 3rem;
  background-image: url("https://cdn.discordapp.com/attachments/392353546332405763/758277143858774016/704014176bc1f285c0c627b4910b64ae.jpg");
  background-attachment: fixed;
  background-repeat: no-repeat;
  background-size: 100% 100%;
  height: 100vh;
}
</style>
