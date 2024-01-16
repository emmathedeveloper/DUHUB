<script>
    import { slide } from 'svelte/transition'
    import { ArrowRight } from 'lucide-svelte'

    
</script>

<section transition:slide|local class="flex flex-col gap-8 items-center justify-center h-full w-full p-4">
    
    <h1 class="text-2xl font-black">Login</h1>

    <h1 class="font-black text-3xl">DU<span class="text-blue-400 rounded">.HUB</span></h1>

    <form class="flex items-center flex-col gap-4 p-2">
        <input required type="text" placeholder="Username">
        <input required type="password" placeholder="Password">
        <input required type="password" placeholder="DU Password">
        <button class="bg-blue-400 rounded p-4 w-full outline-none text-white font-bold hover:opacity-80 transition-opacity flex items-center justify-center gap-4 group">Login <ArrowRight class="icon group-hover:translate-x-1/2 transition-transform"/></button>
    </form>

    <p>Don't have an account yet? <a class="text-blue-400" href="/signup">Sign Up</a></p>
</section>

<style>
    form{
        width: min(100% , 400px);
    }
    form > input {
        @apply p-4 rounded ring-blue-400 focus:outline-none focus:ring w-full border border-gray-200 transition-all focus:scale-105
    }
</style>