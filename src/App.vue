<template>
<div id="app">
<button class="btn btn-score btn-primary" @click="scoreShow=!scoreShow">Score</button>
  <div class="container">
    <div class="row">
      <div class="col-12">
        <h1>The Super Quiz</h1>
      </div>
    </div>

<transition name="fade">
      <app-score v-if="scoreShow"></app-score>
</transition>


      <component @score="scoreCount(value)" :index="index" :question="currentQuestion"

      :is="submitted">
    </component>

  </div>


</div>
</template>

<script>
import Answer from './components/Answer.vue'
import Question from './components/Question.vue'
import Score from './components/Score.vue'
export default {
  name: 'App',
  data() {
    return {
      submitted: 'app-question',
      index:0,
      currentQuestion:{},
      total:0,
      score:0,
      scoreShow:false,
      questions: [{
        Question: "Whats the capital of Colombia",
        answers: {
          a: 'Medellin',
          b: 'Cartagena',
          c: 'Bogota',
          d: 'Cali',

        },
        solution:'Bogota'
      },
      {
        Question: "What's 45 +20",
        answers: {
          a: 35,
          b: 42,
          c: 37,
          d: 44,

        },
        solution:'c'
      },
      {
        Question: "What's 80 +11",
        answers: {
          a: 35,
          b: 42,
          c: 37,
          d: 44,

        },
        solution:'c'
      }
    ]

    }},
    methods:{
      scoreCount(v){

          alert(v);
      }
    },
    components: {
        appAnswer: Answer,
        appQuestion: Question,
        appScore: Score

      },

      filters: {
        capitalized: function(value) {
          return value.toUpperCase();
        }
      },
      created() {
        //do something after creating vue instance
        this.currentQuestion=this.questions[this.index];
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

body{
  background-image:
}

.sign {
  width: 80%;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
  background-color: #2e26a4;
  margin: 20px auto;
  color: #ddd9e3;
  padding: 20px;
  font-size: 2rem;
}
.btn-score{
  border-radius: 1px 20px 20px 1px;
  position: fixed;
  left:1px;
  z-index: 2;
}

.fade-enter-active, .fade-leave-active {
  transition: opacity .4s;
}
.fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
  opacity: 0;
}

.slide-enter {
  opacity: 0;
  transition: 2s;
}

.slide-leave {}

.slide-enter-active {
  animation: slide-in 1s forwards;
  transition: opacity .5s;
}

.slide-leave-active {
  animation: slide-out 1s ease-out forwards;
  transition: opacity .5s;
  opacity: 0;
}


@keyframes slide-in {
  from {
    transform: translateY(20px);
    width: 100%;
  }

  to {
    transform: translateY(0);
    width: 80%;
  }
}


@keyframes slide-out {
  from {
    transform: translateY(0);

  }

  to {
    transform: translateY(20px);

  }
}
</style>
