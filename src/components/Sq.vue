<template>
  <a :href="items.web" class="tile" v-for="items in web" :key='items'>
    <div class="tile-icon" :key="items">
      <img :src="items.addr">
    </div>
    <div class="tile-tilte" :key="items">
      <span>{{ items.name }}</span>
    </div>
  </a>
  <div class="tile"  @click="xs()" v-show=tj>
    <div class="tile-icon">
      <div id="tj"></div>
    </div>
    <div class="tile-tilte">
      <span>添加快捷方式</span>
    </div>
  </div>
  <div id="adds" v-show=xxss>
    <div id="addn">创建快捷方式</div>
    <div id="addweb">
      <p>名称</p>
      <input class="addi" id="add1" type="text" placeholder="网站名称">
      <p>网址</p>
      <input class="addi" id="add2" type="text" placeholder="eg:请加上请求头，可能需要富强才能显示图标">
    </div>
    <div id="addok">
      <button @click="closee()">取消</button>
      <button @click="fav()">完成</button>
    </div>
  </div>
  <div id="hh" v-show=xxss></div>
</template>

<script>
export default {
  mounted() {
    if (window.localStorage.getItem('sj') === null) {
      var nr = [
        {
          addr: 'https://t2.gstatic.com/faviconV2?client=SOCIAL&type=FAVICON&fallback_opts=TYPE,SIZE,URL&url=https://github.com&size=32',
          name: 'Github',
          web: 'https://github.com'
        },
        {
          addr: 'https://t2.gstatic.com/faviconV2?client=SOCIAL&type=FAVICON&fallback_opts=TYPE,SIZE,URL&url=https://www.youtube.com&size=32',
          name: 'Youtube',
          web: 'https://www.youtube.com'
        }
      ]
      window.localStorage.setItem('sj',JSON.stringify(nr))
    }
    this.web = JSON.parse(window.localStorage.getItem('sj'))
    console.log(this.web.length)
    if (this.web.length == 10) {
      this.tj = false
    }
  },
  data() {
    return{
       web: [],
      xxss: false,
      tj: true
    }
  },
  methods:{
    fav(){
      let wicon = 'https://t2.gstatic.com/faviconV2?client=SOCIAL&type=FAVICON&fallback_opts=TYPE,SIZE,URL&url=%s&size=32'
      let nm = document.getElementById('add1').value
      let addrt = document.getElementById('add2').value
      let addrc = wicon.replace(/%s/,addrt)
      this.web.push({
        addr: addrc,
        name: nm,
        web: addrt
      })
      window.localStorage.setItem('sj',JSON.stringify(this.web))
      this.xxss = false
    },
    xs(){
      console.log('点击xs')
      this.xxss = true
      console.log(this.web)
    },
    closee(){
      console.log('点击closee')
      this.xxss = false
    }
  }
}
</script>

<style>
.tile{
  width: 112px;
  height: 112px;
  margin: 0;
  display: flex;
  flex-direction: column;
  --column-count: 5;
  --row-count: 2;
  align-items: center;
  border-radius: 4px;
  text-decoration: none;
}
.tile:hover{
  background-color: rgba(32 , 33, 36, .1);
}
.tile-icon{
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  width: 48px;
  height: 48px;
  border-radius: 50%;
  margin-top: 16px;
  background-color: rgba(241, 243, 244, 1);
}
img{
  width: 24px;
  height: 24px;
}
.tile-tilte{
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  background-color: white;
  color: black;
  border-radius: 18px;
  width: 88px;
  height: 32px;
  line-height: 16px;
  margin-top: 6px;
  padding: 2px 8px;
}
#tj{
  background-image: url('../assets/add.svg');
  height: 24px;
  width: 24px;
}
#adds{
  background-color:aliceblue;
  width: 512px;
  position: absolute;
  z-index: 3;
  top: 50%;
  left: 50%;
  -webkit-transform: translate(-50%, -50%);
  border-radius: 8px;
}
#addn{
  padding: 20px 20px 16px 20px;
  margin: 0;
}
#addweb{
  padding: 0 20px;
  margin: 0;
}
#addok{
  padding: 24px 16px 16px 16px;
  margin: 0;
  text-align: right;
}
#addok button{
  background-color: aliceblue;
  border-color: #b6f7fa;
  width: 50px;
  height: 32px;
  margin: 3px;
  border-radius: 7px;
  box-shadow: 0 8px 16px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19);
}
.addi{
  background-color: rgba(224, 224, 224, 0.586);
  border-bottom-width: 2px;
  border-color: rgb(182, 247, 250);
}
#hh{
  position: absolute;
  top: 0;
  width: 100%;
  height: 100%;
  background:rgba(0, 0, 0,70%);
  z-index: 1;
}
</style>