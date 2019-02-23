<template>
  <tr>
    <td class="w-25">
      <div class="Currency-more-information">
        <span>{{ item.name }}</span>
        <button class="btn btn-outline-info btn-sm" @click="handlerClick(item.id)">More</button>
      </div>
    </td>
    <td class="w-25">{{ item.type }}</td>
    <td class="w-25">{{ item.symbol }}</td>
    <td class="w-25" :class="{'New': item.is_new}">
      <span v-if="item.is_new">New!</span>
    </td>
  </tr>
</template>

<script>
import { eventEmitter } from "../../../main";

export default {
  name: "ListItem",
  props: {
    item: {
      type: Object,
      required: true
    }
  },
  methods: {
    handlerClick(id) {
      eventEmitter.$emit("loadSubItemInformation", [id]);
    }
  }
};
</script>

<style>
.New {
  color: red;
}

button {
  outline: none;
}

.Currency-more-information {
  display: flex;
  justify-content: space-between;
}
</style>


