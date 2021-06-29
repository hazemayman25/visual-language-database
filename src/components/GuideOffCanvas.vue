<template>
  <div
    class="offcanvas offcanvas-bottom"
    tabindex="-1"
    id="offcanvasBottomSelect"
    aria-labelledby="offcanvasBottomLabel"
  >
    <div class="offcanvas-header">
      <h3 class="offcanvas-title" id="offcanvasBottomLabel">
        SELECT
      </h3>
      <button
        type="button"
        class="btn-close text-reset"
        data-bs-dismiss="offcanvas"
        aria-label="Close"
      ></button>
    </div>
    <div class="offcanvas-body small d-flex flex-column align-items-start">
      <p>
        The <span style="color: red;">SELECT</span> statement is used to select
        data from a database.
      </p>
      <p>
        The data returned is stored in a result table, called the result-set.
      </p>
      <br />
      <p>Selecting data is achieved easily by doing the following:</p>
      <ol class="d-flex flex-column align-items-start">
        <li>Click on the "Select" button on the Blocks Group</li>
        <li>
          After seeing a query block appear on the Queries Container, specify
          which database you need to access
        </li>
        <li>Specify which table you want to access</li>
        <li>Specify which column you want to access</li>
      </ol>
      <p>
        <strong>Note: </strong>If you did not select a column, all the columns
        will be viewed
      </p>
      <br />
      <p>
        By default the selection query will show you the whole column. If you
        want specific entries you can put a restriction using the
        <span style="color: red;">WHERE</span> clause, also you can sort your
        selections using <span style="color: red;">ORDER BY</span>
      </p>
    </div>
  </div>

  <div
    class="offcanvas offcanvas-bottom"
    tabindex="-1"
    id="offcanvasBottomWhere"
    aria-labelledby="offcanvasBottomLabel"
  >
    <div class="offcanvas-header">
      <h3 class="offcanvas-title" id="offcanvasBottomLabel">
        WHERE
      </h3>
      <button
        type="button"
        class="btn-close text-reset"
        data-bs-dismiss="offcanvas"
        aria-label="Close"
      ></button>
    </div>
    <div class="offcanvas-body small d-flex flex-column align-items-start">
      <p>
        The WHERE clause is used to filter records.
      </p>
      <p>
        It is used to extract only those records that fulfill a specified
        condition.
      </p>
      <br />
      <p>
        <strong>Note: </strong>The WHERE clause is not only used in
        <span style="color: red;">SELECT</span> statements, it is also used in
        <span style="color: red;">UPDATE</span>,
        <span style="color: red;">DELETE</span>, etc.!
      </p>
      <br />
      <p>
        Where clause is automatically called after a
        <span style="color: red;">DELETE</span> query, but for
        <span style="color: red;">SELECT</span> and
        <span style="color: red;">UPDATE</span> works by your choice
      </p>
      <p>
        If you want to use it by your choice, the
        <span style="color: red;">WHERE</span> clause works as the following:
      </p>
      <ol class="d-flex flex-column align-items-start">
        <li>Click on the "Where" button on the Blocks Group</li>
        <li>
          After seeing a query block appear on the Queries Container, specify
          which column you need to put a restriction on
        </li>
        <li>Specify the operator you want to use</li>
        <li>
          Specify the value you want to compare with the chosen column
        </li>
      </ol>
    </div>
  </div>

  <div
    class="offcanvas offcanvas-bottom"
    tabindex="-1"
    id="offcanvasBottomInsert"
    aria-labelledby="offcanvasBottomLabel"
  >
    <div class="offcanvas-header">
      <h3 class="offcanvas-title" id="offcanvasBottomLabel">
        INSERT
      </h3>
      <button
        type="button"
        class="btn-close text-reset"
        data-bs-dismiss="offcanvas"
        aria-label="Close"
      ></button>
    </div>
    <div class="offcanvas-body small d-flex flex-column align-items-start">
      <p>
        The <span style="color: red;">INSERT</span> statement is used to insert
        new records in a table.
      </p>
      <br />
      <p>
        <span style="color: red;">INSERT</span> query works as the following:
      </p>
      <ol class="d-flex flex-column align-items-start">
        <li>Click on the "Insert" button on the Blocks Group</li>
        <li>
          After seeing a query block appear on the Queries Container, specify
          which database you want to access
        </li>
        <li>Specify the table you want to add data to</li>
        <li>
          You will then be given input slots that vary according to the table
          data, the number of columns for the table for instance, Use those
          slots to fill the data you wish to enter
        </li>
      </ol>
    </div>
  </div>

  <div
    class="offcanvas offcanvas-bottom"
    tabindex="-1"
    id="offcanvasBottomDelete"
    aria-labelledby="offcanvasBottomLabel"
  >
    <div class="offcanvas-header">
      <h3 class="offcanvas-title" id="offcanvasBottomLabel">
        DELETE
      </h3>
      <button
        type="button"
        class="btn-close text-reset"
        data-bs-dismiss="offcanvas"
        aria-label="Close"
      ></button>
    </div>
    <div class="offcanvas-body small d-flex flex-column align-items-start">
      <p>
        The <span style="color: red;">DELETE</span> statement is used to delete
        existing records in a table.
      </p>
      <br />
      <p>
        The <span style="color: red;">DELETE</span> query works as the
        following:
      </p>
      <ol class="d-flex flex-column align-items-start">
        <li>Click on the "Delete" button on the Blocks Group</li>
        <li>
          After seeing a query block appear on the Queries Container, specify
          which database you want to access
        </li>
        <li>Specify the table you want to add data to</li>
        <li>
          You will then be asked to put a condition through the automated
          <span style="color: red;">WHERE</span> clause
        </li>
        <li>
          put the condition you want as a way to specify which records you want
          to delete
        </li>
      </ol>
    </div>
  </div>

  <div
    class="offcanvas offcanvas-bottom"
    tabindex="-1"
    id="offcanvasBottomOrderBy"
    aria-labelledby="offcanvasBottomLabel"
  >
    <div class="offcanvas-header">
      <h3 class="offcanvas-title" id="offcanvasBottomLabel">
        ORDER BY
      </h3>
      <button
        type="button"
        class="btn-close text-reset"
        data-bs-dismiss="offcanvas"
        aria-label="Close"
      ></button>
    </div>
    <div class="offcanvas-body small d-flex flex-column align-items-start">
      <p>
        The <span style="color: red;">ORDER BY</span> statement is used to sort
        the result-set in ascending or descending order.
      </p>
      <br />
      <p>
        <strong>NOTE:</strong> This statement is only available after calling
        the <span style="color: red;">SELECT</span> query
      </p>
      <p>
        The <span style="color: red;">ORDER BY</span> query works as the
        following:
      </p>
      <ol class="d-flex flex-column align-items-start">
        <li>Click on the "Order" button on the Blocks Group</li>
        <li>
          After seeing a query block appear on the Queries Container, you will
          be asked to choose a number of columns you want to sort by. The
          priority is highest from <strong>LEFT</strong> to
          <strong>RIGHT</strong>
        </li>
        <li>Specify the columns you want to sort by</li>
        <li>
          Specify whether you want to sort the selected column
          <strong>ASCENDINGLY</strong> or <strong>DESCENDINGLY</strong>
        </li>
      </ol>
    </div>
  </div>

  <div
    class="offcanvas offcanvas-bottom"
    tabindex="-1"
    id="offcanvasBottomUpdate"
    aria-labelledby="offcanvasBottomLabel"
  >
    <div class="offcanvas-header">
      <h3 class="offcanvas-title" id="offcanvasBottomLabel">
        UPDATE
      </h3>
      <button
        type="button"
        class="btn-close text-reset"
        data-bs-dismiss="offcanvas"
        aria-label="Close"
      ></button>
    </div>
    <div class="offcanvas-body small d-flex flex-column align-items-start">
      <p>
        The <span style="color: red;">UPDATE</span> statement is used to modify
        the existing records in a table.
      </p>
      <br />
      <p>
        <strong>NOTE:</strong> You can modify certain records by specifying a
        condition by using the <span style="color: red;">WHERE</span> query
      </p>
      <br />
      <p>
        The <span style="color: red;">UPDATE</span> query works as the
        following:
      </p>
      <ol class="d-flex flex-column align-items-start">
        <li>Click on the "Update" button on the Blocks Group</li>
        <li>
          After seeing a query block appear on the Queries Container, you will
          be asked to choose the database you want to access
        </li>
        <li>Specify the table you want to update</li>
        <li>
          Specify how many columns you want to update
        </li>
        <li>
          you will be given some input slots. Each slot requires a certain
          column input and the value you need to put in that column
        </li>
      </ol>
      <br />
      <p>
        <strong>NOTE:</strong> Calling the
        <span style="color: red;">UPDATE</span> query without a
        <span style="color: red;">WHERE</span> clause will update all the
        records in the chosen column/s
      </p>
    </div>
  </div>

  <div
    class="offcanvas offcanvas-bottom"
    tabindex="-1"
    id="offcanvasBottomDrop"
    aria-labelledby="offcanvasBottomLabel"
  >
    <div class="offcanvas-header">
      <h3 class="offcanvas-title" id="offcanvasBottomLabel">
        DROP
      </h3>
      <button
        type="button"
        class="btn-close text-reset"
        data-bs-dismiss="offcanvas"
        aria-label="Close"
      ></button>
    </div>
    <div class="offcanvas-body small d-flex flex-column align-items-start">
      <p>
        The <span style="color: red;">DROP</span> statement is used to drop an
        existing table in a database.
      </p>
      <br />
      <p>
        <strong>NOTE:</strong> Unlike the
        <span style="color: red;">TRUNCATE</span> query, which empties the table
        btu leaves its definition, the
        <span style="color: red;">DROP</span> query removes the table definition
        and its contents.
      </p>
      <br />
      <p>
        The <span style="color: red;">DROP</span> query works as the following:
      </p>
      <ol class="d-flex flex-column align-items-start">
        <li>Click on the "Drop" button on the Blocks Group</li>
        <li>
          After seeing a query block appear on the Queries Container, you will
          be asked to choose the database you want to access
        </li>
        <li>Specify the table you want to remove</li>
      </ol>
    </div>
  </div>

  <div
    class="offcanvas offcanvas-bottom"
    tabindex="-1"
    id="offcanvasBottomTruncate"
    aria-labelledby="offcanvasBottomLabel"
  >
    <div class="offcanvas-header">
      <h3 class="offcanvas-title" id="offcanvasBottomLabel">
        TRUNCATE
      </h3>
      <button
        type="button"
        class="btn-close text-reset"
        data-bs-dismiss="offcanvas"
        aria-label="Close"
      ></button>
    </div>
    <div class="offcanvas-body small d-flex flex-column align-items-start">
      <p>
        The <span style="color: red;">TRUNCATE</span> command deletes the data
        inside a table, but not the table itself.
      </p>
      <br />
      <p>
        <strong>NOTE:</strong> Unlike the
        <span style="color: red;">DROP</span> query, which removes the table
        definition and its contents, the
        <span style="color: red;">DROP</span> query empties the table btu leaves
        its definition.
      </p>
      <br />
      <p>
        The <span style="color: red;">TRUNCATE</span> query works as the
        following:
      </p>
      <ol class="d-flex flex-column align-items-start">
        <li>Click on the "Truncate" button on the Blocks Group</li>
        <li>
          After seeing a query block appear on the Queries Container, you will
          be asked to choose the database you want to access
        </li>
        <li>Specify the table you want to empty</li>
      </ol>
    </div>
  </div>

  <div
    class="offcanvas offcanvas-bottom"
    tabindex="-1"
    id="offcanvasBottomCreateTable"
    aria-labelledby="offcanvasBottomLabel"
  >
    <div class="offcanvas-header">
      <h3 class="offcanvas-title" id="offcanvasBottomLabel">
        CREATE TABLE
      </h3>
      <button
        type="button"
        class="btn-close text-reset"
        data-bs-dismiss="offcanvas"
        aria-label="Close"
      ></button>
    </div>
    <div class="offcanvas-body small d-flex flex-column align-items-start">
      <p>
        The <span style="color: red;">CREATE TABLE</span> command creates a new
        table in the database.
      </p>
      <br />
      <p>
        The <span style="color: red;">CREATE TABLE</span> query works as the
        following:
      </p>
      <ol class="d-flex flex-column align-items-start">
        <li>Click on the "Create Table" button on the Blocks Group</li>
        <li>
          After seeing a query block appear on the Queries Container, you will
          be asked to choose the database you want to access
        </li>
        <li>
          Write the name you desire for the new table on the input field that
          will appear once you choose the database
        </li>
        <li>
          Specify the number of columns you want for that table
        </li>
        <li>
          Write the names you want for the columns you want to create
        </li>
      </ol>
    </div>
  </div>

  <div
    class="offcanvas offcanvas-bottom"
    tabindex="-1"
    id="offcanvasBottomCreateDatabase"
    aria-labelledby="offcanvasBottomLabel"
  >
    <div class="offcanvas-header">
      <h3 class="offcanvas-title" id="offcanvasBottomLabel">
        CREATE DATABASE
      </h3>
      <button
        type="button"
        class="btn-close text-reset"
        data-bs-dismiss="offcanvas"
        aria-label="Close"
      ></button>
    </div>
    <div class="offcanvas-body small d-flex flex-column align-items-start">
      <p>
        The <span style="color: red;">CREATE DATABASE</span> command creates a
        new database in the engine.
      </p>
      <br />
      <p>
        The <span style="color: red;">CREATE DATABASE</span> query works as the
        following:
      </p>
      <ol class="d-flex flex-column align-items-start">
        <li>Click on the "Create Database" button on the Blocks Group</li>
        <li>
          Write the name you desire for the new database on the input field
        </li>
      </ol>
    </div>
  </div>

  <div
    class="offcanvas offcanvas-bottom"
    tabindex="-1"
    id="offcanvasBottomHelp"
    aria-labelledby="offcanvasBottomLabel"
  >
    <div class="offcanvas-header">
      <div class="d-flex flex-column align-items-center" style="width: 100%;">
        <h1 class="offcanvas-title" id="offcanvasBottomLabel">
          <strong>vSQL</strong>
        </h1>
        <sub class="fw-light text-dark">
          Inspired from Scratch
        </sub>
      </div>
      <button
        type="button"
        class="btn-close text-reset"
        data-bs-dismiss="offcanvas"
        aria-label="Close"
      ></button>
    </div>
    <div class="offcanvas-body small d-flex flex-column align-items-start">
      <p>
        Welcome to vSQL, a free Visual Programming language that helps us
        understand how the real SQL databases work.
      </p>
      <br />
      <p>
        the language works in the shape of blocks so that it can be easier for
        the user to manipulate queries.
      </p>
      <p>The language works as the following:</p>
      <ol class="d-flex flex-column align-items-start">
        <li>
          You have to select a button from a group of buttons on the left side
          on a container known as <strong>Blocks Group</strong>
        </li>
        <li>
          each button represents a SQL query, once clicked it will generate a
          block with an equivalent meaning to the button selected and place it
          on the middle container known as <strong>Queries Container</strong>
        </li>
        <li>
          After choosing certain blocks to execute, after pressing
          <strong>Execute</strong> you can see the results from the container on
          the right side known as <strong>Engine Canvas</strong>
        </li>
        <li>
          <div class="d-flex flex-column align-items-start">
            <p>
              The <strong>Engine Canvas</strong> will display results in two
              ways:
            </p>
            <ul class="d-flex flex-column align-items-start">
              <li>
                The top dropdown menus that require you to select any table to
                view
              </li>
              <li>
                The last <span style="color: red;">SELECT</span> query executed
              </li>
            </ul>
          </div>
        </li>
      </ol>
    </div>
  </div>
  <div
    class="offcanvas offcanvas-bottom"
    tabindex="-1"
    id="offcanvasBottomOurTeam"
    aria-labelledby="offcanvasBottomLabel"
  >
    <div class="offcanvas-header">
      <h3 class="offcanvas-title" id="offcanvasBottomLabel">
        OUR TEAM:
      </h3>
      <button
        type="button"
        class="btn-close text-reset"
        data-bs-dismiss="offcanvas"
        aria-label="Close"
      ></button>
    </div>
    <div class="offcanvas-body small d-flex flex-column align-items-start">
      <ul class="d-flex flex-column align-items-start">
        <li>Hazem Ayman 40-11085</li>
        <li>
          Ahmed Emad 40-2273
        </li>
        <li>Abdullah Mahmoud 40-4264</li>
        <li>
          Ahmed Halawa 40-3185
        </li>
        <li>
          Omar Mahmoud 40-3063
        </li>
        <li>
          Karim Fekry 40-2242
        </li>
      </ul>
    </div>
  </div>
</template>
