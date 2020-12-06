<template>
  <div class="card mb-0 mt-0 col-12 col-lg-6  bg-transparent border-0">
    <div class="row justify-content-center">
      <div class="col-4 align-items-center justify-content-center d-flex ">
        <img :src=img class="img-fluid " :alt="title" />
      </div>
      <div class="col-8 ">
        <div class="card-body pl-0 ">
          <h5 class="card-title text-center h4">{{title}}</h5>
          <p class="card-text text-justify rounded-top bg-light px-2" v-html ="desc">
            
          </p>
          <div class="d-flex justify-content-end ">
            <a type="button" class="btn-sm btn-light" target="_blank" v-bind:href=link>Info</a>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    title: String,
    desc: String,
    img: String,
    link: String,
  },
};
</script>

<style scoped>
img{
  vertical-align: middle;
  
}
</style>
