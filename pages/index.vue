<template>
  <ul>
    <li v-for="content in contents" :key="content.id">
      <nuxt-link :to="`/${content.id}`">
        {{ content.title }}
      </nuxt-link>
    </li>
  </ul>
</template>

<script>
import axios from 'axios'
export default {
  async asyncData() {
    const { data } = await axios.get(
      // your-service-id部分は自分のサービスidに置き換えてください
      'https://yamachokiblog.microcms.io/api/v1/news',
      {
        // your-api-key部分は自分のapi-keyに置き換えてください
        headers: { 'X-MICROCMS-API-KEY': '98c7e39b3ecb44ef9a819e07332b80405543' }
      }
    )
    return data
  }
}
</script>
