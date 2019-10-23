<template>
  <div class="app-header">
    <span>MASTERMIND</span>
    <nav class="nav">
      <ul class="nav__list">
        <li v-for="route in routes" :key="route.name">
          <RouterLink
            class="nav__list-item"
            exact-active-class="nav__list-item--active"
            :to="{ name: route.name || route.meta.defaultName }"
          >{{ route.meta.displayName }}</RouterLink>
        </li>
      </ul>
    </nav>
  </div>
</template>

<script>
import routes from "../routes";

export default {
  name: "AppHeader",
  data() {
    return {
      routes
    };
  }
};
</script>

<style lang="scss">
.app-header {
  width: 100vw;
  max-width: 2500px;
  height: 80px;
  background-color: #4e6c90;
  display: flex;
  justify-content: space-between;

  span {
    color: #fff;
    font-size: 32px;
    padding-top: 20px;
    padding-left: 10px;
  }
}

.nav {
  &__list {
    display: flex;
    justify-content: space-between;
    list-style: none;
    padding: 1.5em;
    &-item {
      text-decoration: none;
      padding: 0.5em 1em;
      font-size: 20px;
      color: white;
      height: 40px;
      &--active {
        background-color: white;
        color: #4e6c90;
        border-radius: 5px;
      }
    }
  }
}
</style>