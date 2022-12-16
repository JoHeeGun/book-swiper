<template>
  <div>    
    book serach data <br> 
    {{item.documents}} 
  </div>
</template>

<script>
import axios from 'axios';

export default {
  data() {
    return{
      item:[],
    }
  },
  
  mounted() {
    this.searchBook();
  },
  methods:{
    async searchBook() {
      try {
        let sort = 'accuracy';
        let target = 'title';
        let title = 'lion';            

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

        console.log('api',api);

        this.item = api.data;

      } catch (err) {
        console.log(err);
      }
      
    }
  }
}
</script>

<style>
</style>
