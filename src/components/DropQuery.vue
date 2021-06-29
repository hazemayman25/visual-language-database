<template>
  <div
    class="badge bg-secondary d-flex align-items-center mt-1 mb-1"
    id="drop-block"
  >
    Drop from
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

    <select
      class="form-select form-select-sm text-dark ms-1 me-1"
      aria-label=".form-select-sm example"
      v-if="selectedDatabase"
      v-model="selectedTable"
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
    };
  },
  watch: {
    executeClicked(value) {
      if (value) {
        const { queryIndex, queryType, selectedDatabase, selectedTable } = this;
        this.emitter.emit("save-query-data", {
          queryIndex: queryIndex,
          queryType: queryType,
          selectedDatabase: selectedDatabase,
          selectedTable: selectedTable,
        });
      }
    },
  },
  mounted() {
    this.queryIndex = this.currentBlocks.length;
    this.queryType = this.currentBlocks[this.queryIndex - 1];
  },
};
</script>

<style scoped></style>
