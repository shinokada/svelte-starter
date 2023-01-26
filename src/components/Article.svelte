<script>
  import urlSlug from "url-slug";
  import { pop } from "svelte-spa-router";
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
    <h1>{article.title}</h1>
    <p>Published: {format(article.publishDate)}</p>
    <img src={article.image} alt="img" />
    <p>{article.content}</p>
    <button on:click={pop} on:keydown|preventDefault={pop}>Back</button>
  </div>
{:else}
  <NotFound />
{/if}
