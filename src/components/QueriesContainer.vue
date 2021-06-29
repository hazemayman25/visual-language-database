<template>
  <div>
    <div>
      <div v-for="(button, index) in currentBlocks" :key="index">
        <select-query
          v-if="button === 'Select'"
          :database-engine="databaseEngine"
          :execute-clicked="executeClicked"
          :current-blocks="currentBlocks"
        ></select-query>

        <delete-query
          v-else-if="button === 'Delete'"
          :database-engine="databaseEngine"
          :execute-clicked="executeClicked"
          :current-blocks="currentBlocks"
        >
        </delete-query>

        <insert-query
          v-else-if="button === 'Insert'"
          :database-engine="databaseEngine"
          :execute-clicked="executeClicked"
          :current-blocks="currentBlocks"
        ></insert-query>

        <update-query
          v-else-if="button === 'Update'"
          :database-engine="databaseEngine"
          :execute-clicked="executeClicked"
          :current-blocks="currentBlocks"
        >
        </update-query>

        <drop-query
          v-else-if="button === 'Drop'"
          :database-engine="databaseEngine"
          :execute-clicked="executeClicked"
          :current-blocks="currentBlocks"
        ></drop-query>

        <truncate-query
          v-else-if="button === 'Truncate'"
          :database-engine="databaseEngine"
          :execute-clicked="executeClicked"
          :current-blocks="currentBlocks"
        ></truncate-query>

        <create-table-query
          v-else-if="button === 'Create Table'"
          :database-engine="databaseEngine"
          :execute-clicked="executeClicked"
          :current-blocks="currentBlocks"
        ></create-table-query>

        <create-database-query
          v-else-if="button === 'Create Database'"
          :execute-clicked="executeClicked"
          :current-blocks="currentBlocks"
        ></create-database-query>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ["databaseEngine", "clicks", "currentBlocks", "executeClicked"],
  data() {
    return {
      selectedTableDelete: "",
    };
  },
  methods: {},
  mounted() {
    this.emitter.on("initialize-where", (array) => {
      this.selectedTableDelete = array[1];
    });
    this.emitter.on("original-state-delete-block", (originalArray) => {
      this.selectedTableDelete = originalArray[1];
    });
  },
};
</script>

<style scoped>
</style>