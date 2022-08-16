<script lang="ts">
    export let message: string;
    export let isError: boolean;

    import { slide } from 'svelte/transition';
</script>


{#if isError}
    <div class="bg-red-100 border border-red-400 text-red-700 px-4 py-3 rounded flex align-middle justify-between mb-6 w-64 left-0 right-0 mx-auto absolute" role="alert" in:slide out:slide>
        <div>
            <strong class="font-bold">Error!</strong><br>
            <span class="block sm:inline">{message}</span>
        </div>
    </div>
{/if}