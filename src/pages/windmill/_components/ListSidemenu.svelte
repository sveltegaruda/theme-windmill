<script>
  import { createEventDispatcher } from "svelte";
  import SVG from "./svg.svelte";
  import Menu from "./SideMenu.svelte";
  import SideSubMenu from "./SideSubMenu.svelte";

  const dispatch = createEventDispatcher();

  function togglePagesMenu() {
    menusub.isOpen = !menusub.isOpen;
  }

  function dismissSidemenu(event) {
    dispatch("dismissSidemenu", {
      isSidemenu: false,
    });
  }

  export let menusub;
</script>

<ul class="mt-6">
  <Menu to="/windmill/index" svg="windmill" label="Dashboard" />
  <Menu to="/windmill/forms" svg="forms" label="Forms" />
  <Menu to="/windmill/cards" svg="cards" label="Cards" />
  <Menu to="/windmill/charts" svg="charts" label="Charts" />
  <Menu to="/windmill/buttons" svg="buttons" label="Buttons" />
  <Menu to="/windmill/modals" svg="modals" label="Modals" />
  <Menu to="/windmill/tables" svg="tables" label="Tables" />

  <li class="relative px-6 py-3" on:click={(event) => event.stopPropagation()}>
    <button
      class="inline-flex items-center justify-between w-full text-sm font-semibold transition-colors duration-150 hover:text-gray-800 dark:hover:text-gray-200"
      on:click={togglePagesMenu}
      aria-haspopup="true">
      <span class="inline-flex items-center">
        <SVG svg="pages" />
        <span class="ml-4">Pages</span>
      </span>
      <SVG svg="evenodd" />
    </button>

    <ul
      x-transition:enter="transition-all ease-in-out duration-300"
      x-transition:enter-start="opacity-25 max-h-0"
      x-transition:enter-end="opacity-100 max-h-xl"
      x-transition:leave="transition-all ease-in-out duration-300"
      x-transition:leave-start="opacity-100 max-h-xl"
      x-transition:leave-end="opacity-0 max-h-0"
      class="p-2 mt-2 space-y-2 overflow-hidden text-sm font-medium text-gray-500 rounded-md shadow-inner bg-gray-50 dark:text-gray-400 dark:bg-gray-900 {menusub.isOpen === true ? menusub.classOpen : menusub.classClose}"
      style="display: {menusub.isOpen ? 'block' : 'none'};"
      aria-label="submenu">
      <SideSubMenu href="/windmill/pages/index" label="Login" />
      <SideSubMenu href="/windmill/pages/create-account" label="Create account" />
      <SideSubMenu href="/windmill/pages/forgot-password" label="Forgot password" />
      <SideSubMenu href="/windmill/404" label="404" />
      <SideSubMenu href="/windmill/blank" label="Blank" />
    </ul>
  </li>
</ul>
<div class="px-6 my-6">
  <button
    class="flex items-center justify-between w-full px-4 py-2 text-sm font-medium leading-5 text-white transition-colors duration-150 bg-purple-600 border border-transparent rounded-lg active:bg-purple-600 hover:bg-purple-700 focus:outline-none focus:shadow-outline-purple">
    Create account
    <span class="ml-2" aria-hidden="true">+</span>
  </button>
</div>
