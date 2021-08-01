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

<main>
  <h1 class="title">Price svelte demo</h1>
  <p>Checkout <a href={route.CHARTS.path}>charts</a> page.</p>
  <Button click={clickedHandler}>Button clicked {buttonClicked} times</Button>
  <ul>
    <!-- Iterate over list, each item is set to user variable and the key to be used is user.id -->
    {#each userList as user (user.id)}
      <li>{user.firstName} {user.lastName}</li>
    {:else}
      <li>No list available</li>
    {/each}
  </ul>
</main>
