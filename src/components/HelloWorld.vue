<template>
    <div id="main">
         <div class="koutbox1"><img id="slidingImg" src="~@/assets/img/时间刻度_10.png" alt=""></div> 
         <div class="eoutbox"><p id="slidingImgline"></p></div>
          <div class="koutbox2"><img  id="slidingImg2" src="~@/assets/img/时间刻度_10.png" alt=""></div> 
    </div>
</template>
<script>
let moment = require('moment');
export default {
  name: "HelloWorld",
 data() {
    return {
     
    }
  },
  mounted() {
    let that = this;
    that.LopTime();   
        setInterval(function() {
      var mindata = new Date().getHours() * 60 + new Date().getMinutes();
      if (mindata % 15 == 0) {
        that.LopTime();
        console.log(mindata)
      }
    }, 60000);     //在生命周期中调用LopTime（）方法
  },
  props: [''],
  computed: {},
  methods: {
    LopTime(){
      let timer=new Date()
      let hours=timer.getHours()
      let min=timer.getMinutes()
      let total=hours*60+min
     let localnum=parseInt(total/15)
      let Insetlinelocation = -234 + localnum*parseFloat(760/96);
       let Insetlinelocationline = 329 + localnum*parseFloat(760/96);
        document.getElementById('slidingImg').style.left = Insetlinelocation + 'px';
          document.getElementById('slidingImg2').style.left = Insetlinelocation + 'px';
           document.getElementById('slidingImgline').style.left = Insetlinelocationline + 'px';
      console.log(localnum)
    }
  }

};
</script>
<style  scoped>
#main {
  display: -webkit-box;
  display: -webkit-flex;
  display: -ms-flexbox;
  display: flex;
  flex-direction: column;
  flex-wrap: nowrap;
  justify-content: flex-start;
  align-items: center;
  width: 1128px;
 /*  height: 210px; */
  border: 1px #e4e4ec solid;
  margin: 50px auto;
  position: relative;
}
.koutbox1 {
  width: 1128px;
  height: 28px;
  border-bottom: 1px #e4e4ec solid;
  background-image: url("~@/assets/img/刻度02_03.png");
  background-repeat: no-repeat;
  background-position: 0px 3px;
  position: relative;
}
.koutbox2 {
  width: 1128px;
  height: 28px;
  border-top: 1px #e4e4ec solid;
  background-image: url("~@/assets/img/刻度02_03.png");
  background-repeat: no-repeat;
  background-position: 0px 3px;
}
img {
  position: relative;
  left: -234px;
}
.eoutbox {
  width: 1128px;
  height: 154px;
}
p {
  width: 1px;
  height: 154px;
  background-color: red;
  position: relative;
  top: -16px;
  left: 329px;
}
</style>


