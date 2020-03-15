<template>
  <div class="sample">
    <h1>Test Question</h1>
    <div id="question">
      <ul>
        <li v-for="item in questions" :key="item.text">
          {{ item.id }} {{ item.text }}
        </li>
      </ul>

      <button @click="onAnswer">Commit</button>
    </div>
    <div id="answer" v-show="isAnswer">
      <p>answer</p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Sample',
  data () {
    return {
      isAnswer: false,
      questions: [
        { id: "1", text: "item1" },
        { id: "2", text: "item2" },
        { id: "3", text: "item3" },
        { id: "4", text: "item4" },
      ]
    }
  },
  methods: {
    onAnswer(event) {
      this.isAnswer = true;
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
