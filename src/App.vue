<template>
  <div>hihi</div>
  <Memos
    :memos="memos"
    :currentText="currentText"
    :addMemo="addMemo"
    :removeMemo="removeMemo"
    :modifyMemo="modifyMemo"
    v-model:currentText="currentText"
  />
  <button @click="modalState = true">open modal</button>
  <Modal v-model:modalstate="modalState" />
</template>

<script>
import Memos from "./components/Memos.vue";
import Modal from "./components/Modal.vue";
export default {
  name: "App",
  data() {
    return {
      currentId: 1,
      currentText: "",

      defaultMemo: {
        title: "default",
        content: "content",
        updatedDate: Date.now(),
        id: 0,
      },
      memos: [
        {
          title: "default",
          content: "content",
          updatedDate: Date.now(),
          id: 0,
        },
      ],
      modalState: false,
    };
  },
  components: {
    Memos,
    Modal,
  },
  methods: {
    addMemo() {
      this.memos.push({
        ...this.defaultMemo,
        title: this.currentText,
        updatedDate: Date.now(),
        id: this.currentId,
      });
      this.currentText = "";
      this.currentId += 1;
    },
    removeMemo(id) {
      this.memos = this.memos.filter((memo) => memo.id !== id);
    },
    modifyMemo({ key, value, id }) {
      this.memos = this.memos.map((memo) => {
        if (memo.id !== id) return memo;
        return {
          ...memo,
          [key]: value,
        };
      });
    },
  },
};
</script>

<style>
html,
body {
  width: 100%;
  height: 100%;
}
</style>