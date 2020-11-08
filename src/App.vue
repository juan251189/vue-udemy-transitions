<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <br>
    <button @click="selected=!selected">Click me </button>



    <transition name="fade">
      <p class="sign" v-if="selected">oiiii</p>
    </transition>
    <transition name="slide" type="transition">
      <p v-if="selected" class="sign">{{text | capitalized}}</p>

    </transition>

  </div>
</template>

<script>

export default {
  name: 'App',
  data(){
    return{
      selected:true,
      text:'hi there'
    }
  },
  components: {

  },
  filters:{
    capitalized:function(value){
      return value.toUpperCase();
    }
  }

}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.sign{
  width: 80%;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
  background-color: #2e26a4;
  margin:20px auto;
  color:#ddd9e3;
  padding: 20px;
  font-size: 2rem;
}



.fade-enter .fade-leave{
  opacity: 0;
}


.fade-enter-active{
  opacity: 1px;
  transition: .5s;
}
.fade-leave-active{
  transition: opacity .5s;
  opacity: 0;
}
.slide-enter {
  opacity: 0;
  transition: 2s;
}
.slide-leave{

}

.slide-enter-active{
  animation: slide-in 1s forwards;
  transition: opacity .5s;
}

.slide-leave-active{
  animation: slide-out 1s ease-out forwards;
  transition: opacity .5s;
  opacity: 0;
}


@keyframes slide-in {
  from{
    transform: translateY(20px);
    width: 100%;
  }
  to{
    transform: translateY(0);
    width: 80%;
  }
}


@keyframes slide-out {
  from{
    transform: translateY(0);

  }
  to{
    transform: translateY(20px);

  }
}
</style>
