<template>
  <v-container fluid>
    <h2>result</h2>
    <p>Your selections</p>
    <v-card class="result" color="#AACCFF">
      <h3>あなたは {{ resultMessage }}</h3>
    </v-card>
    <v-card class="detail" color="#AACCFF">
      <h3>あなたが選択した内容</h3>
      <div v-for="item in items" :key="item.id">
        <v-card-title>Q{{ item.id }}: {{ item.question }}</v-card-title>
        <v-card-text>
          <v-list-item-subtitle class="text--primary">{{ item.select }} : {{ answers[item.select] }}</v-list-item-subtitle>
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
  name: "SMScaleResult",
  props: ["items", "answers", "point"],
  data() {
    return {
      resultMessage: "",
    };
  },
  methods: {
    onBack(event) {
      this.items.forEach(item => {
        item.select = -1;
      });
      // 子→親へ通知
      this.$emit("back");
    }
  },
  mounted() {
    if (this.point <= 32) {
      this.resultMessage = "空気を読むのが苦手です。"
    }
    else {
      this.resultMessage = "空気を読むのが得意です。"
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
