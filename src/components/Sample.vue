<template>
  <v-content class="sample">
    <h1>Test</h1>

    <div class="qa" v-if="!isAnswer">
      <v-card class="question" v-for="item in items" :key="item.id" color="#AACCFF">
        <v-card-title>Q{{ item.id }}: {{ item.question }}</v-card-title>
        <v-card-actions>
          <v-radio-group v-model="item.select">
            <v-radio
              v-for="(answer, id) in item.answer"
              :key="answer"
              :label="answer"
              :value="id"
            ></v-radio>
          </v-radio-group>
          <p>{{ item.select }}</p>
        </v-card-actions>
      </v-card>
      <v-btn class="commit-button" x-large :ripple="{ center: true }" color="primary" @click="onAnswer">Commit</v-btn>
    </div>

    <div class="result" v-if="isAnswer">
      <p>result</p>
      <p>Your selections</p>
      <div class="question" v-for="item in items" :key="item.id">
        <p>Q{{ item.id }}</p>
        <p>{{ item.question }}</p>
        <div class="answers">
          <p>{{ item.select }} : {{ item.answer[item.select] }}</p>
        </div>
      </div>
      <button @click="onBack">Back</button>
    </div>
  </v-content>
</template>

<script>
export default {
  name: "Sample",
  data() {
    return {
      valid: false,
      sex: true,
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
    onAnswer(event) {
      var isOK = true;
      for (let i = 0; i < this.items.length; i++) {
        const item = this.items[i];
        if (item.select < 0) {
          isOK = false;
          break;
        }
      }
      this.isAnswer = isOK;
    },
    onBack(event) {
      this.isAnswer = false;
      items.forEach(item => {
        item.select = -1;
      });
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
  background: blue;
}
</style>
