<template>
  <div id="app">
    <router-view/>
  </div>
</template>

<script>
export default {};
</script>

<style>
* {
  padding: 0;
  margin: 0;
}
body {
  height: 100%;
  background: linear-gradient(rgba(0, 0, 0, 0.9), rgba(0, 0, 0, 0.9)),
    url(./assets/bg.jpg) no-repeat center;
  background-attachment: fixed;
  background-size: cover;
  color: #fff;
}

.btn {
  background-color: #df292d !important;
  color: #fff !important;
  font-weight: 600 !important;
}

.form-control {
  border-color: #00abc127 !important;
  height: 45px !important;
}
.form-control:focus {
  box-shadow: none !important;
}
img {
   border-radius: 5px;
  opacity: 0.5;
  background: linear-gradient(rgba(0, 0, 0, 0.85), rgba(0, 0, 0, 0.85));
  border: 1px solid #fff;
}
p {
  font-size: 13px !important;
  font-weight: 600;
}
h1 {
  color: #fff;
  font-weight: 700;
}
</style>
