<template>
  <b-modal
    v-if="!(information === null)"
    id="currency-info-modal"
    v-model="showModal"
    size="lg"
    hide-footer
    hide-header
    centered
  >
    <div class="Header-modal">
      <h4>Sub information for currency {{information.name}}</h4>
    </div>
    <div class="Footer-content">
      <table class="table table-striped table-bordered">
        <thead>
          <tr>
            <th>Status</th>
            <th>Description</th>
            <th>Algoritm</th>
            <th>Rank</th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <td>{{information.development_status}}</td>
            <td>{{information.description}}</td>
            <td>{{information.hash_algorithm}}</td>
            <td>{{information.rank}}</td>
          </tr>
        </tbody>
      </table>
    </div>
    <div class="Footer-modal">
      <button @click="showModal = false" class="btn btn-outline-danger btn-sm">Close</button>
    </div>
  </b-modal>
</template>

<script>
import { eventEmitter } from "../../main";

export default {
  name: "SubInformation",
  props: {
    information: {
      type: Object | null,
      required: true
    }
  },
  data() {
    return { showModal: false };
  },
  created() {
    eventEmitter.$on("openModal", () => {
      this.showModal = true;
    });
  }
};
</script>

<style>
.Header-modal {
  text-align: center;
}

.Footer-content {
  display: flex;
  justify-content: center;
  margin: 15px auto;
}

table {
  margin: 5px 0;
}

.Footer-modal {
  display: flex;
  justify-content: center;
  width: 100%;
}
</style>


