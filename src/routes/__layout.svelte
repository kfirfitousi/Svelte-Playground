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
</script>

<Header></Header>

<div class="container sm:w-screen lg:w-2/3 xl:w-1/2 mx-auto mt-8 px-12">
  <main>
    <slot></slot>
  </main>
</div>
  
<footer class="block mx-auto w-full text-center my-4">
  <p class="text-gray-800 dark:text-gray-200">
    Created with 
    <a class="hover:text-purple-600 dark:hover:text-purple-400 hover:underline text-blue-700 dark:text-blue-200"
      target="_blank"
      href="https://svelte.dev">
        SvelteKit
    </a>
    and deployed with
    <a class="hover:text-purple-600 dark:hover:text-purple-400 hover:underline text-blue-700 dark:text-blue-200" 
      target="_blank"
      href="https://vercel.com">
        ▲ Vercel
    </a>
  </p>
</footer>