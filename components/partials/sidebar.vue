<template>
  <div class="main-sidebar">
    <aside id="sidebar-wrapper">
      <div class="sidebar-brand">
        <a href="index.html">Stisla</a>
      </div>
      <div class="sidebar-brand sidebar-brand-sm">
        <a href="index.html">St</a>
      </div>
      <ul class="sidebar-menu">
        <li class="menu-header">Dashboard</li>
        <li class="nav-item dropdown">
          <a href="#" class="nav-link has-dropdown"><i class="fas fa-fire"></i><span>Dashboard</span></a>
          <ul class="dropdown-menu">
            <li><a class="nav-link" href="index-0.html">General Dashboard</a></li>
            <li><a class="nav-link" href="index.html">Ecommerce Dashboard</a></li>
          </ul>
        </li>
        <li>
          <nuxt-link class="nav-link" to="/"><i class="far fa-square"></i> <span>Dashboard</span></nuxt-link>
        </li>
        <li>
          <nuxt-link class="nav-link" to="/users"><i class="far fa-square"></i> <span>User</span></nuxt-link>
        </li>
      </ul>
    </aside>
  </div>
</template>