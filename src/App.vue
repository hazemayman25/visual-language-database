<template>
  <home-nav-bar></home-nav-bar>
  <div class="container" :key="componentKey">
    <div class="row">
      <div class="col-2 d-flex flex-column">
        <div class="d-flex justify-content-center">
          <div class="badge bg-info d-flex align-items-center">
            <h3
              style="margin-bottom: 0"
              class="
                fs-5
                display-2
                d-flex
                justify-content-center
                align-items-center
              "
            >
              Blocks Group
            </h3>
          </div>
        </div>
        <buttons-container
          :buttons="buttons"
          :colors="colors"
          :clicks="clicks"
          :current-blocks="currentBlocks"
          :selected-column-for-select="selectedColumnForSelect"
          :is-update-last-input-triggered="isUpdateLastInputTriggered"
        ></buttons-container>
      </div>
      <div class="col-5 d-flex flex-column align-items-center">
        <div class="badge bg-info d-flex align-items-center">
          <h3
            style="margin-bottom: 0"
            class="
              fs-5
              display-2
              d-flex
              justify-content-center
              align-items-center
            "
          >
            Queries Container
          </h3>
        </div>
        <div
          class="
            container
            rounded
            d-flex
            flex-column
            justify-content-between
            mt-2
          "
          style="background: rgb(136, 136, 136); min-height: 100%"
        >
          <queries-container
            :database-engine="databaseEngine"
            :clicks="clicks"
            :current-blocks="currentBlocks"
            :execute-clicked="executeClicked"
          ></queries-container>
          <div class="d-flex flex-row justify-content-center align-items-end">
            <button
              @click="executeRequest"
              class="btn col-6 text-light mb-1"
              :class="executionClass1"
            >
              {{ executionButton1 }}
            </button>
            <button
              @click="forceRerender"
              class="btn col-6 text-light mb-1"
              :class="executionClass3"
            >
              {{ executionButton3 }}
            </button>
          </div>
        </div>
      </div>
      <div
        class="
          col-5
          rounded
          d-flex
          flex-column
          justify-content-between
          align-items-center
        "
      >
        <div class="badge bg-info d-flex align-items-center mb-1">
          <h3
            style="margin-bottom: 0"
            class="
              fs-5
              display-2
              d-flex
              justify-content-center
              align-items-center
            "
          >
            Engine Canvas
          </h3>
        </div>
        <div
          class="
            container
            rounded
            d-flex
            flex-column
            justify-content-between
            mt-1
          "
          style="background: rgb(136, 136, 136); min-height: 100%"
        >
          <engine-canvas
            :execution-button-2="executionButton2"
            :execution-class-2="executionClass2"
            :database-engine="databaseEngine"
            :currently-selected-database="currentlySelectedDatabase"
            :currently-selected-table="currentlySelectedTable"
            :currently-selected-column="currentlySelectedColumn"
          ></engine-canvas>
          <div
            style="width: 100%"
            class="d-flex flex-row justify-content-center align-items-end"
          ></div>
        </div>
      </div>
    </div>
  </div>
  <guide-off-canvas></guide-off-canvas>
</template>

<script>
import HomeNavBar from "./components/HomeNavBar.vue";
import EngineCanvas from "./components/EngineCanvas.vue";
import QueriesContainer from "./components/QueriesContainer.vue";
import ButtonsContainer from "./components/ButtonsContainer.vue";
import GuideOffCanvas from "./components/GuideOffCanvas.vue";

