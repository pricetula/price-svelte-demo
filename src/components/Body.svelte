<article class="body">
  <slot />
</article>

<style lang="scss">
  @import "src/style/partial/index.scss";

  .body {
    min-height: pxToRem(900px);
  }
</style>