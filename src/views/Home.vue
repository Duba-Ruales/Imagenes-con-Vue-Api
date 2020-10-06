/* etiqueta 1 */
<template>
<nav
    class="navbar navbar-expand-lg navbar-light color scrolling-navbar fixed-top bg-warning"
  >
    <div class="container m-2 font-weight-bolder ">
      <router-link to="/"> <h5> VOLVER </h5> </router-link>
    </div>
  </nav>

  
  <div class="container">
    <!-- ROW 1 -->
    <div class="row">
      <div class="col-12"> <br><br><br><br>
        <h2 class="text-center"> <b>CENTRO DE IMAGENES </b> </h2> <hr>
      </div>
    </div>

    <!-- ROW 2 -->
    <div class="row">
      <div class="col-12 col-sm-6 col-md-3" v-for="imagen in imagenes" :key="imagen.id">
        <Imagen :imagen = "imagen" />
      </div>
    </div>
  </div>
</template>

/* etiqueta 2 */
<script>
import Imagen from '../components/imagen';

export default {
  
  name: "Home",
  components: { Imagen },
  data() {
    return {
      imagenes: [],
    };
  },

  mounted() {
    fetch("https://api.jeisontech.dev/api/images", {
      method: "GET" /* tambien se puede usar este metodoc get, juntos */,
    })
      .then((res) => res.json())
      .then((data) => {
        this.imagenes = data;
      });
  },


  /* beforeCreate(){
    console.log("beforeCreate")
  },
  created(){
    console.log("Created")
  },
  beforeMount(){
    console.log("beforeMount")
  },
  mounted(){
    console.log("mounted")
  } */
  
};
</script>

/* etiqueta 3 */
<style>

h1 {
  font-size: 25px; /* tamaño de texto imagenes */
}

h1 {
  background-color: rgba(0, 0, 0, 0.781);
  color: white;
}

</style>
