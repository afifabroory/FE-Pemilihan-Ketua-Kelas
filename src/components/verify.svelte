<script lang="ts">
    import { createEventDispatcher } from 'svelte';

    const dispatch = createEventDispatcher();

    function verify() {
        dispatch('verify');
    }

    export let nim: string;
</script>

<div id="verification-form">
    <div class="font-semibold after:content-['*'] after:text-red-600">Masukkan NIM Anda</div>
    <input class="w-full border border-black rounded px-2 py-1" type="text" bind:value={nim}>
    <div class="flex justify-end">
        <button class="border border-black rounded px-4 py-1 mt-6" on:click={verify}>Next</button>
    </div>
</div>