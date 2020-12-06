<template>
  <div
    class="card px-2 col-12 bg-transparent border-0 "
    v-bind:class="clss"
  >
    <img v-bind:src="member.image" class="img-thumbnail img-fluid " :alt="member.nombre " />
    <div class="p-0">
      <table class="table table-striped  mb-2 p-0 ">
        <tbody>
          <tr class="typet  row align-items-center px-4 py-2">
          
            <h6 class=" text-light  mt-1 text-center col-11">
               {{ member.codigo }}. {{ member.rol }}
            </h6>
          </tr>
          <tr class="namet p-0 m-0  row align-items-center text-center">
          
          <h5 class="text-center  h4 p-0 m-0">
            {{ member.nombre }}
          </h5>
       
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
  height: 9vh;
}
.typet {
  height: 9vh;
}
.desct {
  height: max-content;
}
</style>


