<template>
  <li>
    <span class="list-item">
      <input
        type="checkbox"
        :id="index"
        class="item-checkbox"
        v-model="item.checked"
      />
      <label :for="index" :class="getItemClass(item.checked)">{{
        item.label
      }}</label>
    </span>
    <span v-html="deleteIcons" @click="deleteItem(index)"></span>
  </li>
</template>

<script>
import feather from "feather-icons";

export default {
  name: "ListItem",
  props: {
    item: Object,
    index: Number,
  },
  methods: {
    getItemClass(itemChecked) {
      return itemChecked ? "item-checked" : "";
    },
    deleteItem(index) {
      this.$emit("delete-item", index);
    },
  },
  computed: {
    deleteIcons() {
      return feather.icons.trash.toSvg({ width: 15 });
    },
  },
};
</script>

<style scoped>
li {
  width: 100%;
}
li,
item-list {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
.item-checkbox {
  margin-right: 10px;
}
.item-checked {
  text-decoration: line-through;
}
</style>
