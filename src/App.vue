<template>
  <div id="app">
    <div v-if="!playing">enterキーでスタート</div>
    <div v-else>
      <div>時間：{{ typedTime }}</div>
      <div>入力数：{{ typeWord }}</div>
      <div>単語：{{ nowWord }}</div>
    </div>
  </div>
</template>

<script>
import { reactive, ref, toRefs } from "@vue/reactivity";
export default {
  setup() {
    const InitData = reactive({
      nowWord: "", //単語
      typeWord: "", //入力値
      typedTime: 0, //残り時間
      words: [
        // 出題単語
        "dog",
        "cat",
        "monkey",
        "elephant",
        "giraffe",
        "penguin",
        "lion",
        "tiger",
        "pig",
        "cow",
      ],
    });

    // 押すまで始まらない
    const playing = ref(false);
    const startGame = (e) => {
      // ボタン押されたか判定
      if (e.key !== "Enter") return;
      else {
        playing.value = true;
      } // startGame関数のキーイベント発火
      addEventListener("keydown", startGame);
    };
    return {
      ...toRefs(InitData),
      playing,
    };
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  font-size: 20px;
  margin-top: 100px;
}
</style>
