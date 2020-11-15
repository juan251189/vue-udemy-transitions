<template>
<div id="question" class="row ">
  <div class="col-12 question-title">{{question.Question}}</div>

  <div class="col-6"><span class="question-option">A)</span>
    <button class="btn btn-primary" @click="submit($event)" value="a">{{question.answers.a}}</button></div>

    <div class="col-6"><span class="question-option">B)</span>
      <button class="btn btn-primary" @click="submit($event)" value="b">{{question.answers.b}}</button></div>

      <div class="col-6"><span class="question-option">C)</span>
        <button class="btn btn-primary" @click="submit($event)" value="c">{{question.answers.c}}</button></div>

        <div class="col-6"><span class="question-option">D)</span>
          <button class="btn btn-primary" @click="submit($event)" value="d">{{question.answers.d}}</button></div>

</div>
</template>
<script>
export default {

  data: () => ({

  }),
  props: ['question'],
  methods: {
    submit(value) {
      var answer = value.target.value;
      console.log(typeof(answer));
      if(answer===this.question.solution){
        alert("great Juan you did it")
      }
      else{
        alert("you better grap the next plain and go and visit colombia")
      }

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

#question button{
  margin-bottom: 30px;
  width: 150px;
}
.question-option{
  font-size: 1em;
  font-weight: 700;
  position: relative;
  bottom: 10px;
  right: 5px;
}

.question-title{
  width: 100%!important;
padding: 0px;
margin-bottom: 30px;;
  border:1px solid lightgrey;
}



</style>
