<script>
  import urlSlug from "url-slug";
  import { pop } from "svelte-spa-router";
  import { Button } from "flowbite-svelte";
  import { format } from "timeago.js";
  import { blogs } from "../data.js";
  import NotFound from "../components/NotFound.svelte";
  export let params = {};
  let article;
  blogs.forEach((blog, index) => {
    if (params.title === urlSlug(blog.title)) {
      article = blog;
    }
  });
</script>

{#if article}
  <div>
    <h1 class="text-3xl dark:text-white">{article.title}</h1>
    <p class="text-lg dark:text-white">
      Published: {format(article.publishDate)}
    </p>
    <img src={article.image} alt="img" />
    <p class="text-lg dark:text-white">{article.content}</p>
    <Button class="my-4" on:click={pop}>Back</Button>
  </div>
{:else}
  <NotFound />
{/if}
