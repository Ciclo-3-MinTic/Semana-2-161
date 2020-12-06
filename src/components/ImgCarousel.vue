<template>
  <div class="carousel-item align-self-start"
  :class="active">
    <img
      :src=img 
      class="w-50 d-inline col align-self-start "
      
    />
    <img
      :src=img2 
      class="w-50  d-inline col align-self-start "
      
    />
    
  </div>
</template>

<script>
export default {
  name:"imgCarousel",
    props: {
    
    img: String,
    
    img2: String,
    active: String,
    
  },
};
</script>

<style scoped>
.carousel-item{
  height: 200px;
}
img{
  vertical-align: top;
}

</style>