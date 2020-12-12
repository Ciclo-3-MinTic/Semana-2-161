<template>
<div v-if="this.dataText.length >= 4">
    <div  class="row justify-content-center">
  <div class="card mb-0 mt-0 col-12 col-md-6  bg-transparent border-0"
    v-for="(data, index) in this.dataText"
          :key="index"
          >
    <div class="row justify-content-center">
      <div class="col-4 align-items-center justify-content-center d-flex ">
        <img :src="data.thumbnail" class="img-fluid " :alt="data.title" >
      </div>
      <div class="col-8 ">
        <div class="card-body pl-0 ">
          <h5 class="card-title text-center h4">{{data.title}}</h5>
          <p class="card-text text-justify rounded-top bg-light px-2" v-html ="data.content_short">
            
          </p>
          <div class="d-flex justify-content-end ">
            <a type="button" class="btn-sm btn-light" target="_blank" v-bind:href="data.url_download">Info</a>
          </div>
        </div>
      </div>
    </div>
  </div>
  </div>
  </div>
</template>

<script>
export default {
  name: "BooksApi",

  data(){
    return{
      dataText: [],
    };
  },

 async beforeCreate(){
  const getNews = async () => {
      let urlText =
        "https://www.etnassoft.com/api/v1/get/?any_tags=[html,css,javascript]&order=newest&num_items=4&lang=spanish";
      const resultText = await fetch(urlText, {
        method: "GET",
      });

      const result = await resultText.json();

      if (result.length >= 4) {
        this.dataText = result;

      /*   console.log(this.dataText); */
      }
    };

    await getNews();

 }
 
 
};

</script>

<style scoped>
img{
  vertical-align: middle;
  
}
</style>
