<template>
  <div
    class="badge bg-success d-flex flex-wrap align-items-center mt-1 mb-1"
    id="create-table-block"
  >
    Create in
    <select
      class="form-select form-select-sm text-dark ms-1 me-1 mt-1"
      aria-label=".form-select-sm example"
      style="width: max-content"
      v-model="selectedDatabase"
    >
      <option disabled selected value="0">Database</option>
      <option v-for="(value, key) in databaseEngine" :key="key" :value="key">
        {{ key }}
      </option>
    </select>
    {{ selectedDatabase ? "Table With Name" : "" }}
    <input
      class="rounded column-name ms-1"
      type="text"
      v-show="selectedDatabase"
      v-model="newTableName"
    />
    <input
      class="rounded columns-input me-1"
      type="number"
      v-model="newTableColumnsCount"
      v-if="newTableName"
    />
    <input
      class="rounded column mb-1 ms-1 me-1"
      type="text"
      :placeholder="`Column${index}`"
      v-for="index in newTableColumnsCount"
      :key="index"
      v-show="newTableName"
      v-model="newTableColumns[index - 1]"
    />
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
      newTableColumnsCount: 0,
      newTableColumns: [],
      newTableName: "",
    };
  },
  methods: {},
  watch: {
    newTableColumnsCount(value) {
      this.newTableColumnsCount = Number.parseInt(value);
    },
    executeClicked(value) {
      if (value) {
        const {
          queryIndex,
          queryType,
          selectedDatabase,
          newTableName,
          newTableColumns,
        } = this;

        let newTableData = [];
        newTableData = [newTableName, {}];
        newTableColumns.forEach((column) => {
          newTableData[1][column] = "--";
        });

        this.emitter.emit("save-query-data", {
          queryIndex: queryIndex,
          queryType: queryType,
          selectedDatabase: selectedDatabase,
          newTableData: newTableData,
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

<style scoped>
.columns-input {
  width: 15%;
}
.column,
.column-name {
  width: 20%;
}
</style>
