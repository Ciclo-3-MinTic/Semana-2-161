<template>
  <div
    class="card px-2 col-12 bg-transparent border-0 "
    v-bind:class="Boots"
  >
    <img v-bind:src="img" class="img-thumbnail img-fluid foto" :alt="name" />
    <div class="p-0">
      <table class="table table-striped  mb-2 p-0 ">
        <tbody>
          <tr class="namet p-0 m-0  row align-items-center">
          <h5 class="text-center user-select-all h4 p-0 m-0">
            {{ name }}
          </h5>
          </tr>
          <tr class="typet  text-center">
            <h6 class="card-subtitle text-light  mt-1 ">
              {{ type }}
            </h6>
          </tr>
          <tr class="desct ">
           
              <p
                class="mb-0 text-justify  m-0 p-2 align align-bottom font-weight-bolder"
              >
                {{ desc }}
              </p>
           
          </tr>
        </tbody>
      </table>
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
    Boots: String,
  },
};
</script>

<style scoped>
.namet {
  height: 15vh;
}
.typet {
  height: 8vh;
}
.desct {
  height: max-content;
}
</style>


