<script>
  import '../app.css';
  import { browser } from '$app/env'; 

  let dark = browser && localStorage.getItem('dark') || 'true';
  
  const toggleDarkMode = () => {
    localStorage.dark = (dark === 'true') ? 'false' : 'true'
    dark = localStorage.getItem('dark')
    
    if (dark === 'true')
      document.documentElement.classList.add('dark')
    else
      document.documentElement.classList.remove('dark')
  }
</script>

<div class="container sm:w-screen lg:w-2/3 xl:w-1/2 mx-auto mt-5 px-12">
  <main>
    <button class="block mx-auto mb-6 rounded w-32 p-2 text-gray-200 dark:text-gray-800 bg-gray-600 dark:bg-gray-400"
            on:click={toggleDarkMode}>
      {dark === 'true' ? 'Light Mode' : 'Dark Mode'}
    </button>
    
    <div>
      <slot></slot>
    </div>
  </main>
    
  <footer class="block mx-auto w-full text-center my-4">
    <p class="text-gray-800 dark:text-gray-200">
      Created with 
      <a class="hover:text-purple-600 dark:hover:text-purple-400 hover:underline text-blue-700 dark:text-blue-200"
        target="_blank"
        rel="noopener"
        href="https://svelte.dev">
          SvelteKit
      </a>
      and deployed with
      <a class="hover:text-purple-600 dark:hover:text-purple-400 hover:underline text-blue-700 dark:text-blue-200" 
        target="_blank"
        rel="noopener" 
        href="https://vercel.com">
          ▲ Vercel
      </a>
    </p>
  </footer>
</div>