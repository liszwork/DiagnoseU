<template>
  <v-container fluid>
    <v-card class="question" v-for="item in items" :key="item.id" color="#AACCFF">
      <v-card-title>Q{{ item.id }}: {{ item.question }}</v-card-title>
      <v-card-actions>
        <v-radio-group v-model="item.select">
          <v-radio v-for="(answer, id) in item.answer" :key="answer" :label="answer" :value="id"></v-radio>
        </v-radio-group>
      </v-card-actions>
    </v-card>
    <v-btn
      class="commit-button"
      x-large
      :ripple="{ center: true }"
      color="primary"
      @click="onAnswer"
    >Commit</v-btn>
  </v-container>
</template>

<script>
export default {
  name: "Sample",
  props: [
    'items',
  ],
  data() {
    return {
    };
  },
  methods: {
    onAnswer(event) {
      this.$parent.isAnswer = isOK;
      var isOK = true;
      for (let i = 0; i < this.items.length; i++) {
        const item = this.items[i];
        if (item.select < 0) {
          isOK = false;
          break;
        }
      }
      // this.$parent.isAnswer = isOK;
      // 親へ通知
      this.$emit('commit');
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
