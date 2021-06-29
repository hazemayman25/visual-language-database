<template>
  <div
    class="badge bg-info d-flex flex-wrap align-items-center mt-1 mb-1"
    id="order-by-block"
    v-if="selectedTable !== '' && typeof selectedTable !== 'undefined'"
  >
    Order By
    <select
      class="form-select form-select-sm text-dark ms-1 me-1 mt-1"
      aria-label=".form-select-sm example"
      style="width: max-content"
      v-model="columnSlots"
    >
      <option disabled selected value="0">0</option>
      <option :value="index" v-for="index in howManyColumns" :key="index">
        {{ index }}
      </option>
    </select>
    <select
      v-show="columnSlots > 0 && typeof columnSlots !== 'undefined'"
      class="form-select form-select-sm text-dark ms-1 me-1 mt-1"
      aria-label=".form-select-sm example"
      v-for="index in columnSlots"
      :key="index"
      style="width: fit-content"
      v-model="selectedColumns[index - 1]"
    >
      <option selected>
        {{ selectedColumns[index - 1] }}
      </option>
      <option
        v-for="(value, key) in databaseEngine[selectedDatabase][
          selectedTable
        ][0]"
        :key="key"
        :value="key"
      >
        {{ key }}
      </option>
    </select>
    {{ columnSlots > 0 && typeof columnSlots !== "undefined" ? "in" : "" }}
    <select
      v-show="columnSlots > 0 && typeof columnSlots !== 'undefined'"
      class="form-select form-select-sm text-dark ms-1 me-1 mt-1"
      aria-label=".form-select-sm example"
      style="width: fit-content"
      v-model="ascendingFlag"
    >
      <option :value="true">ASCENDING</option>
      <option :value="false">DESCENDING</option>
    </select>
    {{ columnSlots > 0 && typeof columnSlots !== "undefined" ? "way" : "" }}
  </div>
</template>

<script>
export default {
  props: [
    "databaseEngine",
    "selectedTableSelect",
    "selectedDatabase",
    "currentBlocks",
    "executeClicked",
  ],
  data() {
    return {
      queryIndex: null,
      queryType: null,
      selectedTable: "",
      selectedColumns: [],
      howManyColumns: 0,
      columnSlots: 0,
      ascendingFlag: null,
    };
  },
  methods: {},
  mounted() {
    this.selectedTable = this.selectedTableSelect;
    this.queryIndex = this.currentBlocks.length;
    this.queryType = this.currentBlocks[this.queryIndex - 1];
  },
  watch: {
    selectedTable(value) {
      if (value !== "" && typeof value !== "undefined") {
        this.howManyColumns = Object.keys(
          this.databaseEngine[this.selectedDatabase][this.selectedTable][0]
        ).length;
        for (let i = 0; i < this.howManyColumns; i++) {
          this.selectedColumns.push("none");
        }
      }
    },
    executeClicked(value) {
      if (value) {
        const { queryIndex, queryType, selectedColumns, ascendingFlag } = this;
        this.emitter.emit("save-query-data", {
          queryIndex: queryIndex,
          queryType: queryType,
          selectedColumns: selectedColumns,
          ascendingFlag: ascendingFlag,
        });
      }
    },
  },
};
</script>

<style scoped></style>
