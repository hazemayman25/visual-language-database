<template>
  <!-- Select condition -->

  <div
    class="badge bg-warning d-flex align-items-center mt-1 mb-1"
    id="where-block"
    v-if="
      selectedTableSelect !== '' && typeof selectedTableSelect !== 'undefined'
    "
  >
    Where
    <select
      class="form-select form-select-sm text-dark ms-1 me-1"
      aria-label="form-select-sm example"
      v-model="selectedColumnWhere"
    >
      <option value="" disabled selected>Column</option>
      <option
        v-for="(value, key) in databaseEngine[selectedDatabase][
          selectedTableSelect
        ][0]"
        :key="key"
        :value="key"
      >
        {{ key }}
      </option>
    </select>
    <select
      class="form-select form-select-sm text-dark ms-1 me-1"
      aria-label=".form-select-sm example"
      v-model="conditionOperator"
    >
      <option value="" disabled selected>Operator</option>
      <option value="greater">Greater than</option>
      <option value="less">Less than</option>
      <option value="equal">Equals</option>
    </select>
    <input
      class="rounded"
      v-if="selectedColumnWhere !== '' && conditionOperator"
      type="text"
      v-model="whereInputSelect"
    />
  </div>

  <!-- Delete condition -->

  <div
    class="badge bg-warning d-flex align-items-center mt-1 mb-1"
    id="where-block"
    v-else-if="
      selectedTableDelete !== '' && typeof selectedTableDelete !== 'undefined'
    "
  >
    Where
    <select
      class="form-select form-select-sm text-dark ms-1 me-1"
      aria-label=".form-select-sm example"
      v-model="selectedColumnWhere"
    >
      <option value="" disabled selected>Column</option>
      <option
        v-for="(value, key) in databaseEngine[selectedDatabase][
          selectedTableDelete
        ][0]"
        :key="key"
        :value="key"
      >
        {{ key }}
      </option>
    </select>
    <select
      class="form-select form-select-sm text-dark ms-1 me-1"
      aria-label=".form-select-sm example"
      v-model="conditionOperator"
    >
      <option value="" disabled selected>Operator</option>
      <option value="greater">Greater than</option>
      <option value="less">Less than</option>
      <option value="equal">Equals</option>
    </select>
    <input
      class="rounded"
      v-if="selectedColumnWhere && conditionOperator"
      type="text"
      v-model="whereInputDelete"
    />
  </div>

  <!-- Update condition -->

  <div
    class="badge bg-warning d-flex align-items-center mt-1 mb-1"
    id="where-block"
    v-else-if="
      selectedTableUpdate !== '' && typeof selectedTableUpdate !== 'undefined'
    "
  >
    Where
    <select
      class="form-select form-select-sm text-dark ms-1 me-1"
      aria-label=".form-select-sm example"
      v-model="selectedColumnWhere"
    >
      <option value="" disabled selected>Column</option>
      <option
        v-for="(value, key) in databaseEngine[selectedDatabase][
          selectedTableUpdate
        ][0]"
        :key="key"
        :value="key"
      >
        {{ key }}
      </option>
    </select>
    <select
      class="form-select form-select-sm text-dark ms-1 me-1"
      aria-label=".form-select-sm example"
      v-model="conditionOperator"
    >
      <option value="" disabled selected>Operator</option>
      <option value="greater">Greater than</option>
      <option value="less">Less than</option>
      <option value="equal">Equals</option>
    </select>
    <input
      class="rounded"
      v-if="selectedColumnWhere !== '' && conditionOperator"
      type="text"
      v-model="whereInputUpdate"
    />
  </div>
</template>

<script>
export default {
  props: [
    "databaseEngine",
    "currentBlocks",
    "selectedDatabase",
    "selectedTableDelete",
    "selectedTableSelect",
    "selectedTableUpdate",
    "executeClicked",
  ],
  data() {
    return {
      queryIndex: null,
      queryType: null,
      selectedTable: "",
      selectedColumn: "",
      selectedColumnWhere: "",
      whereInputSelect: "",
      whereInputDelete: "",
      whereInputUpdate: "",
      conditionOperator: "",
    };
  },
  watch: {
    executeClicked(value) {
      if (value && this.whereInputSelect) {
        const {
          queryIndex,
          queryType,
          selectedColumnWhere,
          conditionOperator,
          whereInputSelect,
        } = this;
        this.emitter.emit("save-query-data", {
          queryIndex: queryIndex,
          queryType: queryType,
          selectedColumnWhere: selectedColumnWhere,
          conditionOperator: conditionOperator,
          whereInputSelect: whereInputSelect,
        });
      } else if (value && this.whereInputDelete) {
        const {
          queryIndex,
          queryType,
          selectedColumnWhere,
          conditionOperator,
          whereInputDelete,
        } = this;
        this.emitter.emit("save-query-data", {
          queryIndex: queryIndex,
          queryType: queryType,
          selectedColumnWhere: selectedColumnWhere,
          conditionOperator: conditionOperator,
          whereInputDelete: whereInputDelete,
        });
      } else if (value && this.whereInputUpdate) {
        const {
          queryIndex,
          queryType,
          selectedColumnWhere,
          conditionOperator,
          whereInputUpdate,
        } = this;
        this.emitter.emit("save-query-data", {
          queryIndex: queryIndex,
          queryType: queryType,
          selectedColumnWhere: selectedColumnWhere,
          conditionOperator: conditionOperator,
          whereInputUpdate: whereInputUpdate,
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
input {
  width: 90%;
}
</style>
