<template>
  <div
    class="memo-container"
    @mouseenter="showDeleteButton = true"
    @mouseleave="showDeleteButton = false"
  >
    <input @input="_modifyMemoTitle" :value="memo.title" />
    <span>{{ computedDate }}</span>
    <textarea @input="_modifyMemoContent" :value="memo.content" />
    <button v-show="showDeleteButton" @click="_removeMemo">delete</button>
  </div>
</template>

<script>
export default {
  name: "Memo",
  emits: {},
  created() {
    console.log(this.testValue);
  },
  data() {
    return {
      showDeleteButton: false,
    };
  },
  props: {
    memo: Object,
    removeMemo: Function,
    modifyMemo: Function,
  },
  computed: {
    computedDate() {
      const date = new Date(this.memo.updatedDate);
      return date.toLocaleDateString() + date.toLocaleTimeString();
    },
  },
  methods: {
    _modifyMemoContent(e) {
      this.modifyMemo({
        key: "content",
        value: e.target.value,
        id: this.memo.id,
      });
    },
    _modifyMemoTitle(e) {
      this.modifyMemo({
        key: "title",
        value: e.target.value,
        id: this.memo.id,
      });
    },
    _removeMemo() {
      this.removeMemo(this.memo.id);
    },
  },
};
</script>

<style scoped>
.memo-container {
  background-color: rgb(235, 235, 235);
  width: fit-content;
  height: fit-content;
  padding: 5px;
  margin: 5px;
}

.memo-container * {
  margin: 3px;
}
</style>