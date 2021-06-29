<template>
  <div
    class="
      badge
      bg-light
      d-flex
      text-dark
      flex-wrap
      align-items-center
      mt-1
      mb-1
    "
    id="update-block"
  >
    Update
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
    <select
      class="form-select form-select-sm text-dark ms-1 me-1 mt-1"
      aria-label=".form-select-sm example"
      style="width: max-content"
      v-if="selectedDatabase"
      v-model="selectedTable"
    >
      <option disabled selected value="0">Table</option>
      <option
        v-for="(value, key) in databaseEngine[selectedDatabase]"
        :key="key"
        :value="key"
      >
        {{ key }}
      </option>
    </select>
    <div
      v-if="selectedTable"
      class="d-flex justify-content-start align-items-center"
    >
      Set
      <select
        @change="emitPassUpdateInput"
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
    </div>

    <div
      v-for="index in columnSlots"
      :key="index"
      class="d-flex justify-content-between align-items-center"
      v-show="columnSlots > 0 || typeof columnSlots !== 'undefined'"
    >
      <select
        class="form-select form-select-sm text-dark ms-1 me-1 mt-1"
        aria-label=".form-select-sm example"
        style="width: fit-content"
        v-model="selectedColumns[index - 1]"
      >
        <option disabled selected>Column{{ index }}</option>
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

      =
      <input
        @change="mountWhere"
        class="rounded ms-1"
        type="text"
        v-model="columnInputs[index - 1]"
      />
    </div>
  </div>
  <where-query
    v-if="columnInputs[columnInputs.length - 1] !== '' && whereClicked"
    :selected-database="selectedDatabase"
    :selected-table-select="''"
    :database-engine="databaseEngine"
    :selected-table-delete="''"
    :selected-table-update="selectedTable"
    :current-blocks="currentBlocks"
    :execute-clicked="executeClicked"
  ></where-query>
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
      howManyColumns: 0,
      columnSlots: 0,
      selectedColumns: [],
      columnInputs: [],
      whereClicked: false,
    };
  },
  methods: {
    emitPassUpdateInput() {
      this.emitter.emit("update-pass-last-input-to-button", true);
    },
    whereClickedFunc(array) {
      if (array[1] === this.queryIndex) {
        this.whereClicked = array[0];
      }
    },
  },
  watch: {
    selectedTable(value) {
      if (value !== "" && typeof value !== "undefined") {
        this.howManyColumns = Object.keys(
          this.databaseEngine[this.selectedDatabase][this.selectedTable][0]
        ).length;
      }
    },
    columnSlots(value) {
      for (let i = 0; i < value; i++) {
        this.selectedColumns.push("");
        this.columnInputs.push("none");
      }
    },
    executeClicked(value) {
      if (value) {
        const {
          queryIndex,
          queryType,
          selectedDatabase,
          selectedTable,
          selectedColumns,
          columnInputs,
        } = this;

        let updateData = [];

        selectedColumns.forEach((selectedColumn, index) => {
          updateData = [...updateData, [[selectedColumn], columnInputs[index]]];
        });

        this.emitter.emit("save-query-data", {
          queryIndex: queryIndex,
          queryType: queryType,
          selectedDatabase: selectedDatabase,
          selectedTable: selectedTable,
          updateData: updateData,
        });
      }
    },
  },
  mounted() {
    this.queryIndex = this.currentBlocks.length;
    this.queryType = this.currentBlocks[this.queryIndex - 1];

    this.emitter.on("where-clicked", this.whereClickedFunc);
  },
};
</script>

<style scoped>
.badge {
  width: min-content;
}
</style>
