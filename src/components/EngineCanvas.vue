<template>
  <div>
    <select
      class="
        form-select form-select-sm
        text-light
        d-flex
        flex-column
        justify-content-start
        mt-1
      "
      id="database-dropdown"
      aria-label=".form-select-sm example"
      v-model="selectedDatabase"
    >
      <option value="" disabled selected>Select a Database</option>
      <option v-for="(value, key) in databaseEngine" :key="key" :value="key">
        {{ key }}
      </option>
    </select>
    <select
      @change="viewTable"
      v-model="selectedTable"
      class="form-select form-select-sm text-light mt-1"
      id="table-dropdown"
      aria-label=".form-select-sm example"
      v-if="selectedDatabase"
    >
      <option value="" disabled selected>Select a Table</option>
      <option
        v-for="(value, key) in databaseEngine[selectedDatabase]"
        :key="key"
        :value="key"
      >
        {{ key }}
      </option>
    </select>
  </div>
  <div class="container mt-2">
    <database-table
      v-if="selectedTable && selectedTable in databaseEngine[selectedDatabase]"
      :table-name="selectedTable"
      :table="databaseEngine[selectedDatabase][selectedTable]"
    ></database-table>
    <div class="badge bg-dark text-light">
      {{
        currentlySelectedColumn &&
        currentlySelectedDatabase &&
        currentlySelectedTable
          ? "SELECTION RESULT: "
          : ""
      }}
    </div>

    <database-table
      v-if="
        currentlySelectedColumn &&
          currentlySelectedDatabase &&
          currentlySelectedTable
      "
      :table-name="currentlySelectedTable"
      :table="currentlySelectedColumn"
    ></database-table>
  </div>
</template>

<script>
export default {
  props: [
    "databaseEngine",
    "executionButton2",
    "executionClass2",
    "currentlySelectedColumn",
    "currentlySelectedDatabase",
    "currentlySelectedTable",
  ],
  data() {
    return {
      selectedDatabase: "",
      selectedTable: "",
    };
  },
};
</script>

<style scoped>
.btn {
  color: rgb(44, 44, 44);
}
#table-dropdown,
#database-dropdown {
  background-color: rgb(44, 44, 44);
}
#input {
  max-width: 30%;
}
#select-dropdown {
  max-width: max-content;
}

.badge {
  width: fit-content;
}

#select-block {
  display: flex;
  width: 100%;
  align-items: center;
}
</style>
