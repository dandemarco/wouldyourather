<template>
<div id=app>

  <h1>Would you rather?</h1>

  <!-- LAB: In App.vue, use v-for to display a list of WouldYouRatherQuestion components, one for each question. -->
  <would-you-rather-question v-for="entry in questions" 
  v-bind:key="entry.id"
  v-bind:question="entry.question"
  v-bind:answer1="entry.answer1" 
  v-bind:answer2="entry.answer2" 
  v-on:answer-changed="answerChanged">
  </would-you-rather-question>

  <!--LAB: App.vue should display a component with a list of all of the user's choices for each question in an li element.-->
  <li v-for="answer in answerBank" 
  v-bind:key="answer">{{answer}}</li>

</div>
</template>

<script>
//import data from WouldYouRatherQuestion component
import WouldYouRatherQuestion from './components/WouldYouRatherQuestion.vue'

export default {
  name: 'App',
  components: {
    WouldYouRatherQuestion,
  },
  data() {
    return {

      //App.vue should include a questions array. Each question object should have a unique ID, question, and two answers
      questions: [
        {
          id: 0,
          question: "...live in a house shaped like a triangle or a circle?",
          answer1: "Triangle House",
          answer2: "Circle House",
        },
        {
          id: 1,
          question: "...have the ability to fly or be invisible?",
          answer1: "Fly",
          answer2: "Invisibility",
        },
        {
          id: 2,
          question: "...it always be sunny when you wake up or stay brighter later in the evening?",
          answer1: "Sunny when I wake up",
          answer2: "Brighter in the evening",
        },
      ],
      userSelectionMessage: "",
      answerBank: [],
    }
  },
  methods: {
    //LAB: The parent should display the user's selections for each question.
    answerChanged(choice) {
      this.userSelectionMessage = `You chose ${choice}.`
      this.answerBank.push(this.userSelectionMessage)
      console.log(this.answerBank)
    },
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
</style>
