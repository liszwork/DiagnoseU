<template>
  <v-container fluid>
    <h2>result</h2>
    <p>Your selections</p>
    <v-card class="question" color="#AACCFF">
      <div v-for="item in items" :key="item.id">
        <v-card-title>Q{{ item.id }}: {{ item.question }}</v-card-title>
        <v-card-text>
          <v-list-item-subtitle
            class="text--primary"
          >{{ item.select }} : {{ item.answer[item.select] }}</v-list-item-subtitle>
        </v-card-text>
      </div>
    </v-card>
    <v-btn
      class="commit-button"
      x-large
      :ripple="{ center: true }"
      color="primary"
      @click="onBack"
    >Back</v-btn>
  </v-container>
</template>

<script>
export default {
  name: "SampleResult",
  props: [
    'items',
  ],
  data() {
    return {
      //
    };
  },
  methods: {
    onBack(event) {
      this.items.forEach(item => {
        item.select = -1;
      });
      // 子→親へ通知
      this.$emit('back');
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
