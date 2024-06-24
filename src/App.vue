<template>
  <q-layout view="hHh lpR fFf">
    <q-header elevated>
      <q-toolbar class="custom-toolbar">
        <q-btn-dropdown class="custom-dropdown" label="Daftar Tugas" dropdown-icon="^">
          <q-list class="nav-list">
            <q-item clickable v-close-popup>
              <router-link to="/">
                <q-item-section>
                  <q-item-label style="color: #00bfff;">Weather</q-item-label>
                </q-item-section>
              </router-link>
            </q-item>
            <q-item clickable v-close-popup>
              <router-link to="/tugas4">
                <q-item-section>
                  <q-item-label style="color: #00bfff;">Tugas 4</q-item-label>
                </q-item-section>
              </router-link>
            </q-item>
          </q-list>
        </q-btn-dropdown>
      </q-toolbar>
    </q-header>

    <q-page-container>
      <router-view></router-view>
    </q-page-container>
  </q-layout>
</template>

<script>
export default {
  setup() {}
};
</script>

<style scoped>
@import './assets/index.css';

.custom-toolbar {
  background-color: whitesmoke;
  color: #00bfff;
  text-decoration: none;
  padding: 15px;
}

.custom-dropdown {
  background-color: whitesmoke;
  color: #00bfff;
}

.nav-list {
  background-color: whitesmoke;
  color: #00bfff;
}

.nav-list .q-item-link {
  text-decoration: none;
}

.q-item-section {
  color: whitesmoke !important;
}
</style>
