<script lang="ts">
    export let step: number;
    export let title: string;
    export let subtitle: string;
</script>

<div class="mx-auto my-auto w-fit py-12 px-8 rounded-lg border shadow-md bg-white">
    {#if step != 3}
        <div class="text-center text-xl font-bold">{title}<br>{subtitle}</div>
    {/if}
    <div class="mt-6 w-fit mx-auto">
        <slot/>
    </div>
    <div class="flex items-center justify-center mt-6">
        {#if step == 1}
            <div class="bg-blue-500 w-2 h-2 rounded-full mr-2"></div>
            <div class="bg-blue-200 w-2 h-2 rounded-full mr-2"></div>
            <div class="bg-blue-200 w-2 h-2 rounded-full"></div>
        {:else if step == 2}
            <div class="bg-blue-200 w-2 h-2 rounded-full mr-2"></div>
            <div class="bg-blue-500 w-2 h-2 rounded-full mr-2"></div>
            <div class="bg-blue-200 w-2 h-2 rounded-full"></div>
        {:else if step == 3}
            <div class="bg-blue-200 w-2 h-2 rounded-full mr-2"></div>
            <div class="bg-blue-200 w-2 h-2 rounded-full mr-2"></div>
            <div class="bg-blue-500 w-2 h-2 rounded-full"></div>
        {/if}
    </div>
    {#if step <= 3}
        <div class="flex justify-center mt-8">
            <a class="text-gray-400 underline" href="hasil.html">Hasil voting</a>
        </div>
    {/if}
</div>