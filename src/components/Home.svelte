<script>
  import { Alert } from "flowbite-svelte";
  import { format } from "timeago.js";
  import Card from "./Card.svelte";
  import { blogs } from "../data.js";
</script>

<h1 class="text-3xl dark:text-white">Lorem ipsum dolor sit amet</h1>
{#each blogs as blog, i}
  <Card
    title={blog.title}
    description={blog.content}
    image={blog.image}
    publishDate={format(blog.publishDate)}
  />
{/each}

