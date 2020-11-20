<script>
    import { url, isActive } from "@roxi/routify";
    import SVG from "./svg.svelte";

    export let to;
    export let svg;
    export let label;
</script>

<li class="relative px-6 py-3">
    {#if $isActive(to)}
        <span
            class="absolute inset-y-0 left-0 w-1 bg-purple-600 rounded-tr-lg rounded-br-lg"
            aria-hidden="true" />
    {/if}
    <a
        class={'inline-flex items-center w-full text-sm transition-colors duration-150 hover:text-gray-800 dark:hover:text-gray-200' + ($isActive(to) ? ' font-bold text-gray-800 dark:text-gray-100' : ' font-semibold text-gray-600')}
        href={$url(to)}>
        <SVG {svg} />
        <span class="ml-4">{label}</span>
    </a>
</li>
