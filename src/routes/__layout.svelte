<script lang="ts">
  import Nav from "../components/Nav.svelte";
  import Footer from "../components/Footer.svelte";
</script>

<main>
  <Nav />
  <slot />
  <Footer />
</main>

<style lang="scss">
  @import "src/style/global.scss";
</style>
