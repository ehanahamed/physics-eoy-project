<script lang="ts">
    import GHIcon from "$lib/icons/GitHub.svelte";
    import SunIcon from "$lib/icons/Sun.svelte";
    import MoonIcon from "$lib/icons/Moon.svelte";

	let { children } = $props();
</script>
<svelte:head>
    <title>Physics EOY Project</title>
</svelte:head>
<header class="navbar with-search with-status" style="border-bottom: none;">
    <div class="menu flex" style="align-items: center; justify-content: center;">
        <p class="fg0" style="padding-left: 1rem;">Physics EOY Project</p>
    </div>
    <div class="search"></div>
    <div class="status" style="padding-right: 1rem;">
        <button class="button-box show-on-light-mode-only" style="margin-top: 0px;" onclick={() => {
            document.documentElement.classList.remove("theme-flight");
            document.documentElement.classList.add("theme-fdark");
            if (window.localStorage) {
                window.localStorage.setItem("physicseoyproj:theme", "dark");
            }
        }}>
            <MoonIcon></MoonIcon>
        </button>
        <button class="button-box show-on-dark-mode-only" style="margin-top: 0px;" onclick={() => {
            document.documentElement.classList.remove("theme-fdark");
            document.documentElement.classList.add("theme-flight");
            if (window.localStorage) {
                window.localStorage.setItem("physicseoyproj:theme", "light");
            }
        }}>
            <SunIcon></SunIcon>
        </button>
    </div>
</header>
<div style="min-height: 70vh;">
    {@render children()}
</div>
<div class="footer" style="padding-top: 2rem;">
    <div class="flex" style="justify-content: center;">
        <div style="text-align: start;">
            <p class="fg0">AP Physics 1 End-of-Year Project 2026</p>
            <p class="fg0" style="margin-top: 0.4rem;">Ehan A</p>
        </div>
    </div>
    <a class="button faint" href="https://github.com/ehanahamed/physics-eoy-project">
        <GHIcon></GHIcon> See Source Code
    </a>
</div>

<style>
:global {
    .theme-flight .show-on-light-mode-only,
    .theme-fdark .show-on-dark-mode-only,
    .theme-flight button.show-on-light-mode-only,
    .theme-fdark button.show-on-dark-mode-only,
    .theme-flight .button.show-on-light-mode-only,
    .theme-fdark .button.show-on-dark-mode-only {
        display: block;
    }
    .theme-flight .show-on-dark-mode-only,
    .theme-fdark .show-on-light-mode-only,
    .theme-flight button.show-on-dark-mode-only,
    .theme-fdark button.show-on-light-mode-only,
    .theme-flight .button.show-on-dark-mode-only,
    .theme-fdark .button.show-on-light-mode-only {
        display: none;
    }
    @media (prefers-color-scheme: light) {
        .show-on-dark-mode-only,
        button.show-on-dark-mode-only,
        .button.show-on-dark-mode-only {
            display: none;
        }
        .show-on-light-mode-only,
        button.show-on-light-mode-only,
        .button.show-on-light-mode-only {
            display: block;
        }
        .theme-flight .show-on-light-mode-only,
        .theme-fdark .show-on-dark-mode-only,
        button.theme-flight .show-on-light-mode-only,
        button.theme-fdark .show-on-dark-mode-only,
        .button.theme-flight .show-on-light-mode-only,
        .button.theme-fdark .show-on-dark-mode-only {
            display: block;
        }
        .theme-flight .show-on-dark-mode-only,
        .theme-fdark .show-on-light-mode-only,
        button.theme-flight .show-on-dark-mode-only,
        button.theme-fdark .show-on-light-mode-only,
        .button.theme-flight .show-on-dark-mode-only,
        .button.theme-fdark .show-on-light-mode-only {
            display: none;
        }
    }
    @media (prefers-color-scheme: dark) {
        .show-on-light-mode-only,
        button.show-on-light-mode-only,
        .button.show-on-light-mode-only {
            display: none;
        }
        .show-on-dark-mode-only,
        button.show-on-dark-mode-only,
        .button.show-on-dark-mode-only {
            display: block;
        }
        .theme-flight .show-on-light-mode-only,
        .theme-fdark .show-on-dark-mode-only,
        button.theme-flight .show-on-light-mode-only,
        button.theme-fdark .show-on-dark-mode-only,
        .button.theme-flight .show-on-light-mode-only,
        .button.theme-fdark .show-on-dark-mode-only {
            display: block;
        }
        .theme-flight .show-on-dark-mode-only,
        .theme-fdark .show-on-light-mode-only,
        button.theme-flight .show-on-dark-mode-only,
        button.theme-fdark .show-on-light-mode-only,
        .button.theme-flight .show-on-dark-mode-only,
        .button.theme-fdark .show-on-light-mode-only {
            display: none;
        }
    }
}
</style>
