<template>
  <div>            
    <div>book data v-for</div>
    <div 
      v-for="(i,index) in item.documents" :key="index"
    >
      <div>
      authors : {{i.authors}} <br>      
      datetime : {{i.datetime}} <br>
      price :  {{i.price}} <br>
      title : {{i.title}}
      </div>
      <div>
        -------------------------------------
      </div>
    </div>

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
