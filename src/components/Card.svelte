<script>
  import { link } from "svelte-spa-router";
  import urlSlug from "url-slug";
  export let title, description, image, publishDate;
</script>

<div class="grid gap-4 p-4">
  <img src={image} alt="img" class="rounded-md max-w-xs" />

  <div>
    <h2 class="my-2 text-2xl font-medium dark:text-white">
      <a href={`/article/${urlSlug(title)}`} use:link>{title}</a>
    </h2>
    <p class="my-2 text-lg dark:text-white">
      {description.substring(0, 180)}...
    </p>
    <p class="text-lg dark:text-white">Published: {publishDate}</p>
  </div>
</div>
