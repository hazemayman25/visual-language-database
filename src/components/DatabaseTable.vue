<template>
  <div class="d-flex justify-content-center mt-1 mb-1">
    <h3 class="rounded bg-light text-dark pe-1 ps-1 mt-1">
      {{ tableName }}
    </h3>
  </div>
  <table
    class="table rounded position-relative table-striped table-dark table-sm"
  >
    <thead>
      <tr>
        <th scope="col" v-for="(value, key) in table[0]" :key="key">
          {{ key }}
        </th>
      </tr>
    </thead>
    <tbody>
      <tr scope="row" v-for="(row, index) in table" :key="index">
        <td v-for="(value, key) in row" :key="key">{{ value }}</td>
      </tr>
    </tbody>
  </table>
</template>

<script>
export default {
  props: ["tableName", "table"],
  data() {
    return {};
  },
};
</script>

<style scoped>
table {
  overflow: hidden;
}
h3 {
  width: fit-content;
}
</style>