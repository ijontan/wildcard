<script lang="ts">
	import RandomBg from "$lib/components/randomBg.svelte";
    import "../app.css";
    import { onMount } from "svelte";

    onMount(() => {
        setTimeout(() => {
            alert("YOu are takING too LoNG to reAD this page! All your DAta iS goINg to be DElETED!");
            window.location.href = "/";
        }, 60000);
    })
</script>

<div class=" fixed top-0 left-0 -z-50">
    <RandomBg animated>
        <div class="body h-screen w-screen" />
    </RandomBg>
</div>
    
<slot/>

<style lang="postcss">
</style>