export default {
  name: "App",
  components: {
    HomeNavBar,
    QueriesContainer,
    EngineCanvas,
    ButtonsContainer,
    GuideOffCanvas,
  },
  data() {
    return {
      componentKey: 0,
      databaseEngine: {
        database1: {
          friends: [
            {
              id: 1,
              firstname: "Hazem",
              lastname: "Ayman",
              age: 22,
              faculty: "MET",
            },
            {
              id: 2,
              firstname: "Hazem",
              lastname: "Ahmed",
              age: 23,
              faculty: "MET",
            },
            {
              id: 3,
              firstname: "Hazem",
              lastname: "Ahmed",
              age: 25,
              faculty: "MET",
            },
            {
              id: 4,
              firstname: "Ahmed",
              lastname: "Emad",
              age: 23,
              faculty: "MET",
            },
            {
              id: 5,
              firstname: "Abdullah",
              lastname: "Mahmoud",
              age: 22,
              faculty: "MET",
            },
          ],
          doctors: [
            {
              id: 1,
              firstname: "Wael",
              lastname: "Abouelsaadat",
              age: 50,
              faculty: "MET",
              major: "CSEN",
            },
            {
              id: 2,
              firstname: "Slim",
              lastname: "Abdelnadher",
              age: 50,
              faculty: "MET",
              major: "CSEN",
            },
            {
              id: 3,
              firstname: "Abdelmagid",
              lastname: "Kofta",
              age: 50,
              faculty: "MET",
              major: "CSEN",
            },
          ],
        },
      },
      buttons: [
        "Select",
        "Where",
        "Insert",
        "Delete",
        "Order",
        "Update",
        "Drop",
        "Truncate",
        "Create Table",
        "Create Database",
      ],
      colors: [
        "btn-primary mt-2 mb-1",
        "btn-warning mt-1 mb-1",
        "btn-success mt-1 mb-1",
        "btn-danger mt-1 mb-1",
        "btn-info mt-1 mb-1",
        "btn-light mt-1 mb-1",
        "btn-secondary mt-1 mb-1",
        "btn-dark mt-1 mb-1",
        "btn-success mt-1 mb-1",
        "btn-primary mt-1 mb-1",
      ],
      executionButton1: "Execute",
      executionButton2: "Create Chart",
      executionButton3: "Reset",
      executionClass1: "btn-success me-2 ms-2",
      executionClass2: "btn-info me-2 ms-2",
      executionClass3: "btn-danger me-2 ms-2",
      clicks: [0, 0, 0, 0, 0, 0, 0, 0, 0, 0],
      currentBlocks: [],
      selectedColumnForSelect: "",
      isUpdateLastInputTriggered: false,
      executeClicked: false,
      queries: [],
      currentlySelectedDatabase: null,
      currentlySelectedTable: null,
      currentlySelectedColumn: null,
      databaseToDeleteFrom: null,
      tableToDeleteFrom: null,
      databaseToUpdateFrom: null,
      tableToUpdateFrom: null,
      updateInput: null,
    };
  },
  methods: {
    forceRerender() {
      this.componentKey += 1;
      this.clicks = [0, 0, 0, 0, 0, 0, 0, 0, 0, 0];
      this.currentBlocks = [];
      this.selectedColumnForSelect = "";
      this.isUpdateLastInputTriggered = false;
      this.executeClicked = false;
      this.queries = [];
      this.currentlySelectedDatabase = null;
      this.currentlySelectedTable = null;
      this.currentlySelectedColumn = null;
      this.databaseToDeleteFrom = null;
      this.tableToDeleteFrom = null;
      this.databaseToUpdateFrom = null;
      this.tableToUpdateFrom = null;
      this.updateInput = null;
      //I PUSHED
    },
    execute() {
      function getKeyByValue(object, value) {
        return Object.keys(object).find((key) => object[key] === value);
      }
      let queriesObjs = [];
      for (let i = 0; i < this.queries.length; i++) {
        queriesObjs = [
          ...queriesObjs,
          JSON.parse(JSON.stringify(this.queries[i])),
        ];
      }
      queriesObjs.forEach((query, index) => {
        if (query.queryType === "Select") {
          const databaseName = query.selectedDatabase;
          let filteredDatabase = Object.assign(
            {},
            this.databaseEngine[databaseName]
          );
          this.currentlySelectedDatabase = filteredDatabase;
          let filteredTable = getKeyByValue(
            filteredDatabase,
            filteredDatabase[query.selectedTable]
          );
          this.currentlySelectedTable = filteredTable;
          let filteredColumn = [];
          if (query.selectedColumn) {
            for (let row of filteredDatabase[filteredTable]) {
              filteredColumn = [...filteredColumn, row[query.selectedColumn]];
            }
          }
          let filteredColumnObj = [];
          if (filteredColumn.length !== 0) {
            for (let column of filteredColumn) {
              filteredColumnObj = [
                ...filteredColumnObj,
                { [query.selectedColumn]: column },
              ];
            }
          } else {
            for (let row of filteredDatabase[filteredTable]) {
              filteredColumnObj = [...filteredColumnObj, row];
            }
          }

          this.currentlySelectedColumn = filteredColumnObj;
        } else if (query.queryType === "Where") {
          if (queriesObjs[index - 1].queryType === "Select") {
            let selectedColumnWhere = query.selectedColumnWhere;
            let filteredRows;
            switch (query.conditionOperator) {
              case "greater":
                filteredRows = this.currentlySelectedDatabase[
                  this.currentlySelectedTable
                ].filter((row) => {
                  return row[selectedColumnWhere] > query.whereInputSelect;
                });
                break;
              case "less":
                filteredRows = this.currentlySelectedDatabase[
                  this.currentlySelectedTable
                ].filter((row) => {
                  return row[selectedColumnWhere] < query.whereInputSelect;
                });
                break;
              case "equal":
                filteredRows = this.currentlySelectedDatabase[
                  this.currentlySelectedTable
                ].filter((row) => {
                  return row[selectedColumnWhere] == query.whereInputSelect;
                });
                break;
            }
            let filteredColumnObj = [];
            let selectedColumn = Object.keys(this.currentlySelectedColumn[0]);
            for (let row of filteredRows) {
              filteredColumnObj = [
                ...filteredColumnObj,
                { [selectedColumn]: row[selectedColumn] },
              ];
            }

            this.currentlySelectedColumn = filteredColumnObj;
          } else if (queriesObjs[index - 1].queryType === "Delete") {
            this.databaseEngine[this.databaseToDeleteFrom][
              this.tableToDeleteFrom
            ] = this.databaseEngine[this.databaseToDeleteFrom][
              this.tableToDeleteFrom
            ].filter((row) => {
              if (typeof row[query.selectedColumnWhere] === "number") {
                var queryInputNumber = Number.parseInt(query.whereInputDelete);
              } else {
                var queryInputString = query.whereInputDelete;
              }
              switch (query.conditionOperator) {
                case "greater":
                  if (queryInputNumber && !queryInputString) {
                    return row[query.selectedColumnWhere] < queryInputNumber;
                  } else {
                    return row[query.selectedColumnWhere] < queryInputString;
                  }
                case "less":
                  if (queryInputNumber && !queryInputString) {
                    return row[query.selectedColumnWhere] > queryInputNumber;
                  } else {
                    return row[query.selectedColumnWhere] > queryInputString;
                  }
                case "equal":
                  if (queryInputNumber && !queryInputString) {
                    return row[query.selectedColumnWhere] != queryInputNumber;
                  } else {
                    return row[query.selectedColumnWhere] != queryInputString;
                  }
              }
            });
          } else if (queriesObjs[index - 1].queryType === "Update") {
            this.databaseEngine[this.databaseToUpdateFrom][
              this.tableToUpdateFrom
            ].forEach((row) => {
              if (typeof row[query.selectedColumnWhere] === "number") {
                var queryInputNumber = Number.parseInt(query.whereInputUpdate);
              } else {
                var queryInputString = query.whereInputUpdate;
              }
              switch (query.conditionOperator) {
                case "greater":
                  if (queryInputNumber && !queryInputString) {
                    if (row[query.selectedColumnWhere] > queryInputNumber) {
                      this.updateInput.forEach((updatedRow) => {
                        row[updatedRow[0]] = updatedRow[1];
                      });
                    }
                    break;
                  } else {
                    if (row[query.selectedColumnWhere] > queryInputString) {
                      this.updateInput.forEach((updatedRow) => {
                        row[updatedRow[0]] = updatedRow[1];
                      });
                    }
                    break;
                  }
                case "less":
                  if (queryInputNumber && !queryInputString) {
                    if (row[query.selectedColumnWhere] < queryInputNumber) {
                      this.updateInput.forEach((updatedRow) => {
                        row[updatedRow[0]] = updatedRow[1];
                      });
                    }
                    break;
                  } else {
                    if (row[query.selectedColumnWhere] < queryInputString) {
                      this.updateInput.forEach((updatedRow) => {
                        row[updatedRow[0]] = updatedRow[1];
                      });
                    }
                    break;
                  }
                case "equal":
                  if (queryInputNumber && !queryInputString) {
                    if (row[query.selectedColumnWhere] == queryInputNumber) {
                      this.updateInput.forEach((updatedRow) => {
                        row[updatedRow[0]] = updatedRow[1];
                      });
                    }
                    break;
                  } else {
                    if (row[query.selectedColumnWhere] == queryInputString) {
                      this.updateInput.forEach((updatedRow) => {
                        row[updatedRow[0]] = updatedRow[1];
                      });
                    }
                    break;
                  }
              }
            });
          }
        } else if (query.queryType === "Order") {
          let columnsToOrderBy = query.selectedColumns.filter((column) => {
            return column !== "none";
          });
          let ascendingFlag = query.ascendingFlag;
          const selectedTable = [
            ...this.currentlySelectedDatabase[this.currentlySelectedTable],
          ];
          if (ascendingFlag) {
            selectedTable.sort((a, b) => {
              let sortingAsc;

              columnsToOrderBy.forEach((column) => {
                switch (typeof a[column]) {
                  case "number" || "boolean":
                    sortingAsc = sortingAsc || a[column] - b[column];
                    break;
                  case "string":
                    sortingAsc =
                      sortingAsc || a[column].localeCompare(b[column]);
                    break;
                  default:
                    break;
                }
              });

              return sortingAsc;
            });
          } else {
            selectedTable.sort((a, b) => {
              let sortingDsc;
              columnsToOrderBy.forEach((column) => {
                switch (typeof a[column]) {
                  case "number" || "boolean":
                    sortingDsc = sortingDsc || b[column] - a[column];
                    break;
                  case "string":
                    sortingDsc =
                      sortingDsc || b[column].localeCompare(a[column]);
                    break;
                  default:
                    break;
                }
              });
              return sortingDsc;
            });
          }
          this.currentlySelectedDatabase = {
            [this.currentlySelectedTable]: selectedTable,
          };
          const nameOfColumn = Object.keys(this.currentlySelectedColumn[0]);
          let filteredColumn = [];
          let filteredColumnObj = [];
          for (let row of this.currentlySelectedDatabase[
            this.currentlySelectedTable
          ]) {
            filteredColumn = [...filteredColumn, row[nameOfColumn]];
          }
          for (let column of filteredColumn) {
            filteredColumnObj = [
              ...filteredColumnObj,
              { [nameOfColumn]: column },
            ];
          }

          this.currentlySelectedColumn = filteredColumnObj;
        } else if (query.queryType === "Insert") {
          if (
            this.databaseEngine[query.selectedDatabase][query.selectedTable]
              .length == 1 &&
            Object.values(
              this.databaseEngine[query.selectedDatabase][
                query.selectedTable
              ][0]
            ).every((element) => {
              return element === "--";
            })
          ) {
            this.databaseEngine[query.selectedDatabase][query.selectedTable] =
              [];
          }
          this.databaseEngine[query.selectedDatabase][query.selectedTable].push(
            query.inputs
          );
        } else if (query.queryType === "Delete") {
          this.databaseToDeleteFrom = query.selectedDatabase;
          this.tableToDeleteFrom = query.selectedTable;
        } else if (query.queryType === "Update") {
          this.databaseToUpdateFrom = query.selectedDatabase;
          this.tableToUpdateFrom = query.selectedTable;
          this.updateInput = query.updateData;
          if (
            queriesObjs.indexOf(query) + 1 === this.currentBlocks.length ||
            queriesObjs[index + 1].queryType !== "Where"
          ) {
            this.databaseEngine[query.selectedDatabase][
              query.selectedTable
            ].forEach((row) => {
              this.updateInput.forEach((updatedRow) => {
                row[updatedRow[0]] = updatedRow[1];
              });
            });
          }
        } else if (query.queryType === "Drop") {
          delete this.databaseEngine[query.selectedDatabase][
            query.selectedTable
          ];
        } else if (query.queryType === "Truncate") {
          const tableAfterTruncate = {};
          for (let key of Object.keys(
            this.databaseEngine[query.selectedDatabase][query.selectedTable][0]
          )) {
            tableAfterTruncate[key] = "--";
          }
          this.databaseEngine[query.selectedDatabase][query.selectedTable] = [
            tableAfterTruncate,
          ];
        } else if (query.queryType === "Create Table") {
          this.databaseEngine[query.selectedDatabase][query.newTableData[0]] = [
            query.newTableData[1],
          ];
        } else if (query.queryType === "Create Database") {
          this.databaseEngine[query.newDatabaseData[0]] =
            query.newDatabaseData[1];
        }
      });
    },
    executeRequest() {
      this.executeClicked = true;

      this.emitter.on("save-query-data", (queryData) => {
        this.queries = [...this.queries, queryData];
      });
      setTimeout(this.execute, 200);
      setTimeout(() => {
        this.executeClicked = false;
      }, 500);
    },
  },
  mounted() {
    this.emitter.on("select-pass-table-column-to-button", (selectedCol) => {
      this.selectedColumnForSelect = selectedCol;
    });
    this.emitter.on("update-pass-last-input-to-button", (isTriggered) => {
      this.isUpdateLastInputTriggered = isTriggered;
    });

    this.emitter.on("create-query", (newClicks) => {
      this.clicks = newClicks;
    });
    this.emitter.on("update-blocks", (newBlocks) => {
      this.currentBlocks = newBlocks;
    });
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.badge {
  width: fit-content;
}
.fs-4 {
  margin-bottom: 0;
  text-align: center;
}
nav {
  background-color: rgb(177, 177, 177);
  margin-bottom: 10vh;
}
</style>
