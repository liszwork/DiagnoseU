<template>
  <v-container fluid>
    <!-- TODO: 診断結果の詳細 -->
    <p class="display-1">あなたは {{ resultMessage }}</p>
    <v-card class="detail" color="#AACCFF">
      <v-card-title class="title font-weight-black" color="#AACCFF">
        選択した内容
      </v-card-title>
      <!-- 選択内容の確認 -->
      <v-card class="card-inner" v-for="item in items" :key="item.id" color="#BBDDFF">
        <v-card-title class="subtitle-1">Q{{ item.id }}: {{ item.question }}</v-card-title>
        <v-card-text>
          <v-list-item-subtitle class="body-1	">{{ answers[item.select] }}</v-list-item-subtitle>
        </v-card-text>
      </v-card>
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
.detail {
  margin-top: 10px;
  margin-bottom: 10px;
  padding: 10px 10px 10px 10px;
}
.card-title {
  /* margin: 0 0 0 0; */
}
.card-inner {
  margin-top: 10px;
  margin-bottom: 10px;
}
</style>
