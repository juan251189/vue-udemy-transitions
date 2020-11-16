<template>
<div id="question" class="row ">
  <div class="col-12 question-title">{{question.Question}}</div>

  <div class="col-6 question-options" v-for="(option,i) in question.answers" :key="i"
  >
<span class="question-option-header">{{i}})</span>
    <button class="btn btn-primary"

    @click="selected=option" :style="selected ===option ? 'background:linear-gradient(to right,#a78419,#dbc534)' : null">
      {{option}}
    </button>

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
<button class="btn btn-info submit" @click="submit" >Submit</button>
</div>

</template>
<script>
export default {

  data: () => ({
      selected:"",
      result:''
  }),
  props: ['question'],
  methods: {
    submit(){
        let value=this.selected;
        if(value==this.question.solution) {
          this.result='correct';
          alert("Excelent")
        }
        else{
          alert("keep trying")
        }

    },
    selectedClass(){
            return {backgroundColor:'red'}
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
}
.question-option-header{
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

.submit{
  display: flex;
  justify-content: flex-end;
  align-items: flex-end;
}


</style>
