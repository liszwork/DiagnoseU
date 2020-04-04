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
            "話をしているときには，相手の表情のわずかな変化にも敏感になる。",
          select: -1
        },
        {
          id: 2,
          question:
            "目をみれば，その人のほんとうの気持ちを正確に読み取ることができる。",
          select: -1
        }
        // {
        //   id: 3,
        //   question: "だれかが自分にうそをついても，表情やしぐさですぐにうそだと見抜くことができる。",
        //   select: -1,
        // },
        // {
        //   id: 4,
        //   question: "目をみれば，自分が相手に何か不都合なことを言ったかどうか分かる。",
        //   select: -1,
        // },
        // {
        //   id: 5,
        //   question: "相手が冗談を聴いて笑っても，内心ではその冗談を下品であると思っているかどうかを見抜くことができる。",
        //   select: -1,
        // },
        // {
        //   id: 6,
        //   question: "私の直感力は，相手の気持ちや行いの原因を知るのにとても役に立つ。",
        //   select: -1,
        // },
        // {
        //   id: 7,
        //   question: "相手や状況に応じて自分の行動を変えるのが得意である。",
        //   select: -1,
        // },
        // {
        //   id: 8,
        //   question: "その場面でどのようにふるまえばよいか分かれば，それに応じて，自分の行動をたやすく変えることができる。",
        //   select: -1,
        // },
        // {
        //   id: 9,
        //   question: "自分が今いる場面で必要とされていることに応じて，自分の行動を変えることができる。",
        //   select: -1,
        // },
        // {
        //   id: 10,
        //   question: "物事が自分の思い通りにうまくいかないときには，すぐに他のやり方に切り換えることができる。",
        //   select: -1,
        // },
        // {
        //   id: 11,
        //   question: "自分のためになると分かっていても，体裁をよくするのが苦手ではない。",
        //   select: -1,
        // },
        // {
        //   id: 12,
        //   question: "まわりの人が望んでいることに応じて，自分の行動を変えることができる。",
        //   select: -1,
        // },
        // {
        //   id: 13,
        //   question: "相手にどのような印象でも与えることができる。",
        //   select: -1,
        // },
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
