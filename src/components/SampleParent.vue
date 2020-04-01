<template>
  <v-content class="sample">
    <v-container fluid>
      <h1>Sample</h1>

      <Sample v-if="!isAnswer" :items="items" @commit="toResult" />
      <SampleResult v-if="isAnswer" :items="items" @back="toQuestion" />
    </v-container>
  </v-content>
</template>

<script>
import Sample from "./Sample";
import SampleResult from "./SampleResult";

export default {
  name: "SampleParent",
  components: {
    Sample,
    SampleResult
  },
  data: () => {
    return {
      isAnswer: false,
      items: [
        {
          id: 1,
          question: "Q1 text...",
          answer: ["a1", "b1"],
          select: -1
        },
        {
          id: 2,
          question: "Q2 text...",
          answer: ["a2", "b2", "c2"],
          select: -1
        }
      ]
    };
  },
  methods: {
    toResult() {
      this.isAnswer = true;
    },
    toQuestion() {
      this.isAnswer = false;
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.question {
  margin: 10px;
}
.commit-button {
  text-align: center;
}
</style>
