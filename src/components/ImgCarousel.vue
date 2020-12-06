<template>
  <div class="carousel-item align-self-start"
  :class="active">
    <img
      :src=img 
      :alt=alter
      class="w-50 d-inline col align-self-start "
      
    />
    <img
      :src=img2 
      :alt=alter2
      class="w-50  d-inline col align-self-start "
      
    />
    
  </div>
</template>

<script>
export default {
    props: {
    alter: String,
    img: String,
    alter2: String,
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