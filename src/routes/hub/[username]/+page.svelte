<script lang="ts">
  import Post from '$lib/components/post/post.svelte';
</script>

<section class="h-full w-full bg-gray-100 p-2 flex items-center justify-center select-none">
    <main class="flex flex-col h-full gap-4">
        <nav class="flex items-center justify-around w-full bg-white rounded shadow p-4">
            <h1 class="font-bold">Welcome Emmanuel</h1>

            <div class="flex items-center gap-2">
                <strong>30 🔥</strong>
                
            </div>
        </nav>

        <div class="flex-1 overflow-scroll">
            {#each { length: 25 } as b}
                <Post />
            {/each}
        </div>
    </main>
</section>

<style>
    main{
        width: min(100% , 700px);
    }
</style>