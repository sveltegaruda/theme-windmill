<script>
  /* import { Link } from "svelte-routing"; */
  import { isActive } from "@roxi/routify";

  export let to = "";
  export let attrclass =
    "inline-flex items-center w-full text-sm font-semibold transition-colors duration-150 hover:text-gray-800 dark:hover:text-gray-200";

  function setActiveStatus(to) {
    // The object returned here is spread on the anchor element's attributes
    if ($isActive(to)) {
      /* return {
        class:
          "svelte-link inline-flex items-center w-full text-sm font-semibold transition-colors duration-150 hover:text-gray-800 dark:hover:text-gray-200 text-gray-800 dark:text-gray-100",
      }; */
      attrclass =
        "svelte-link inline-flex items-center w-full text-sm font-semibold transition-colors duration-150 hover:text-gray-800 dark:hover:text-gray-200 text-gray-800 dark:text-gray-100";
    }
    attrclass =
        "svelte-link inline-flex items-center w-full text-sm font-semibold transition-colors duration-150 hover:text-gray-800 dark:hover:text-gray-200 text-gray-800 dark:text-gray-100";
    /* return { class: attrclass }; */
    return '"' + attrclass + '"';
  }
  let linkClass = setActiveStatus(to);
</script>

<!-- <Link to="{to}" getProps="{getProps}"> -->
<a href={to} class={linkClass}>
  <slot />
</a>
<!-- </Link> -->
