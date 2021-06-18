<template>
  <nav class="navbar navbar-expand-lg navbar-light bg-warning">
    <div class="container-fluid">
      <router-link class="navbar-brand" to="/">導覽列</router-link>
      <div class="collapse navbar-collapse" id="navbarNav">
        <ul class="navbar-nav">
          <li class="nav-item">
            <router-link to="/About" class="nav-link active">About</router-link>
          </li>
          <li class="nav-item">
            <router-link to="/Products" class="nav-link">產品</router-link>
          </li>
        </ul>
      </div>
    </div>
  </nav>
  <div class="container text-center">
    <h1 class="py-3">前台</h1>
  </div>
  <router-view></router-view>
</template>
