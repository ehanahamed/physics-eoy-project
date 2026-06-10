<script>
    import { onMount } from "svelte";
    import FileInputBox from "$lib/FileInputBox.svelte";
    // import EditIcon from "$lib/icons/Pencil.svelte";
    // import GridIcon from "$lib/icons/AppsGrid.svelte";
    import CheckmarkIcon from "$lib/icons/Checkmark.svelte";

    let uploadButtonEnabled = $state(false);
    let step = $state(0);
    let fileInput;
    let canvas;

    let objectURLs = [];
    onMount(() => {
        return () => {
            objectURLs.forEach(objectURL => URL.revokeObjectURL(objectURL));
        }
    })
    let selectedColor = $state();
</script>
<div class="grid page">
    <div class="content" style="margin-top: 1rem;">
        {#if step == 0}
        <p style="font-size: 1.2rem;">Select an image of a track <span class="fg0">(from an overhead view)</span></p>
        <!-- accept="image/*,video/*" -->
        <FileInputBox accept="image/*" onChangeCallback={(files) => uploadButtonEnabled = files.length > 0} bind:this={fileInput}></FileInputBox>
        <div class="flex">
            <button disabled={!uploadButtonEnabled} style={uploadButtonEnabled ? "" : "opacity: 0.6;"} onclick={() => {
                fileInput.showLoading();
                const ctx = canvas.getContext("2d");
                const img = new Image();
                img.onload = () => {
                    canvas.width = img.width;
                    canvas.height = img.height;
                    ctx.drawImage(img, 0, 0);
                }
                const objectURL = URL.createObjectURL(fileInput.getFiles()[0]);
                objectURLs.push(objectURL);
                img.src = objectURL;
                fileInput.hideLoading();
                step = 1;
            }}>
                <CheckmarkIcon></CheckmarkIcon> Next
            </button>
        </div>
        {/if}
        {#if step == 1}
            <p style="font-size: 1.2rem;">Select a point anywhere on the track</p>
        {/if}
        <canvas bind:this={canvas} class="canvas {step > 0 ? "" : "hide"}" style={step == 1 ? "cursor: crosshair;" : ""} onclick={(e) => {
            if (step == 1) {
                const rect = canvas.getBoundingClientRect();
                const scaleX = canvas.width / rect.width;
                const scaleY = canvas.height / rect.height;
                const ctx = canvas.getContext("2d");
                const x = Math.floor((e.clientX - rect.left) * scaleX);
                const y = Math.floor((e.clientY - rect.top) * scaleY);
                const pixel = ctx.getImageData(x, y, 1, 1).data;
                selectedColor = { r: pixel[0], g: pixel[1], b: pixel[2] };
            }
        }}></canvas>
        {#if step == 1}
            <p>Selected color:</p>
            {#if selectedColor == null}
                <p class="fg0" style="font-size: 1.2rem; margin-top: 0.4rem;">(None)</p>
            {:else}
            <div style="width: 5rem; height: 3rem; margin-top: 0.4rem; border-radius: 0.8rem; border: 0.2rem solid var(--border); background-color: rgb({selectedColor.r ?? 0} {selectedColor.g ?? 0} {selectedColor.b ?? 0});"></div>
            {/if}
            <div class="flex">
                <button disabled={selectedColor?.r == null} style={selectedColor?.r == null ? "opacity: 0.6;" : ""}>
                    <CheckmarkIcon></CheckmarkIcon> Confirm
                </button>
            </div>
        {/if}
{#if false}
        <p class="h4" style="margin-top: 2rem;">0 <span class="fg0">total turns on this track</span></p>
        <div class="flex">
            <div>
                <p style="font-size: 0.9rem; margin-bottom: 0px;" class="fg0">Input max forward acceleration</p>
                <div class="flex" style="margin-top: 0.4rem; align-items: center;">
                    <input type="text" style="max-width: 4rem;">
                    <span>m/s/s</span>
                </div>
            </div>
            <div>
                <p style="font-size: 0.9rem; margin-bottom: 0px;" class="fg0">Input max braking deacceleration</p>
                <div class="flex" style="margin-top: 0.4rem; align-items: center;">
                    <input type="text" style="max-width: 4rem;">
                    <span>m/s/s</span>
                </div>
            </div>
            <div>
                <p style="font-size: 0.9rem; margin-bottom: 0px;" class="fg0">Input max velocity</p>
                <div class="flex" style="margin-top: 0.4rem; align-items: center;">
                    <input type="text" style="max-width: 4rem;">
                    <span>m/s</span>
                </div>
            </div>
        </div>
        <div class="flex">
            <button class="alt yayy"><CheckmarkIcon></CheckmarkIcon> Calculate</button>
        </div>
        <div class="box center text fg0">
            Enter vehicle settings and press calculate to show results here
        </div>
        <!-- <div class="box">
        <p><span class="ohno">41.2 m/s/s</span> deacceleration before turn #1</p>
        <p><span class="ohno">-5.2 m/s</span> net change in velocity for turn #1</p>
        </div>
        <div class="box">
        <p><span class="ohno">36.3 m/s/s</span> deacceleration before turn #2</p>
        <p><span class="ohno">-2.8 m/s</span> net change in velocity for turn #2</p>
        </div>
        <div class="box">
        <p><span class="ohno">48.9 m/s/s</span> deacceleration before turn #3</p>
        <p><span class="ohno">-9.1 m/s</span> net change in velocity for turn #3</p>
        </div> -->
        {/if}
    </div>
</div>
<style>
    .canvas {
        width: min(100%, 40rem);
        height: auto;
        border-radius: 0.8rem;
        border: 0.2rem solid var(--border);
    }
</style>
