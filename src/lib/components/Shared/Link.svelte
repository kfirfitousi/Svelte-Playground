<script>
    export let href
    export let newWindow = true
</script>

<a 
    class="hover:text-purple-600 dark:hover:text-purple-400 hover:underline text-blue-700 dark:text-blue-200"
    target={newWindow ? "_blank" : '_self'}
    {href}>
        <slot></slot>
</a>