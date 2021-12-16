<script context="module">
  export async function load({ fetch }) {
    const res = await fetch('https://api.spacex.land/graphql', {
      method: 'POST',
      headers: {
        'Content-Type': 'application/json'
      },
      body: JSON.stringify({
        query: `{
            launchesPast(limit: 10) {
                mission_name
                launch_date_local
                links {
                    video_link
                }
            }
        }`
      })
    });

    if (res.ok) {
      const { data } = await res.json();
      return {
        props: {
          launches: data.launchesPast
        }
      };
    }

    return {
      status: res.status,
      error: new Error(`Error fetching GraphQL data`)
    };
  }
</script>

<script>
  import Link from '$lib/components/Shared/Link.svelte'

  export let launches
</script>

<h1 class="mb-4 text-center text-4xl text-gray-800 dark:text-gray-200">SpaceX Launches</h1>

<p class="mb-3 text-gray-800 dark:text-gray-200">
  This is an example
  <Link href="https://svelte.dev">SvelteKit</Link>
  application fetching GraphQL data from the public
  <Link href="https://api.spacex.land/graphql">SpaceX API</Link>.
  View source on
  <Link href="https://github.com/leerob/sveltekit-graphql">GitHub</Link>.
</p>

<ul class="list-none p-0 mt-4">
  {#each launches as launch}
    <li class="rounded-md mb-3 bg-gray-600 hover:bg-gray-700 dark:bg-gray-400 dark:hover:bg-gray-500">
      <a 
        class="block px-3 py-3"
        target="_blank"
        href={launch.links.video_link}>
          <h2 class="text-blue-200 dark:text-blue-900">{launch.mission_name}</h2>
          <p class="text-gray-100 dark:text-gray-900">{new Date(launch.launch_date_local).toLocaleString()}</p>
      </a>
    </li>
  {/each}
</ul>

<style>
  li {
    transition: 0.15s box-shadow ease-in-out;
  }
  li:hover {
    box-shadow: 0 5px 10px rgba(0, 0, 0, 0.12);
  }
</style>
