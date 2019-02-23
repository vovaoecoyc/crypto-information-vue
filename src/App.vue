<template>
  <div id="app">
    <List :data="data"/>
    <SubInformation :information="dataSelectItem"/>
  </div>
</template>

<script>
import axios from "axios";
import * as API from "./constants";
import { eventEmitter } from "./main";

import List from "./components/List";
import SubInformation from "./components/SubInformation";

export default {
  name: "App",
  components: { List, SubInformation },
  data() {
    return { data: null, dataSelectItem: null };
  },
  watch: {
    dataSelectItem: function(data, prevData) {
      if (data !== null) {
        eventEmitter.$emit("openModal");
      }
    }
  },
  methods: {
    getCryptoList() {
      axios
        .get(API.URL_CRYPTO_DATA)
        .then(response => {
          if (response.status === 200) this.data = response.data;
        })
        .catch(error => {
          console.log(error);
        });
    },
    getCurrencyInformation(id) {
      axios
        .get(`${API.URL_CRYPTO_DATA}/${id}`)
        .then(response => {
          console.log("subIfo", response);
          if (response.status === 200) this.dataSelectItem = response.data;
        })
        .catch(error => {
          console.log(error);
        });
    }
  },
  mounted() {
    this.getCryptoList();
  },
  created() {
    eventEmitter.$on("loadSubItemInformation", id => {
      this.getCurrencyInformation(id);
    });
  }
};
</script>

<style>
#app {
  margin: auto;
}
</style>
