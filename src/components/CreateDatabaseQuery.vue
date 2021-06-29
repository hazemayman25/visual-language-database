<template>
  <div
    class="badge bg-primary d-flex flex-wrap align-items-center mt-1 mb-1"
    id="create-database-block"
  >
    Create new
    <input
      placeholder="Database"
      class="rounded column-name ms-1"
      type="text"
      v-model="newDatabaseName"
    />
  </div>
</template>

<script>
export default {
  props: ["currentBlocks", "executeClicked"],
  data() {
    return {
      queryIndex: null,
      queryType: null,
      newDatabaseName: "",
    };
  },
  methods: {},
  watch: {
    executeClicked(value) {
      if (value) {
        const { queryIndex, queryType, newDatabaseName } = this;

        let newDatabaseData = [newDatabaseName, {}];

        this.emitter.emit("save-query-data", {
          queryIndex: queryIndex,
          queryType: queryType,
          newDatabaseData: newDatabaseData,
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
  width: 30%;
}
</style>
