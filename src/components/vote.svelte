<script lang="ts">
    let candidate : string;
    let disable : boolean = true;

    function changed() {
        disable = false;
    }

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
            step++;
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
    export let step: number;
</script>

<div>
    <label>
        <div class="font-semibold after:content-['*'] after:text-red-500 text-gray-600">Kandidat</div>
        <select class="w-full rounded p-2 border border-gray-300 shadow focus:outline-none focus:shadow-outline text-gray-700" bind:value={candidate} on:change={changed}>
            <option disabled selected>Pilih kandidat</option>
            {#each data as candidate}
                <option value={candidate.NIM}>{candidate.nama}</option>
            {/each}
        </select>
        <div class="flex justify-end">
            <button class="grow rounded px-5 py-2 mt-6 bg-blue-500 disabled:bg-blue-300 text-white font-bold" on:click={vote} disabled={disable}>Kirim</button>
        </div>
    </label>
</div>