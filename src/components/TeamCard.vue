<template>
  <div
    class='card justify-content-center col-12 align-items-center justify-content-center d-flex'
    v-bind:class=Boots
  >
    <img  v-bind:src=img  class="img-fluid" alt="..."/>
    <div class="card-body">
      <h5 class="card-title text-center user-select-all">{{name}}</h5>
      <h5 class="card-subtitle text-muted text-center">{{type}}</h5>
      <p class="card-text text-justify">
        {{desc}}
      </p>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    name: String,
    type: String,
    desc: String,
    img: String,
    Boots: String
  },
};
</script>


