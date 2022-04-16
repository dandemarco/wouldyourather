<!--LAB: A WouldYouRatherQuestion component displays a question, and two radio buttons, one for each answer.-->

<template>
  <div class="wyr">
    <h2>Would you rather...</h2>

    <h3>{{question}}</h3>

    <!-- Make a radio button input
    Use v-model to send the data from this input to the "choice" in data() 
    Use v-bind to bind the data to "answer1" in props
    Use v-on to listen for when the input changes, and call the "choiceMade" method-->
    <input type="radio" 
    v-model="choice" 
    v-bind:value="answer1"
    v-on:change="choiceMade"
    ><label>{{answer1}}</label>

    <input type="radio" 
    v-model="choice" 
    v-bind:value="answer2"
    v-on:change="choiceMade"
    ><label>{{answer2}}</label>
    
  </div>
</template>

<script>
export default {
  name: 'WouldYouRatherQuestion',
  props: {
    question: String,
    answer1: String,
    answer2: String,
  },
  data() {
    return {
      choice: ''
    }
  },
  methods: {
    //LAB: When the user selects a choice for each question, the WouldYouRatherQuestion component should emit a message to its parent. 
    choiceMade() {
      this.$emit('answer-changed', this.choice)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

h3 {
  margin: 40px 0 0;
}

.wyr {
  border: 2px black solid;
  font-family:'Courier New', Courier, monospace;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  background-color: aquamarine;
}


</style>
