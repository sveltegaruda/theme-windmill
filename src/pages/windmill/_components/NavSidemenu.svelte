<script>
  import { createEventDispatcher } from "svelte";
  const dispatch = createEventDispatcher();

  import NavLink from "./NavLink.svelte";
  import ListSidemenu from "./ListSidemenu.svelte";

  let menusub = {
    classOpen: "transition-all ease-in-out duration-300 opacity-100 max-h-xl",
    classClose: "transition-all ease-in-out duration-300 opacity-0 max-h-0",
    isOpen: false,
  };

  function toggleSideMenu() {
    sidemenu.isSidemenuMobile = !sidemenu.isSidemenuMobile;
    if (sidemenu.isSidemenuMobile) {
      document.querySelectorAll(".theme-backdrop")[0].style.display = "block";
    }
  }
  function closeSideMenu() {
    sidemenu.isSidemenuMobile = false;
  }
  function togglePagesMenu() {
    menusub.isOpen = !menusub.isOpen;
  }

  function handleDismiss(flag) {
    if (flag === true) {
      closeSideMenu();
    }
    if (flag === "menu") {
      dispatch("dismissSidemenu", {
        isSidemenu: false,
      });
    }
  }

  export let sidemenu;
</script>

<svelte:window
  on:keydown={(e) => e.key === 'Escape' && handleDismiss(true)}
  on:click={() => handleDismiss(true)} />

{#if !sidemenu.isSidemenuMobile}
  <aside
    class="z-20 hidden w-64 overflow-y-auto bg-white dark:bg-gray-800 md:block flex-shrink-0">
    <div class="py-4 text-gray-500 dark:text-gray-400">
      <div id="title-desktop">
        <NavLink
          attrclass="ml-6 text-lg font-bold text-gray-800 dark:text-gray-200"
          to="/windmill">
          Windmill.svlt
        </NavLink>
      </div>

      <ListSidemenu
        {menusub}
        on:dismissSidemenu={() => handleDismiss('menu')} />
    </div>
  </aside>
{:else}
  <aside
    x-show={sidemenu.isSidemenuMobile}
    x-transition:enter="transition ease-in-out duration-150"
    x-transition:enter-start="opacity-0 transform -translate-x-20"
    x-transition:enter-end="opacity-100"
    x-transition:leave="transition ease-in-out duration-150"
    x-transition:leave-start="opacity-100"
    x-transition:leave-end="opacity-0 transform -translate-x-20"
    class="fixed inset-y-0 z-20 flex-shrink-0 w-64 mt-16 overflow-y-auto bg-white dark:bg-gray-800 md:hidden {sidemenu.isSidemenuMobile === true ? sidemenu.classOpen : sidemenu.classClose}"
    style="display: {sidemenu.isSidemenuMobile ? 'block' : 'none'};"
    on:click={(event) => event.stopPropagation()}>
    <div class="py-4 text-gray-500 dark:text-gray-400">
      <div id="title-mobile">
        <NavLink
          attrclass="ml-6 text-lg font-bold text-gray-800 dark:text-gray-200"
          to="/windmill">
          Windmill.svlt
        </NavLink>
      </div>

      <ListSidemenu
        {menusub}
        on:dismissSidemenu={() => handleDismiss('menu')} />
    </div>
  </aside>
{/if}
<div
  x-show={sidemenu.isSidemenuMobile}
  x-transition:enter="transition ease-in-out duration-150"
  x-transition:enter-start="opacity-0"
  x-transition:enter-end="opacity-100"
  x-transition:leave="transition ease-in-out duration-150"
  x-transition:leave-start="opacity-100"
  x-transition:leave-end="opacity-0"
  class="fixed inset-0 z-10 flex items-end bg-black bg-opacity-50 sm:items-center sm:justify-center {sidemenu.isSidemenuMobile === true ? sidemenu.classBackdropShow : sidemenu.classBackdropHide}"
  style="display: {sidemenu.isSidemenuMobile ? 'block' : 'none'};" />
