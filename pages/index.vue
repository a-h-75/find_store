<template>
  <section>
    <h2>検索結果 （{{shops.length}}件）</h2>
    <p v-if="error">データの取得に失敗しました</p>
    <ul>
      <li v-for="shop in shops" :key="shop.id">
        <p>{{shop.id}}</p>
        <p>{{shop.name}}</p>
      </li>
    </ul>
  </section>
</template>

<script>
import axios from 'axios';

export default {
  data() {
    return {
      shops: [],
      error: false
    }
  },
  methods: {
    setShop(res) {
      this.shops = res.data.results.shop
    },
    setError(err) {
      console.log(err)
      this.error = true
    }
  },
  async mounted() {
    try {
      const position = await getCurrentPosition()
      // APIからデータ取得
      const { data } = await

      this.$axios('http://localhost:3000/api/gourmet/v1/', {
        // パラメータの設定
        params: {
          key: process.env.apikey,
          // lat: '35.6811689074',
          lat: position.coords.latitude,
          // lng: '139.7672508709',
          lng: position.coords.longitude,
          format: 'json'
        }
      })
    this.shops = data.results.shop
    } catch(err) {
      this.setError(err)
    }
  }
}
</script>

<style>

</style>
