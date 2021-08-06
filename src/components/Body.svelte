<article class="body">
  <slot />
</article>

<style lang="scss">
  @import "src/style/partial/index.scss";

  .body {
    margin-top: $nav-height;
    min-height: pxToRem(900px);
  }
</style>