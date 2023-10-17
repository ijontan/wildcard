<script lang="ts">
	import { page } from "$app/stores";
	import Button from "$lib/components/button.svelte";
	import Text from "$lib/components/text.svelte";


    let title = $page.url.pathname.split("/").pop();
    let val = 0;
</script>

<div class=" flex flex-col">
    <div class=" self-start">
        <Text text={"Feed Back for" + title}/>
    </div>
    <div class=" self-end">
        <Text text={"HOw Much you rate for this feature"}/>
    </div>
    <div class=" self-center">
        <Text text={"We would Like you hear frOM YoU"}/>
    </div>
    <div class=" self-start">
        <Text text={val.toString()}/>
    </div>
    <div class=" self-end flex flex-row">
        <Button text="+" clickAction={() => {val++;}}/>
        <Button text="-" clickAction={() => {val--;}}/>
    </div>
    <Button text="submit" clickAction={() => {
        alert("thasnk you for your feedback")
    }}/>
</div>


