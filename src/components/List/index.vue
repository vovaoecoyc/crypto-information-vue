<template>
  <div class="List">
    <h3>Data about crypto currensies</h3>
    <table class="table table-striped table-bordered" v-if="data !== null">
      <thead>
        <tr>
          <th>Name</th>
          <th>Type</th>
          <th>Symbol</th>
          <th>New</th>
        </tr>
      </thead>
      <tbody>
        <ListItem v-for="value in data" :key="value.id" :item="value"/>
      </tbody>
    </table>

    <div class="Spinner" v-else>
      <div/>
      <div/>
      <div/>
    </div>
  </div>
</template>

<script>
import ListItem from "./ListItem";

export default {
  name: "List",
  props: {
    data: {
      type: Array
    }
  },
  components: { ListItem }
};
</script>

<style>
.List {
  width: 70%;
  margin: auto;
  text-align: center;
}

.List h3 {
  margin: 20px;
}

table {
  text-align: center;
}

@keyframes spinner {
  to {
    opacity: 0.1;
    transform: translate3d(0, 10px, 0);
  }
}

.Spinner {
  display: flex;
  justify-content: center;
  margin: 100px auto;
}

.Spinner > div {
  width: 25px;
  height: 25px;
  margin: 10px;
  background: #8385aa;
  border-radius: 50%;
  animation: spinner 0.6s infinite alternate;
}

.Spinner > div:nth-child(2) {
  animation-delay: 0.2s;
}

.Spinner > div:nth-child(3) {
  animation-delay: 0.4s;
}
</style>


