<template>
  <v-container fluid>
    <v-card class="question" v-for="item in items" :key="item.id" color="#AACCFF">
      <v-card-title>Q{{ item.id }}: {{ item.question }}</v-card-title>
      <p class="error-text" v-if="validation(item.select)">入力してください。</p>
      <v-card-actions>
        <v-radio-group v-model="item.select">
          <v-radio v-for="(answer, index) in answers" :key="answer" :label="answer" :value="index"></v-radio>
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
  name: "SMScaleForm",
  props: [
    "items",
    "answers",
    "point",
  ],
  computed: {
  },
  data() {
    return {
      radioConstant: {
        default: -1,
        error: -2,
      },
    };
  },
  methods: {
    onAnswer(event) {
      // 結果に進んでもいい？
      var isOK = true;
      var sumPt = 0;
      for (let i = 0; i < this.items.length; i++) {
        const item = this.items[i];
        if (item.select < 0) {
          // 発見したら留まる&対象要素をエラーにする
          isOK = false;
          item.select = -2;
        }
        sumPt += (item.select + 1);
      }
      // this.point = sumPt;
      // 親に通知
      if (isOK) {
        this.$emit('commit', sumPt);
      }
    },
    validation(select) {
      // ラジオボタンエラー判定
      return (select == -2);
    },
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.question {
  margin-top: 10px;
  margin-bottom: 10px;
  padding: 10px 10px 10px 10px;
}
.commit-button {
  text-align: center;
  margin-top: 10px;
}
.error-text {
  color: red;
}
</style>
