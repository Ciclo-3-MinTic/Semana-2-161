<template>
  <div
    class="card px-2 col-12 bg-transparent border-0 "
    v-bind:class="clss"
  >
    <img v-bind:src="member.image" class="img-thumbnail img-fluid " :alt="member.nombre " />
    <div class="p-0">
      <table class="table table-striped  mb-2 p-0 ">
        <tbody>
          <tr class="namet p-0 m-0  row align-items-center">
          <h5 class="text-center user-select-all h4 p-0 m-0">
            {{ member.nombre }}
          </h5>
          </tr>
          <tr class="typet  text-center">
            <h6 class="card-subtitle text-light  mt-1 ">
              {{ member.rol }}
            </h6>
          </tr>
          <tr class="desct ">
           
              <p
                class="mb-0 text-justify  m-0 p-2 align align-bottom font-weight-bolder"
              >
                {{ member.descripcion }}
              </p>
           
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script>
export default {
  name:"TeamCard",

  props: {
    member:{}

    
    
  },
  data(){
    return {
      clss: this.member.codigo>4?"col-md-4 col-lg":"col-md-6 col-lg"
      
    };
  },
 
}
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


