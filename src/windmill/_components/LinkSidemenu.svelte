<script>
  /* import { Link } from "svelte-routing"; */

  //  export let to = "";
  export let attrclass =
    "inline-flex items-center w-full text-sm font-semibold transition-colors duration-150 hover:text-gray-800 dark:hover:text-gray-200";

  function getProps({ location, href, isPartiallyCurrent, isCurrent }) {
    const isActive = href === "/" ? isCurrent : isPartiallyCurrent || isCurrent;

    // The object returned here is spread on the anchor element's attributes
    if (isActive) {
      return {
        class:
          "svelte-link inline-flex items-center w-full text-sm font-semibold transition-colors duration-150 hover:text-gray-800 dark:hover:text-gray-200 text-gray-800 dark:text-gray-100",
      };
    }
    return { class: attrclass };
  }
</script>

<!-- <Link to="{to}" getProps="{getProps}"> -->
<slot />
<!-- </Link> -->
