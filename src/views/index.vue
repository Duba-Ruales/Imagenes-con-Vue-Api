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
          <br />
          <h2 class="text-center mt-5"><b> MENÚ PRINCIPAL </b></h2>
          <hr />


          <!-- Seleccionar imagen de Desktop  -->
          <span class="btn btn-primary btn-file btn-block rounded-pill mb-2">
            <i style='font-size:24px' class='fas'>&#xf382;</i>&nbsp; <!-- Icono de selecion imagen -->
            <b>SELECCIONAR IMAGEN</b> 
            <input
            class="btn btn-primary btn-block "
            type="file"
            @change="onFileSelected"
            oninput="pic.src=window.URL.createObjectURL(this.files[0])"
            
          />
          </span>


          <!-- Mostrar Previsuaizacion tañaño fijo -->
          <div class="preview">
            <img id="pic" />
          </div>
          <br />


          <!-- Agregar imagen -->
          <button
            class="btn btn-success btn-block rounded-pill"
            @click="onUpload"
          >
          <!-- <i class="material-icons">&#xe39d;</i> --> 
          <i class="material-icons " style='font-size:24px'>&#xe439;</i> &nbsp; <!-- icomo de add imagenes -->
            <b> AGREGAR IMAGEN</b>
          </button>

          <br>
          <!--  MOSTRAR IMAGENES -->
          <li class="btn btn-warning font-weight-bolder btn-block rounded-pill">
            <router-link to="/Home" id="nourl">
            <!-- <i class="material-icons">&#xe413;</i> -->
            <i class="material-icons " style='font-size:24px'>&#xe3b6;</i> &nbsp;<!-- icomo de imagenes -->
              <b>MOSTRAR IMAGENES</b>
            </router-link>
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
/* BOTON DE SELECCIONAR LAS IMAGENES */
.btn-file {
  position: relative;
  overflow: hidden;
}
.btn-file input[type="file"] {
  position: absolute;
  top: 0;
  right: 0;
  min-width: 100%;
  min-height: 100%;
  font-size: 100px;
  text-align: right;
  filter: alpha(opacity=0);
  opacity: 0;
  outline: none;
  background: rgb(255, 255, 255);
  cursor: inherit;
  display: block;
}

/* Color de letra de hipervinculo y URL */
b {
  color: rgb(17, 17, 17);
}
i {
  color: rgb(255, 255, 255);
}

#nourl {
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
body {
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
