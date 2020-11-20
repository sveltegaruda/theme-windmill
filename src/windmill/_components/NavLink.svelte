<script>
/*   import { Link } from "svelte-routing"; */
  
  import { createEventDispatcher } from 'svelte';
  const dispatch = createEventDispatcher();

//  export let to = "";
  export let attrclass = "";
  export let isClose = false;

  function getProps({ location, href, isPartiallyCurrent, isCurrent }) {
    const isActive = href === "/" ? isCurrent : isPartiallyCurrent || isCurrent;

    if (isActive) {
      if (isClose) {
      	dispatch('dispatchclose', {
      		isClose: !isClose
      	});
      }
    }

    return { class: attrclass };
  }
</script>

<!-- <Link to="{to}" getProps="{getProps}"> -->
  <slot />
<!-- </Link> -->
