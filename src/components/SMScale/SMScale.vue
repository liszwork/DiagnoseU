<template>
  <v-content class="sample">
    <v-container fluid>
      <SMScaleForm
        v-if="!isAnswer"
        :items="items"
        :answers="answers"
        :point="point"
        @commit="toResult"
      />
      <SMScaleResult
        v-if="isAnswer"
        :items="items"
        :answers="answers"
        :point="point"
        @back="toQuestion"
      />
    </v-container>
  </v-content>
</template>

<script>
import SMScaleForm from "./SMScaleForm";
import SMScaleResult from "./SMScaleResult";

export default {
  name: "SMScale",
  components: {
    SMScaleForm,
    SMScaleResult
  },
  data: () => {
    return {
      isAnswer: false,
      point: 0,
      answers: [
        "全然当てはまらない", // 0 - 1pt
        "あまり当てはまらない",
        "やや当てはまる",
        "かなり当てはまる" // 3 - 4pt
      ],
      items: [
        {
          id: 1,
          question:
            "会話をしているとき、相手の表情のわずかな変化にも敏感になる。",
          select: -1
        },
        {
          id: 2,
          question: "相手の顔や目を見れば、その人の本当の気持ちを読み取ることができる。",
          select: -1
        },
        {
          id: 3,
          question:
            "誰かが自分に嘘をついても、表情やしぐさで嘘だと見抜くことができる。",
          select: -1
        },
        {
          id: 4,
          question:
            "目を見れば、自分が相手の気に障ることを言ったか気づくことができる。",
          select: -1
        },
        {
          id: 5,
          question:
            "相手が冗談を聞いて笑っていても、内心では反感を持っているか気づくことができる。",
          select: -1
        },
        {
          id: 6,
          question:
            "自分の直感力は、相手の気持ちや行いの原因を知るのにとても役立つ。",
          select: -1
        },
        {
          id: 7,
          question: "相手や状況に応じて自分の行動を変えるのが得意。",
          select: -1
        },
        {
          id: 8,
          question:
            "その場面でどのように振る舞えば良いか分かれば、それに応じて自分の行動を変えることができる。",
          select: -1
        },
        {
          id: 9,
          question:
            "自分が今いる場面で必要とされていることに応じて、自分の行動を変えることができる。",
          select: -1
        },
        {
          id: 10,
          question:
            "物事が自分のうまくいかないとき、すぐに他のやり方に切り換えることができる。",
          select: -1
        },
        {
          id: 11,
          question:
            "自分のためになると分かっているとき、体裁よく行動することができる。",
          select: -1
        },
        {
          id: 12,
          question:
            "まわりの人が望んでいることに応じて、自分の行動を変えることができる。",
          select: -1
        },
        {
          id: 13,
          question: "相手に合わせて、自分の印象を変えることができる。",
          select: -1
        }
      ]
    };
  },
  methods: {
    toResult(pt) {
      this.isAnswer = true;
      this.point = pt;
    },
    toQuestion() {
      this.isAnswer = false;
    }
  },
  created: function() {
    this.$emit("update-title", "SM尺度診断");
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
