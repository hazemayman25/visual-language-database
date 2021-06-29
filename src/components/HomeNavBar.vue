<template>
  <nav class="navbar navbar-expand-lg navbar-light">
    <div class="container-fluid">
      <div style="width:100%;" class="row">
        <div class="col-3 mb-2 d-flex justify-content-start">
          <div class="d-flex flex-column align-items-center">
            <a
              style="margin-right: 0;"
              class="navbar-brand fw-bold"
              href="#"
              @click="forceRerender"
              >vSQL</a
            >
            <sub class="fw-light text-dark">
              Inspired from Scratch
            </sub>
          </div>

          <button
            class="navbar-toggler"
            type="button"
            data-bs-toggle="collapse"
            data-bs-target="#navbarSupportedContent"
            aria-controls="navbarSupportedContent"
            aria-expanded="false"
            aria-label="Toggle navigation"
          >
            <span class="navbar-toggler-icon"></span>
          </button>
        </div>
        <div class="col-6 d-flex justify-content-between align-items-center">
          <div
            class="collapse navbar-collapse justify-content-center"
            id="navbarSupportedContent"
          >
            <ul class="navbar-nav mb-2 mb-lg-0">
              <li class="nav-item">
                <a
                  class="nav-link active"
                  href="#"
                  data-bs-toggle="offcanvas"
                  data-bs-target="#offcanvasBottomHelp"
                  >Help</a
                >
              </li>

              <li class="nav-item dropdown">
                <a
                  class="nav-link active dropdown-toggle"
                  href="#"
                  id="navbarDropdown"
                  role="button"
                  data-bs-toggle="dropdown"
                  aria-expanded="false"
                >
                  Queries Guide
                </a>
                <ul class="dropdown-menu" aria-labelledby="navbarDropdown">
                  <li>
                    <a
                      class="dropdown-item"
                      href="#"
                      data-bs-toggle="offcanvas"
                      data-bs-target="#offcanvasBottomSelect"
                      aria-controls="offcanvasBottom"
                      >Select</a
                    >
                  </li>
                  <li>
                    <a
                      class="dropdown-item"
                      href="#"
                      data-bs-toggle="offcanvas"
                      data-bs-target="#offcanvasBottomWhere"
                      aria-controls="offcanvasBottom"
                      >Where</a
                    >
                  </li>
                  <li>
                    <a
                      class="dropdown-item"
                      href="#"
                      data-bs-toggle="offcanvas"
                      data-bs-target="#offcanvasBottomInsert"
                      aria-controls="offcanvasBottom"
                      >Insert</a
                    >
                  </li>
                  <li>
                    <a
                      class="dropdown-item"
                      href="#"
                      data-bs-toggle="offcanvas"
                      data-bs-target="#offcanvasBottomDelete"
                      >Delete</a
                    >
                  </li>
                  <li>
                    <a
                      class="dropdown-item"
                      href="#"
                      data-bs-toggle="offcanvas"
                      data-bs-target="#offcanvasBottomOrderBy"
                      >Order By</a
                    >
                  </li>
                  <li>
                    <a
                      class="dropdown-item"
                      href="#"
                      data-bs-toggle="offcanvas"
                      data-bs-target="#offcanvasBottomUpdate"
                      >Update</a
                    >
                  </li>
                  <li>
                    <a
                      class="dropdown-item"
                      href="#"
                      data-bs-toggle="offcanvas"
                      data-bs-target="#offcanvasBottomDrop"
                      >Drop</a
                    >
                  </li>
                  <li>
                    <a
                      class="dropdown-item"
                      href="#"
                      data-bs-toggle="offcanvas"
                      data-bs-target="#offcanvasBottomTruncate"
                      >Truncate</a
                    >
                  </li>
                  <li>
                    <a
                      class="dropdown-item"
                      href="#"
                      data-bs-toggle="offcanvas"
                      data-bs-target="#offcanvasBottomCreateTable"
                      >Create Table</a
                    >
                  </li>
                  <li>
                    <a
                      class="dropdown-item"
                      href="#"
                      data-bs-toggle="offcanvas"
                      data-bs-target="#offcanvasBottomCreateDatabase"
                      >Create Database</a
                    >
                  </li>
                </ul>
              </li>
              <li class="nav-item">
                <a
                  class="nav-link active"
                  href="#"
                  data-bs-toggle="offcanvas"
                  data-bs-target="#offcanvasBottomOurTeam"
                  aria-controls="offcanvasBottom"
                  >Our Team</a
                >
              </li>
            </ul>
          </div>
        </div>
        <div class="col-3"></div>
      </div>
    </div>
  </nav>
</template>

<script>
export default {};
</script>
