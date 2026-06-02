<script>
    import FileInputBox from "$lib/FileInputBox.svelte";
    import GHIcon from "$lib/icons/GitHub.svelte";
    import EditIcon from "$lib/icons/Pencil.svelte";
    import GridIcon from "$lib/icons/AppsGrid.svelte";
</script>
<div class="grid page" style="min-height: 75vh;">
    <div class="content" style="margin-top: 3rem;">

        <p class="fg0">Upload image of track to calculate</p>
        <FileInputBox></FileInputBox>
        <div class="flex" style="margin-top: 1rem;">
            <button class="button-box"><EditIcon></EditIcon></button>
            <button class="button-box"><GridIcon></GridIcon></button>
        </div>
        <p class="h4" style="margin-top: 2rem;">0 <span class="fg0">total turns on this track</span></p>
        <p><span class="warn">0.00 m/s/s</span> deacceleration before turn #1</p>
        <p><span class="fg0">+0.00 m/s</span> change in velocity (turn #1)</p>
    </div>
</div>
<div class="footer" style="padding-top: 1rem;">
    <p class="fg0">AP Physics EOY Project 2026 · Ehan A</p>
    <button class="faint"><GHIcon></GHIcon> See Source Code</button>
</div>
