<script>
  import Router, { link } from "svelte-spa-router";
  import { routes } from "./routes.js";
  import { onMount } from "svelte";
  import { Alert } from "flowbite-svelte";
  let data;
  async function fetchData() {
    const response = await fetch(import.meta.env.VITE_API_ENDPOINT);
    data = await response.json();
  }

  onMount(fetchData);
</script>

<div class="p-8 overflow-hidden bg-gray-50 dark:bg-gray-900">
  <h1 class="text-4xl">
    Vite + Svelte + TailwindCSS/Flowbite + svelte-spa-router
  </h1>
  <Router {routes} />
  <Alert dismissable>
    <span slot="icon"
      ><svg
        aria-hidden="true"
        class="w-5 h-5"
        fill="currentColor"
        viewBox="0 0 20 20"
        xmlns="http://www.w3.org/2000/svg"
        ><path
          fill-rule="evenodd"
          d="M18 10a8 8 0 11-16 0 8 8 0 0116 0zm-7-4a1 1 0 11-2 0 1 1 0 012 0zM9 9a1 1 0 000 2v3a1 1 0 001 1h1a1 1 0 100-2v-3a1 1 0 00-1-1H9z"
          clip-rule="evenodd"
        /></svg
      >
    </span>
    A simple info alert with an
    <a
      href="/"
      class="font-semibold underline hover:text-blue-800 dark:hover:text-blue-900"
      >example link</a
    >. Give it a click if you like.
  </Alert>
  {#if data}
    <p>Data:</p>
    <ul>
      {#each Object.entries(data) as [key, value]}
        <li>{key}: {value}</li>
      {/each}
    </ul>
  {/if}
</div>
