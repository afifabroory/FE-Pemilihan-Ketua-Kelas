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
        
        if (data['valid'] && nim !== undefined) {
            verified = true;
            error = false;
            
            token = data['token'];

            const response2 = await fetch(`http://localhost/api/candidate`);
            candidate = await response2.json();
            step++;

        } else if (!data['valid'] && nim !== undefined) {
            message = data['message'];
            error = true;
        } else if (nim === undefined) {
            message = 'NIM tidak boleh kosong';
            error = true;
        } else {
            message = 'Kesalahan tidak diketahui, mohon coba kembali';
            error = true;
        }
    }

    export let message: string = '';
    export let error: boolean = false;
    export let step: number;
</script>

{#if !verified}
    <Verify bind:nim={nim} on:verify={verify}/>
{:else}
    <Vote data={candidate} token={token} nim={nim} bind:error={error} bind:message={message} bind:step={step}/>
{/if}