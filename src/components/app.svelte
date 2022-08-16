<script lang="ts">
    import Card from "./card.svelte";
    import Input from "./input.svelte";
    import Alert from "./alert.svelte";
    import Thanks from "./thanks.svelte";

    let message: string;
    let isError: boolean;
    let step: number = 1;
</script>

<Alert message={message} isError={isError}></Alert>
<div class="flex h-screen justify-center items-center bg-slate-100">
    <Card step={step} title={"Pemilihan Ketua Kelas D MI"} subtitle={"Tahun 2022/2023"}>        
        {#if step == 3}
            <Thanks></Thanks>
        {:else}
            <Input bind:step={step} bind:message={message} bind:error={isError}></Input>
        {/if}
    </Card>
</div>