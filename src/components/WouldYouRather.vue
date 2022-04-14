<template>
  <div class="wyr">
    <h2>Please make your choice</h2>

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
  name: 'WouldYouRather',
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
    //this "emits" an answer change event back to App.vue, telling it that the user selected an answer
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
}
</style>
