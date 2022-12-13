<template>
  <div>
    home.vue    
  </div>
</template>

<script>
import axios from 'axios';

export default {
  mounted() {
    this.searchBook()
  },
  methods:{
    async searchBook() {
      try {
        let sort = '';
        let target = '';
        let title = '';            

        let api = await axios.get(
          `https://dapi.kakao.com/v3/search/book?sort=${sort}&target=${target}&page=1`,
          {
            headers: {
              Authorization: 'KakaoAK 3b9b7e5018ae18db72532378d670854e',
            },
            params: {
              query: title,
            },
          },
        );

        console.log('api',api)

      } catch (err) {
        console.log(err);
      }
      
    }
  }
}
</script>

<style>

</style>