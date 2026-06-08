<script>
    import FileInputBox from "$lib/FileInputBox.svelte";
    import GHIcon from "$lib/icons/GitHub.svelte";
    import EditIcon from "$lib/icons/Pencil.svelte";
    import GridIcon from "$lib/icons/AppsGrid.svelte";
    import CheckmarkIcon from "$lib/icons/Checkmark.svelte";
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
    </div>
</div>
<div class="footer" style="padding-top: 1rem;">
    <p class="fg0">AP Physics EOY Project 2026 · Ehan A</p>
    <button class="faint"><GHIcon></GHIcon> See Source Code</button>
</div>
