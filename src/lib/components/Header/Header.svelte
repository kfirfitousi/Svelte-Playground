<script>
    import DarkModeSwitch from './DarkModeSwitch.svelte'
    import { page } from '$app/stores'

    const links = [
        { title: 'Home', path: '/' },
        { title: 'About', path: '/about' }
    ]
</script>

<header class="sticky top-0 flex justify-between">
    <nav class="flex w-full my-0 mx-auto justify-center bg-gray-600 dark:bg-gray-400">
        <ul class="relative sm:w-full md:w-full lg:w-2/3 xl:w-1/2 py-0 px-12 m-0 h-12 flex justify-start items-center list-none bg-contain">
            {#each links as link}
                <li class="relative h-full" class:active={$page.path === link.path}>
                    <a class="flex h-full item-center px-4 py-4 text-gray-200 dark:text-gray-800 hover:bg-gray-400 dark:hover:bg-gray-600 font-bold text-xs tracking-widest no-underline"
                        sveltekit:prefetch href={link.path}>{link.title}</a>
                </li>
            {/each}
            <li class="ml-auto">
                <DarkModeSwitch></DarkModeSwitch>
            </li>
        </ul>
    </nav>
</header>