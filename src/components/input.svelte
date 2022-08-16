<script lang="ts">
    import Verify from "./verify.svelte";
    import Vote from "./vote.svelte";

    let verified: boolean = false;
    let token: string;

    let nim: string;
    let candidate: any[] = [];
    async function verify() {
        const response = await fetch(`http://localhost/api/voter/verify?nim=${nim}`);
        let data = await response.json();
        
        if (data['valid']) {
            verified = true;
            error = false;
            
            token = data['token'];

            const response2 = await fetch(`http://localhost/api/candidate`);
            candidate = await response2.json();
        } else {
            message = data['message'];
            error = true;
        }
    }

    export let message = '';
    export let error = false;
</script>

{#if !verified}
    <Verify bind:nim={nim} on:verify={verify}/>
{:else}
    <Vote data={candidate} token={token} nim={nim} bind:error={error} bind:message={message}/>
{/if}