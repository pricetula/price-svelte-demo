<script lang="ts">
  import Nav from "../components/Nav.svelte";
  import Body from "../components/Body.svelte";
  import Footer from "../components/Footer.svelte";
</script>

<main>
  <Nav />
  <Body>
    <slot />
  </Body>
  <Footer />
</main>

<style lang="scss">
  @import "src/style/global.scss";
</style>
