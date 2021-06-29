<template>
  <div
    class="badge bg-primary d-flex align-items-center mt-1 mb-1"
    id="select-block"
  >
    Select from
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

    <select
      @change="emitPassColumn"
      v-if="selectedTable"
      class="form-select form-select-sm text-dark ms-1 me-1"
      aria-label=".form-select-sm example"
      v-model="selectedColumn"
    >
      <option value="" disabled selected>Column</option>
      <option
        v-for="(value, key) in databaseEngine[selectedDatabase][
          selectedTable
        ][0]"
        :key="selectedTable + key"
        :value="key"
      >
        {{ key }}
      </option>
    </select>
  </div>
  <where-query
    v-if="selectedColumn && whereClicked"
    :selected-database="selectedDatabase"
    :selected-table-select="selectedTable"
    :database-engine="databaseEngine"
    :selected-table-delete="''"
    :selected-table-update="''"
    :current-blocks="currentBlocks"
    :execute-clicked="executeClicked"
  ></where-query>
  <order-by-query
    v-else-if="selectedColumn && orderByClicked"
    :selected-database="selectedDatabase"
    :selected-table-select="selectedTable"
    :database-engine="databaseEngine"
    :current-blocks="currentBlocks"
    :execute-clicked="executeClicked"
  >
  </order-by-query>
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
      selectedColumn: "",
      whereClicked: false,
      orderByClicked: false,
    };
  },
  methods: {
    emitPassColumn() {
      this.emitter.emit(
        "select-pass-table-column-to-button",
        this.selectedColumn
      );
    },
    whereClickedFunc(array) {
      if (array[1] === this.queryIndex) {
        this.whereClicked = array[0];
      }
    },
    orderByClickedFunc(array) {
      if (array[1] === this.queryIndex) {
        this.orderByClicked = array[0];
      }
    },
  },
  beforeCreate() {
    this.emitter.emit("original-state-select-block", "");
  },
  mounted() {
    this.queryIndex = this.currentBlocks.length;
    this.queryType = this.currentBlocks[this.queryIndex - 1];

    this.emitter.on("where-clicked", this.whereClickedFunc);
    this.emitter.on("order-by-clicked", this.orderByClickedFunc);
  },

  watch: {
    executeClicked(value) {
      if (value) {
        const {
          queryIndex,
          queryType,
          selectedDatabase,
          selectedTable,
          selectedColumn,
          whereClicked,
          orderByClicked,
        } = this;
        this.emitter.emit("save-query-data", {
          queryIndex: queryIndex,
          queryType: queryType,
          selectedDatabase: selectedDatabase,
          selectedTable: selectedTable,
          selectedColumn: selectedColumn,
          whereClicked: whereClicked,
          orderyByClicked: orderByClicked,
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
</style>
