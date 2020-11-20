<script>
  // export let location
  import { onMount } from 'svelte'
  
  onMount(() => {
    let els = document.querySelectorAll("li.nav-sidemenu a");
    els = document.querySelectorAll("li.nav-sidemenu span.nav-sidemenu-active");
    for (let i = 0; i < els.length; i++) {
      els[i].className = "nav-sidemenu-active";
    }
  });
</script>

        <main class="h-full pb-16 overflow-y-auto">
          <!-- Remove everything INSIDE this div to a really blank page -->
          <div class="container px-6 mx-auto grid">
            <h2
              class="my-6 text-2xl font-semibold text-gray-700 dark:text-gray-200"
            >
              Blank
            </h2>
          </div>
        </main>