<template>
  <div class="card mb-0 col-12 col-lg-6  ">
    <div class="row justify-content-center">
      <div class="col-3 align-items-center justify-content-center d-flex ">
        <img :src=img class="img-fluid" :alt="title" />
      </div>
      <div class="col-9">
        <div class="card-body pl-0">
          <h5 class="card-title text-center">{{title}}</h5>
          <p class="card-text text-justify" v-html ="desc">
            
          </p>
          <div class="d-flex justify-content-end">
            <a type="button" class="btn-sm btn-outline-info" target="_blank" v-bind:href=link>Info</a>
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
