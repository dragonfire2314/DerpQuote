<script lang="ts">
    type LineItem = {
        sd: string, 
        line_number: number, 
        item: string,
        qty: number, 
        model_no: string, 
        desc: string, 
        list: number
    };

    let items: LineItem[] = [];
    let floatingTextArea = false;

    items.push({
        sd: "70%",
        line_number: 1,
        item: "CH-1",
        qty: 4,
        model_no: "VRHER",
        desc: "THIS IS A DISCRITPTION",
        list: 250, 
    })

    items.push({
        sd: "70%",
        line_number: 1,
        item: "CH-1",
        qty: 4,
        model_no: "VRHER",
        desc: "THIS IS A DISCRITPTION",
        list: 250, 
    })

    items.push({
        sd: "70%",
        line_number: 2,
        item: "CH-2",
        qty: 3,
        model_no: "VRHER",
        desc: "THIS IS A DISCRITPTION",
        list: 250, 
    })

    function dupe(line_number: number) {
        console.log("dup");
        var tempItem: LineItem | undefined = items.find((item) => item.line_number == line_number);
        if (tempItem === undefined)
        {
            console.error("Error duplicating entry");
            return;
        }
        items.push(tempItem)

        items = items;
    }

    function del(line_number: number) {
        console.log("del");
        items = items.filter((item) => item.line_number !== line_number);
    }

    function sortItems() {
        items = items.sort((a, b) => {
            return (a.line_number - b.line_number);
        });
    }

    function textAreaFocusHandler(event: Event) {
        console.log(event.target);
    }

    function textAreaFocusOutHandler(event: Event) {
        console.log(event.target);
    }
</script>

<div class="container">
    <p class="span2row">S/D</p>
    <p class="span2row">Line#</p>
    <p class="span2row">Line</p>
    <p class="span2row">Qty</p>
    <p class="span2row">Model No.</p>
    <p class="span2row">Description</p>
    <p class="span2row">List Each</p>
    <p style="grid-column: 8 / 10;">Dealer</p>
    <p style="grid-row: 2 / 3;">Net Each</p>
    <p style="grid-row: 2 / 3;">Extended Net</p>
    <p style="grid-column: 10 / 12;">GPO Member</p>
    <p style="grid-row: 2 / 3;">Net Each</p>
    <p style="grid-row: 2 / 3;">Extended Net</p>
    <p class="span2row">Dupe</p>
    <p class="span2row">Delete</p>
    {#each items as item}
        <textarea id="sd" bind:value={item.sd} on:focus={textAreaFocusHandler} on:focusout={textAreaFocusOutHandler}></textarea>
        <textarea id="line_number" bind:value={item.line_number} on:change={sortItems}></textarea>
        <textarea id="item" bind:value={item.item}></textarea>
        <textarea id="qty" bind:value={item.qty}></textarea>
        <textarea id="model_no" bind:value={item.model_no}></textarea>
        <textarea id="desc" bind:value={item.desc}></textarea>
        <textarea id="list" bind:value={item.list}></textarea>
        <p class="white_back">Net Each</p>
        <p class="white_back">net</p>
        <p class="white_back">Net Each</p>
        <p class="white_back">ext Net</p>
        <div class="dupe_del"><button title="dup" style="border-radius: 50px;" on:click={() => {dupe(item.line_number)}}></button></div>
        <div class="dupe_del"><button title="del" on:click={() => {del(item.line_number)}}></button></div>
    {/each}
    {#if floatingTextArea}
        <textarea class="floating_textarea"></textarea>
    {/if}
</div>

<style>

.span2row {
    grid-row: 1 / 3;
}

.item {

}

.container {
    display: grid;
    grid-template-columns: 0.5fr 0.5fr 1fr 1fr 2fr 4fr 1fr 1fr 1fr 1fr 1fr 0.5fr 0.5fr;
    grid-auto-rows: auto;
    grid-auto-flow: row;

    border-left: 1px solid black;
    border-top: 1px solid black;
}

.white_back {
    background-color: white;
    height: 60px;

}

p {
    align-self: stretch;
    align-content: end;

    border-right: 1px solid black;
    border-bottom: 1px solid black;

}

.dupe_del {
    background-color: white;
    display: flex;
    justify-content: center;
    border-right: 1px solid black;
    border-bottom: 1px solid black;
}

button {
    background-color: var(--color-purple-300);
    width: 75%;
    height: 75%;
    align-self: center;
}

button:hover {
    background-color: var(--color-purple-400);

}

.floating_textarea {
    background-color: aqua;
    position: absolute;
    height: 200px;
}

textarea {
    padding: 5px;
    resize: none;
    border-top: 0px;
    border-left: 0px;
    height: 60px;
    transition: all 0.15s ease;
}

textarea:focus {
    /* background-color: aqua; */
    position: relative;
    height: 200px;
}

</style>