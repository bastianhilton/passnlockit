<template>
  <Header>
    <!-- Navbar -->
    <nav id="main-navbar" class="navbar navbar-expand-lg navbar-light bg-white fixed-top">
      <!-- Container wrapper -->
      <div class="container-fluid">
        <!-- Toggle button -->
        <button class="navbar-toggler" type="button" data-mdb-toggle="collapse"
          data-mdb-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false"
          aria-label="Toggle navigation">
          <i class="fas fa-bars"></i>
        </button>

        <!-- Collapsible wrapper -->
        <div class="collapse navbar-collapse" id="navbarSupportedContent">
          <!-- Navbar brand -->
          <a class="navbar-brand" href="/">
          <div class="metroname" style="color:yellow;">Pass</div>
          <div class="metroname" style="color:powderblue;">nLockit</div>
        </a>
        </div>
        <!-- Collapsible wrapper -->
        <!-- Search form -->
        <div class="collapse navbar-collapse justify-content-center" id="navbarCenteredExample">
          <MainSearch />
        </div>
        <!-- Right elements -->
        <div class="d-flex align-items-center">
          <!-- Icon -->
          <ul class="navbar-nav me-auto mb-2 mb-lg-0" style="padding-right: 15px;">
            <div class="dropdown">
              <button class="btn btn-warning dropdown-toggle" type="button" id="dropdownMenu2"
                data-mdb-toggle="dropdown" aria-expanded="false">
                Menu
              </button>
              <ul class="dropdown-menu createDrop" aria-labelledby="dropdownMenu2">
                <li>
                  <a class="dropdown-item" href="/">Passwords</a>
                </li>
                <li>
                  <a class="dropdown-item" href="/notes">Notes</a>
                </li>
                <li>
                  <a class="dropdown-item" href="/categories">Categories</a>
                </li>
                <hr />
                <li>
                  <a class="dropdown-item" href="/security">Security Dashboard</a>
                </li>
                <li>
                  <a class="dropdown-item" href="/sites">Sites</a>
                </li>
                <li>
                  <a class="dropdown-item" href="/help">Help</a>
                </li>
              </ul>
            </div>
          </ul>
          <!-- Create -->
          <div class="dropdown">
            <a class="text-reset me-3 dropdown-toggle hidden-arrow" href="#" id="navbarDropdownMenuLink" role="button"
              data-mdb-toggle="dropdown" aria-expanded="false" style="color: white !important;">
              Create
            </a>
            <ul class="dropdown-menu dropdown-menu-end" aria-labelledby="navbarDropdownMenuLink">
              <li>
                <a class="dropdown-item" href="/create/password">Create Password</a>
              </li>
              <li>
                <a class="dropdown-item" href="/create/note">Create Note</a>
              </li>
            </ul>
          </div>
          <!-- Avatar -->
          <div class="dropdown">
            <a class="dropdown-toggle d-flex align-items-center hidden-arrow" href="#" id="navbarDropdownMenuAvatar"
              role="button" data-mdb-toggle="dropdown" aria-expanded="false">
              <img src="https://mdbcdn.b-cdn.net/img/new/avatars/2.webp" class="rounded-circle" height="25"
                alt="Black and White Portrait of a Man" loading="lazy" />
            </a>
            <ul class="dropdown-menu dropdown-menu-end" aria-labelledby="navbarDropdownMenuAvatar">
              <li>
                <a class="dropdown-item" href="/user/">My profile</a>
              </li>
              <li>
                <a class="dropdown-item" href="/user/my-passwords">My Passwords</a>
              </li>
              <li>
                <a class="dropdown-item" href="/user/my-notes">My Notes</a>
              </li>
              <li>
                <a class="dropdown-item" href="#">Logout</a>
              </li>
            </ul>
          </div>
        </div>
        <!-- Right elements -->
      </div>
      <!-- Container wrapper -->
    </nav>
    <!-- Navbar -->
  </Header>
</template>

<script>
  import MainSearch from '~/components/MainSearch.vue'

  export default {
    components: {
      MainSearch
    },
    name: 'IndexPage'
  }

</script>
