<template>
  <div class="sample">
    <h1>Test</h1>

    <div class="qa" v-if="!isAnswer">
      <div class="question" v-for="item in items" :key="item.id">
        <p>Q{{ item.id }}</p>
        <p>{{ item.question }}</p>
        <div class="answers">
          <label v-for="(answer, id) in item.answer">
            <input type="radio" :value="id" v-model="item.select" />
            {{ answer }}
          </label>
        </div>
        <p>{{ item.select }}</p>
      </div>
      <button @click="onAnswer">Commit</button>
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
  </div>
</template>

<script>
export default {
  name: "Sample",
  data() {
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
      ],
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
</style>
