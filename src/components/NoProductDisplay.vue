<template>
  <div class="container1">
    <p class="inter-400">This product is unavailable to show</p>
    <button class="button3" @click="$emit('clickedNew')">Next Product</button>
  </div>
</template>

<script>
export default {
  name: 'NoProductDisplay',
  props:{
  },
}
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@100..900&display=swap');

.container1 {
  position: absolute;
  display: flex;
  flex-direction: column;
  top: 30%;
  width: 1034px;
  height: 580px;
  background-image: url('./src/assets/images/sad-face.png');
  background-repeat: no-repeat;
  background-position: center;
  background-color: white;
  border-radius: 15px;
  box-shadow: 0 4px 4px 0 rgba(0, 0, 0, 0.25);
  align-items: center;
  justify-content: center;
  padding-top: 20px;
  padding-bottom: 20px;
}

.background{
    display: flex;
    justify-content: center;
    position: absolute;
    top: 0px;
    width: 100vw;
    height: 584px;
    background-color: #D8D7D7;
}

.sadface{
  height: 500px;
  width: 1000px;
}

.inter-400{
  font-family: "Inter", sans-serif;
  font-size: 20px;
  font-weight: 400;
  font-style: normal;
}

.button3{
  width: 465px;
  height: 42px;
  background-color: white;
  font-family: "Inter", sans-serif;
  font-size: 20px;
  font-weight: 600;
  font-style: normal;
  border-color: black;
  border-width: 3px;
  border-radius: 4px;
  margin: 0;
}

</style>
