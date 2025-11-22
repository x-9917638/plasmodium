<script lang="ts">
    import error from '$lib/assets/error.svg'
    let {
        title = "Oh no! An error occured loading the fact title.",
        body = "Oh no! An error occured loading the fact body.",
        icon = error
    } = $props();
</script>

<div class="bg-white dark:bg-gray-800 rounded-lg px-6 py-8 ring shadow-xl ring-gray-900/5">
    <span class="inline-flex items-center justify-center rounded-md bg-indigo-500 p-2 shadow-lg">
        <img src={icon} alt={title} height="24px" width="24px">
    </span>
    <h3 class="text-gray-900 dark:text-white mt-5 text-base font-medium tracking-tight">{title}</h3>
    <p class="text-gray-500 dark:text-gray-400 mt-2 text-sm ">{body}</p>
</div>