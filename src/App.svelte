<script>
  let first_name = "sajid";
  let second_name = "amin";

  $: name = `${first_name} ${second_name}`;
  let color = "blue";
  let showText = false;

  let users = [
    {
      id: 1,
      name: "sajid",
    },
    {
      id: 2,
      name: "ali",
    },
  ];

  function toggleColor() {
    color = color === "green" ? "blue" : "green";
    showText = !showText;
    users = [...users, { id: 3, name: "usama" }];
  }
</script>

<main>
  <h1>Hello <span style="color: {color}">{name}!</span></h1>
  {#if showText}
    <p>
      Visit the <a href="https://svelte.dev/tutorial">Svelte tutorial</a> to learn
      how to build Svelte apps.
    </p>
  {:else}
    <p>For Furher Click Button</p>
  {/if}
  <button on:click={toggleColor}>Change Color</button>

  {#each users as user (user.id)}
    <h3>
      {user.id}: {user.name}
    </h3>
  {/each}
</main>

<style>
  main {
    text-align: center;
    padding: 1em;
    max-width: 240px;
    margin: 0 auto;
  }

  h1 {
    color: #ff3e00;
    text-transform: uppercase;
    font-size: 4em;
    font-weight: 100;
  }

  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }
</style>
