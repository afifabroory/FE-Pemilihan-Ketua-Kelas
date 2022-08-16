<script lang="ts">
    let candidate : string;

    async function vote() {            
        let response = await fetch("http://localhost/api/vote", {
            method: "POST",
            headers: {
                'Content-type': 'application/json',
                'Origin': 'http://localhost:5173'
            },
            body: JSON.stringify({
                "nim": nim,
                "candidate": candidate,
                "token": token
            })
        })        

        if (response.status === 201)
            console.log("OK NEXT");
        else {
            let data = await response.json();
            message = data['message'];
            error = true;
        }
    }

    export let data: any[];
    export let token: string;
    export let nim: string;
    export let error: boolean;
    export let message: string;
</script>

<div>
    <label>
        <div class="font-semibold">Kandidat:</div>
        <select class="w-full border border-black rounded px-2 py-1" bind:value={candidate}>
            <option disabled selected>Pilih kandidat</option>
            {#each data as candidate}
                <option value={candidate.NIM}>{candidate.nama}</option>
            {/each}
        </select>
        <div class="flex justify-end">
            <button class="border border-black rounded px-4 py-1 mt-6" on:click={vote}>Kirim</button>
        </div>
    </label>
</div>