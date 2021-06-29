<template>
  <div
    class="badge bg-success d-flex align-items-center mt-1 mb-1"
    id="insert-block"
  >
    Insert in
    <select
      class="form-select form-select-sm text-dark ms-1 me-1"
      aria-label=".form-select-sm example"
      v-model="selectedDatabase"
    >
      <option value="" disabled selected>Database</option>
      <option v-for="(value, key) in databaseEngine" :key="key" :value="key">
        {{ key }}
      </option>
    </select>
    {{ selectedDatabase ? "in" : "" }}
    <select
      class="form-select form-select-sm text-dark ms-1 me-1"
      aria-label=".form-select-sm example"
      v-if="selectedDatabase"
      v-model="selectedTable"
      @change="initializeInputsObject()"
    >
      <option value="" disabled selected>Table</option>
      <option
        v-for="(value, key) in databaseEngine[selectedDatabase]"
        :key="key"
        :value="key"
      >
        {{ key }}
      </option>
    </select>

    {{ selectedTable ? "Values:" : "" }}

    <div class="d-flex flex-wrap ms-2" v-if="selectedTable !== ''">
      <div
        class="d-flex justify-content-between align-items-center"
        v-for="(value, key, index) in databaseEngine[selectedDatabase][
          selectedTable
        ][0]"
        :key="key"
      >
        <label
          :for="
            Object.keys(databaseEngine[selectedDatabase][selectedTable][0])[
              index
            ]
          "
          >{{
            Object.keys(databaseEngine[selectedDatabase][selectedTable][0])[
              index
            ]
          }}:
        </label>
        <input
          class="rounded ms-1"
          :id="
            Object.keys(databaseEngine[selectedDatabase][selectedTable][0])[
              index
            ]
          "
          @change="(event) => addInput(key, event)"
          type="text"
        />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ["databaseEngine", "currentBlocks", "executeClicked"],
  data() {
    return {
      queryIndex: null,
      queryType: null,
      selectedDatabase: "",
      selectedTable: "",
      inputsKeys: [],
      inputValues: [],
      inputs: {},
    };
  },
  methods: {
    addInput(key, event) {
      this.inputs[key] = event.target.value;
    },
    initializeInputsObject() {
      for (let key of Object.keys(
        this.databaseEngine[this.selectedDatabase][this.selectedTable][0]
      )) {
        this.inputs[key] = null;
      }
    },
  },
  mounted() {
    this.queryIndex = this.currentBlocks.length;
    this.queryType = this.currentBlocks[this.queryIndex - 1];
  },
  watch: {
    executeClicked(value) {
      if (value) {
        const {
          queryIndex,
          queryType,
          selectedDatabase,
          selectedTable,
          inputs,
        } = this;
        this.emitter.emit("save-query-data", {
          queryIndex: queryIndex,
          queryType: queryType,
          selectedDatabase: selectedDatabase,
          selectedTable: selectedTable,
          inputs: inputs,
        });
      }
    },
  },
};
</script>

<style scoped>
#form-select {
  width: max-content;
}
.badge {
  width: fit-content;
}
input {
  width: 50%;
}
</style>
