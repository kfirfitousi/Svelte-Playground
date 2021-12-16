<svelte:head>
  <script>
    if (localStorage.dark === 'true' || (!('dark' in localStorage) && window.matchMedia('(prefers-color-scheme: dark)').matches)) {
      document.documentElement.classList.add('dark')
      localStorage.dark = 'true'
    } else {
      document.documentElement.classList.remove('dark')
      localStorage.dark = 'false'
    }
  </script>
</svelte:head>

<script>
  import '../app.css';
  import Header from '$lib/components/Header/Header.svelte'
  import Link from '$lib/components/Shared/Link.svelte'
  import { navigating } from '$app/stores'
</script>

<Header></Header>


<main class="container sm:w-screen lg:w-2/3 xl:w-1/2 mx-auto mt-8 px-12">
  {#if $navigating}
    <p class="text-center text-gray-800 dark:text-gray-200">Loading...</p>
  {:else}
    <slot></slot>
  {/if}
</main>

<footer class="block mx-auto w-full text-center my-4">
  <p class="text-gray-800 dark:text-gray-200">
    Created with 
    <Link href="https://svelte.dev">SvelteKit</Link>
    and deployed with
    <Link href="https://vercel.com">▲ Vercel</Link>
  </p>
</footer>