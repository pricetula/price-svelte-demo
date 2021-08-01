<script lang="ts">
  import { name } from "faker";
  import { route } from "../utils/route";
  import Button from "../components/Button.svelte";

  let buttonClicked: number = 0;

  const clickedHandler = () => (buttonClicked += 1); // Constant value will change whenever the function is clicked making it reactive

  // $: used to state that variable should be reactive and will be evaluated every time before component updates
  // if any value in the statement changes
  $: userList =
    buttonClicked > 3 // buttonClicked value changes this makes it a dependency for userList to be reactive
      ? []
      : Array.from({ length: 4 }, (a, k) => ({
          id: k + 1,
          firstName: name.firstName(),
          lastName: name.lastName(),
        }));

  $: {
    console.log(`Will always log when "buttonClicked" reactive statement changes. buttonClicked = ${buttonClicked}`)
  }
</script>

<article>
  <header class="is-flex is-flex-direction-column is-justify-content-center is-align-items-center header">
    <h1 class="title is-1 has-text-primary">Bulma & svelte</h1>
    <h2 class="title is-4">Simple web app built using Svelte and Bulma CSS</h2>
  </header>
  <Button click={clickedHandler}>Button clicked {buttonClicked} times</Button>
  <ul>
    <!-- Iterate over list, each item is set to user variable and the key to be used is user.id -->
    {#each userList as user (user.id)}
      <li>{user.firstName} {user.lastName}</li>
    {:else}
      <li>No list available</li>
    {/each}
  </ul>
</article>

<style lang="scss">
   @import "src/style/partial/index.scss";

  .header {
    padding: pxToRem(30px) pxToRem(40px) pxToRem(20px);
    & > h1 {
      text-align: center;
    }
  }
</style>
