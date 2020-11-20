<script>
  import { url, isActive } from "@roxi/routify";

  export let href;
  export let label;
</script>

<li
  class="px-2 py-1 transition-colors duration-150 hover:text-gray-800 dark:hover:text-gray-200">
  {#if $isActive(href)}
    <a
      class="svelte-link inline-flex items-center w-full text-sm font-semibold transition-colors duration-150 hover:text-gray-800 dark:hover:text-gray-200 text-gray-800 dark:text-gray-100"
      href={$url(href)}>{label}</a>
  {:else}<a class="w-full hover:text-gray-800 text-gray-600" href={$url(href)}>{label}</a>{/if}
</li>
