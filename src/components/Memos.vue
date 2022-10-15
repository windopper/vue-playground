<template>
  <!-- <input placeholder="hihi" /> -->
  <input
    @input="$emit('update:currentText', $event.target.value)"
    :value="currentText"
  />
  <button @click="addMemo">addMemo</button>
  <div>{{ currentText }}</div>
  <div class="memo-container">
    <div v-for="memo of memos" :key="memo.key">
      <Memo :memo="memo" :removeMemo="removeMemo" :modifyMemo="modifyMemo" />
    </div>
  </div>
</template>

<script>
import Memo from "./Memo.vue";
export default {
  name: "Memos",
  props: {
    currentText: String,
    memos: [Object],
    addMemo: Function,
    removeMemo: Function,
    modifyMemo: Function,
  },
  components: {
    Memo,
  },
  methods: {
    test() {
      console.log("hi");
    },
  },
};
</script>

<style sass scoped>
</style>