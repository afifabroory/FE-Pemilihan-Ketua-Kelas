<script lang="ts">
    import { createEventDispatcher } from 'svelte';
    let disable: boolean = true;

    function change() {
        if (nim !== '') 
            disable = false;
        else
            disable = true;
    }

    const dispatch = createEventDispatcher();

    function verify() {
        dispatch('verify');
    }

    export let nim: string;
</script>

<div>
    <div class="font-semibold after:content-['*'] after:text-red-500 text-gray-600">NIM</div>
    <input class="w-full rounded p-2 border border-gray-300 shadow focus:outline-none focus:shadow-outline text-gray-700" placeholder="Masukkan NIM Anda" type="text" bind:value={nim} on:input={change}>
    <div class="flex justify-end">
        <button class="grow rounded px-5 py-2 mt-6 bg-blue-500 text-white font-bold disabled:bg-blue-300" on:click={verify} disabled={disable}>Next</button>
    </div>
</div>