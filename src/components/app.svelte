<script lang="ts">
    import Card from "./card.svelte";
    import Input from "./input.svelte";
    import Alert from "./alert.svelte";

    let message: string;
    let isError: boolean;
</script>

<Alert message={message} isError={isError}></Alert>
<div class="flex h-screen justify-center items-center">
    <Card>        
        <Input slot="input" bind:message={message} bind:error={isError}></Input>
    </Card>
</div>