<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <br>
    <button @click="selected=!selected">Click me </button>


    <transition appear
    enter-active-class="animate__animated animate__backInDown"
    leave-active-class="animate__animated animate__bounce">
      <div class="alert alert-info" v-if="selected"
      >Hi there</div>
    </transition>

    <hr>
<br>
<select v-model="selectOption">
  <option value="fade">Fade</option>
  <option value="slide">Slide</option>
</select>

    <transition :name="selectOption" appear>
      <p class="sign" v-if="selected" appear>oiiii</p>
    </transition>
    <transition name="slide" type="transition" mode="out-in">
      <div v-if="selected" key="info" class="sign">{{text | capitalized}}</div>
      <div  class="alert alert-warning"
      v-else key="warning">This is some warning</div>

    </transition>


    <br>


  </div>
</template>

<script>

export default {
  name: 'App',
  data(){
    return{
      selected:true,
      text:'hi there',
      selectOption:''
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
