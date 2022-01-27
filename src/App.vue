<template>
  <div id="gradient"></div>
  <Search></Search>
  <div id="bk">
    <Sq></Sq>
  </div>
</template>

<script>
import Search from './components/Search.vue'
import Sq from './components/Sq.vue'

export default {
  name: 'App',
  components: { 
    Search,
    Sq,
  }
}
</script>

<style>
html {
  padding: 0;
  margin: 0;
  height: 100%;
  width: 100%;
  background-image: url(./assets/fb.png);
  background-position: center;
  background-repeat: no-repeat no-repeat;
  background-size:initial;

}
body{
  width: 100%;
  height: 100%;
  padding: 0%;
  margin: 0%;
  font-size: 81.25%;
  font-family: sans-serif,Roboto, 'Segoe UI',Arial,'Microsoft Yahei';
}
a{

}
#app{
  width: 100%;
  height: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
}
#gradient {
  position: absolute;
  width: 100%;
  height: 100%;
  background: radial-gradient(transparent 50%, black),
      linear-gradient(transparent, black);
  opacity: .2;
  z-index: 1;
}
#bk{
  /* background-color: cadetblue; */
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: center;
  flex-wrap: wrap;
  width: 573px;
  z-index: 2;
}
</style>
