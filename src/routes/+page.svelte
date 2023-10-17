<script lang="ts">
	import { goto } from "$app/navigation";
	import Button from "$lib/components/button.svelte";
	import DatePicker from "$lib/components/datePicker.svelte";
	import Dialog from "$lib/components/dialog.svelte";
	import RandomBg from "$lib/components/randomBg.svelte";
    import Text from "$lib/components/text.svelte";
	import TextBox from "$lib/components/textBox.svelte";
	import type { NoteData } from "$lib/modal/note";
	
    let dialog_open = false;
    let randomTextNum = 0;
    function addRandomText() {
        alert("Sinced you annoyed me by clicking and not wanting to do action, I am going to punish you by adding random textt to your screen!");
        randomTextNum++;
    }

    let newNote: NoteData = {
        title: "",
        description: "",
        date: "1-1-2000"
    }

    let notes: NoteData[] = []

    let onHover = false;
</script>

<Text text="NoTE  APp" minSize={2}/>
<Text text="App where you can write note only last 60 seconds" />
<Button text="click_Me_to_add_new_notes" clickAction={() => {dialog_open = true}} didntClickAction={addRandomText}/>
    {#each Array.from({length: randomTextNum}) as _, i}
    <Text text={`
Lorem ipsum dolor sit amet, consectetur adipiscing elit. Phasellus convallis placerat porttitor. Nam blandit placerat tortor et pretium. Ut dapibus, purus quis ullamcorper consequat, nibh nisi porta neque, eu placerat quam nunc quis nunc. Vivamus sit amet aliquam ligula. Nulla felis sem, commodo congue dui in, consequat euismod ligula. Vivamus ornare vel dui vitae dictum. Quisque egestas, justo ut pulvinar accumsan, augue tellus cursus augue, non suscipit velit lectus non tortor. Nunc quis sem sodales, ultricies nibh sed, molestie urna. Vestibulum at augue vitae ex sollicitudin tristique et suscipit felis. Vivamus finibus consectetur sem. Curabitur in semper lacus, a volutpat nibh. Sed id eros scelerisque, placerat ipsum id, iaculis ex. Cras bibendum varius mi, eget aliquet nulla posuere et. Aliquam fermentum erat justo, eu cursus massa elementum non. Suspendisse vehicula consequat leo, eu gravida massa auctor sed. Vestibulum finibus sapien pretium, vehicula ex sit amet, lacinia lacus.
`} />
<Text text={`
Ut augue tellus, rhoncus nec tincidunt at, lobortis in nulla. Morbi lacinia quam sed enim laoreet, in molestie quam dapibus. Nunc ipsum mi, efficitur a orci et, vehicula hendrerit risus. Vivamus sed arcu est. Quisque eros enim, tristique eu suscipit quis, maximus a dui. Morbi tincidunt semper velit, ac blandit enim. Donec porta commodo bibendum.
`}/>
<Text text={`
Quisque nibh odio, rutrum vel pulvinar quis, pellentesque at ligula. Phasellus suscipit, urna non vestibulum molestie, sem erat pretium quam, et maximus leo leo vitae sapien. Morbi et tristique velit, et volutpat eros. Class aptent taciti sociosqu ad litora torquent per conubia nostra, per inceptos himenaeos. Curabitur fringilla mauris ac diam efficitur, pretium tempor augue vehicula. Nulla euismod, purus non iaculis pulvinar, urna massa commodo sapien, eget venenatis velit orci vitae est. Etiam tincidunt malesuada tortor, id commodo massa suscipit ut. Sed porta fermentum ante ut sodales. Donec mollis risus mi, in vestibulum massa fermentum vel.
`}/>
<Text text={`
Fusce tortor nibh, malesuada eget sem in, laoreet ultricies nunc. Donec ac vehicula lorem. Class aptent taciti sociosqu ad litora torquent per conubia nostra, per inceptos himenaeos. In sodales purus nisl, a dapibus justo viverra et. Suspendisse potenti. Mauris auctor odio pretium mauris egestas aliquet. Morbi eget diam vitae neque consectetur rutrum. Maecenas massa mi, tempor vel accumsan ut, faucibus ut est. Cras vitae ullamcorper metus. Aliquam a elit auctor, sollicitudin elit vitae, venenatis metus. Etiam convallis fermentum tincidunt. Nunc mauris enim, bibendum eget maximus eu, aliquet et enim.
`}/>
<Text text={`
Fusce diam tortor, egestas ut porta nec, pharetra nec ante. Nam dui dui, ultrices fringilla auctor quis, bibendum a nibh. Aenean eu augue leo. Ut eget tortor luctus, pretium sem et, volutpat dui. Phasellus tristique, nisl id euismod fermentum, augue odio mattis augue, quis dictum nisi felis eget ex. Sed eu lacus vitae ante semper ornare. Phasellus aliquet nisi quam, sit amet rutrum leo bibendum eu. Donec sodales egestas lorem, sit amet imperdiet risus. Donec aliquet pulvinar ullamcorper. Phasellus non sem sit amet diam lacinia sagittis. Pellentesque eu nisi erat. Pellentesque mattis dui urna, non vulputate lacus pharetra id. Aenean eget tincidunt velit. Proin malesuada enim sed libero lacinia finibus. Ut urna dolor, egestas ut quam ut, euismod cursus quam.
`}/>
    {/each}

{#each notes as note}
    <div class="flex">
        <Text text={note.title} animated={note.title === "animate"}/>
        <Text text={note.description} animated={note.title === "animate"}/>
        <Text text={note.date} animated={note.title === "animate"}/>
    </div>
{/each}

<Dialog show={dialog_open}>
    <RandomBg>
        <div class=" w-[700px] h-[200px] flex flex-col overflow-y-scroll">
            <TextBox  bind:value={newNote.title} />
            <TextBox title="Description" bind:value={newNote.description} />

            <DatePicker bind:value={newNote.date} />
            <div class="flex flex-row justify-between">
                <button on:click={() => {
                    notes = [...notes, newNote];
                    newNote = {
                        title: "",
                        description: "",
                        date: "1-1-2000"
                    }
                    dialog_open = false
                }}>
                    <p class=" opacity-5">Click me to submit</p>
                </button>
                <button on:click={() => {dialog_open = false
                newNote = {
                    title: "",
                    description: "",
                    date: "1-1-2000"
                }
                }}
                    on:mouseenter={() => {onHover = true}}
                    on:mouseleave={() => {onHover = false}}
                    >
                    <RandomBg>
                        <Text text={onHover? "cancel": "submit"}/>
                    </RandomBg>
                </button>
            </div>
        </div>
    </RandomBg>
</Dialog>