<script>
  import { route } from "../utils/route";

  const routeList = Object.values(route)
</script>

<nav class="is-flex is-align-items-center is-justify-content-space-between nav">
  <a
    class="logo"
    href={route.HOME.path}
  >
    Price Svelte Demo
  </a>
  <ul class="is-flex is-justify-content-space-between links">
    {#each routeList as r (r.label)}
      <li>
        <a href={r.path}>{r.label}</a>
      </li>
    {/each}
  </ul>
</nav>

<style lang="scss">
  @import "src/style/partial/index.scss";

  .nav {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    z-index: 2;
    background-color: $midnight-blue;
    min-height: $nav-height;
    padding: 0 pxToRem(50px);

    & > .logo {
      @include font(14px, bold, white);
    }

    & > .links {
      & > li {
        &:not(:last-of-type) {
          margin-right: pxToRem(10px);
        }
        & > a {
          @include font(14px, normal, white);
          opacity: 0.6;
          &:hover {
            opacity: 1;
          }
        }
      }
    }
  }
</style>