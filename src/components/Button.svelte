<script lang="ts">
  export let click: (e: MouseEvent & { currentTarget: EventTarget & HTMLButtonElement; }) => any
</script>
<button
  on:click={click}
  class="button"
>
  <slot />
</button>