<script>
  import { Router } from "@roxi/routify";
  import { routes } from "../.routify/routes";
  import './tailwind.css';
</script>

<style  global>
  @import "../static/global.css";
</style>

<Router {routes} />