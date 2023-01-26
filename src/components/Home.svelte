<script>
  import { format } from "timeago.js";
  import Card from "./Card.svelte";
  import { blogs } from "../data.js";
</script>

<h1>All your traveling tips in one place</h1>
{#each blogs as blog, i}
  <Card
    title={blog.title}
    description={blog.content}
    image={blog.image}
    publishDate={format(blog.publishDate)}
  />
{/each}
