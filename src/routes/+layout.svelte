<script lang="ts">
	import RandomBg from "$lib/components/randomBg.svelte";
    import "../app.css";
</script>

<div class=" fixed top-0 left-0 -z-50">
    <RandomBg animated>
        <div class="body h-screen w-screen" />
    </RandomBg>
</div>
    
<slot/>

<style lang="postcss">
</style>