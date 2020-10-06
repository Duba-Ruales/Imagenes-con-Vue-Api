<template>
  <div class="card">
    <img class="img-fluid img" :src="imagen.url" alt="" />
    <!-- con los dos puntos (:) hace DATA BAIDING -->
    <div class="card-body">
      <h5 class="card-title">{{ imagen.created_at }}</h5>
      <!-- guarda la fecha de creacion de la imagen -->
    </div>
  </div>
</template>

<script>
export default {
  name: "Imagen",
  props: ["imagen"]
};
</script>


<style>
    .img {
  height: 200px;
  object-fit: cover;
  filter: brightness(70%);
}
.img:hover {
  filter: brightness(100%);
}
</style>