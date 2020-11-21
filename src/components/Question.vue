<template>
<div id="question" class="row ">
  <div class="col-12 question-title">{{question.Question}}</div>

  <div class="col-6 question-options" v-for="(option,i) in question.answers" :key="i">
    <transition name="selectedClass">
      <button class="btn btn-primary btn-option" @click="selected=option" :style="selected ===option ? 'background:linear-gradient(to right,#a78419,#dbc534)' : null">
        <span class="question-option-header">{{i}}:</span>
        <div class="option-item">{{option}}</div>
      </button>
    </transition>
  </div>
  <!--
    <button class="btn btn-primary" @click="submit($event)" value="a">{{question.answers.a}}</button></div>

    <div class="col-6"><span class="question-option">B)</span>
      <button class="btn btn-primary" @click="submit($event)" value="b">{{question.answers.b}}</button></div>

      <div class="col-6"><span class="question-option">C)</span>
        <button class="btn btn-primary" @click="submit($event)" value="c">{{question.answers.c}}</button></div>

        <div class="col-6"><span class="question-option">D)</span>
          <button class="btn btn-primary" @click="submit($event)" value="d">{{question.answers.d}}</button>
-->
  <button class="btn btn-info submit" @click="submit">Submit</button>
</div>
</template>
<script>
export default {

  data: () => ({
    selected: "",
    result: ''
  }),
  props: ['question'],
  methods: {
    submit() {
      let value = this.selected;
      if (value == this.question.solution) {
        this.result = 'correct';
        this.$emit('scored');
        alert("Excelent")
      } else {
        alert("keep trying")
      }

    },
    selectedClass() {
      return 'flash'
    }
  }
}
</script>
<style lang="css">

#question{
  border:1px solid lightgrey;
  margin:0px;
  padding: 0px;
}

.question-options button{
  margin-bottom: 30px;
  width: 150px;
  border-radius: 32px;
}
.question-option-header{
  font-size: 1.2em;
  font-weight: 700;
  position: relative;
  bottom: 2px;
  left:10px;
  float: left;
}

.question-title{
  width: 100%!important;
padding: 0px;
margin-bottom: 30px;;
  border:1px solid lightgrey;
}

.option-item{
  display: inline;
width: 100%;
  text-align: left;
}

.submit{
  display: flex;
  justify-content: flex-end;
  align-items: flex-end;
}


.flash-enter-active{
  background-color: red;
}

</style>
