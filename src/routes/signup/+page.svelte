<script lang="ts">
  import { ArrowRight } from "lucide-svelte";
  import { slide } from "svelte/transition";
  import { pb } from '../../store'
  import { goto } from "$app/navigation";

  async function handleSubmit(event: any){

        const e = event as SubmitEvent & { target: EventTarget & HTMLFormElement }

        const data = new FormData(e.target)

        try {
            
            await pb.collection('users').create({
                username: data.get('username'),
                password: data.get('password'),
                passwordConfirm: data.get('password'),
                email: data.get('email')
            })

            if(data.get('email')) await pb.collection('users').requestVerification(data.get('email') as string)

            goto(`/hub/${data.get('username')}`)

        } catch (error) {
            
        }

  }
</script>

<section transition:slide|local class="relative flex flex-col gap-8 items-center justify-center h-full w-full p-4">
    
    <h1 class="text-2xl font-black">Sign Up</h1>

    <h1 class="font-black text-3xl">DU<span class="text-blue-400 rounded">.HUB</span></h1>

    <form on:submit|preventDefault={handleSubmit} class="flex items-center flex-col gap-4 p-2">
        <input required type="text" name="username" placeholder="Username">
        <input required type="email" name="email" placeholder="Email">
        <input required type="password" name="password" placeholder="Password">
        <input required type="password" name="dupassword" placeholder="DU Password">
        <button class="bg-blue-400 rounded p-4 w-full outline-none text-white font-bold hover:opacity-80 transition-opacity flex items-center justify-center gap-4 group">Sign Up <ArrowRight class="icon group-hover:translate-x-1/2 transition-transform"/></button>
    </form>

    <p>Already have an account yet? <a class="text-blue-400" href="/login">Login</a></p>
</section>

<style>
    form{
        width: min(100% , 400px);
    }
    form > input {
        @apply p-4 rounded ring-blue-400 focus:outline-none focus:ring w-full border border-gray-200 transition-all focus:scale-105
    }
</style>