<template>
  <nav
    class="navbar navbar-expand-lg navbar-light color scrolling-navbar fixed-top bg-warning"
  >
    <div class="container m-4 font-weight-bolder "></div>
  </nav>

  <div class="container  ">
    <div class="container mt-5 ">
      <div class="row">
        <div class="col-12">
          <br>
          <h2 class="text-center mt-5"> <b> MENÚ PRINCIPAL </b> </h2><hr>

    <!-- Seleccionar imagen de Desktop  -->
          <input
            class="btn btn-primary btn-block rounded-pill"
            type="file"
            @change="onFileSelected"
            oninput="pic.src=window.URL.createObjectURL(this.files[0])" />
          <br>
          

          <!-- Mostrar Previsuaizacion tañaño fijo -->
          <div class="preview">
            <img id="pic" />
          </div><br>

          <!-- Agregar imagen -->
          <button class="btn btn-success btn-block rounded-pill" @click="onUpload">
            <b>Agregar Imagen</b>
          </button>
          

          <br />
          <!--  MOSTRAR IMAGENES -->
          <li class="btn btn-warning font-weight-bolder btn-block rounded-pill">
            <router-link to="/Home" id="nourl"> <b>MOSTRAR IMAGENES</b> </router-link>
          </li>
        </div>
      </div>
    </div>

    <!-- ROW 2 -->
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "Index",
  data() {
    return {
      selectedFile: null,
    };
  },
  methods: {
    onFileSelected(event) {
      this.selectedFile =
        event.target.files[0]; /* Array para contener los resultados */
    },
    onUpload() {
      const fd = new FormData();
      fd.append("url", this.selectedFile, this.selectedFile.name);
      axios.post("https://api.jeisontech.dev/api/images/", fd).then((res) => {
        console.log(res);
      });
    },
  },
};
/* ------------------- */
</script>

<style>
b {
  color: rgb(0, 0, 0);
}

#nourl{
text-decoration: none;
}
.preview {
  display: flex;
  justify-content: center;
  align-items: center;
}

.preview img {
  max-width: 300px;
  max-height: 300px;
}

html,
body {
  height: 100%;
  margin: 0;
  padding: 0;
}
body{
 
  margin: 0;
  padding: 0;
  display: flex;
  justify-content: center;
  /* align-items: center; */
  /* min-height: 100vh; */
  background: #c5ccdd;
  font-family: sans-serif;
}
</style>
