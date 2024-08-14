<script setup>

const Props = defineProps({ item_name: String, icon_name: String, src:{
    type:String,
    default:' '
} })
const emit = defineEmits(["switch_page"])
function handle_click(e) {
    console.log(Props.item_name)
    emit("switch_page", Props.item_name)
}

</script>


<template>
    <DashBoardItem class=" p-2 mb-3 d-flex align-items-center justify-content-center shadow rounded-4"
        @click="handle_click" style="height:70px;">
        <template v-if="Props.src==' '">
            <ion-icon style="font-size: 28px;" :name="Props.icon_name"></ion-icon>
        </template>
        <template v-else>
            <img :src="Props.src" alt="8" style="height: 25px;" class="rounded">
        </template>
        <b id="word-3" class="ms-2"> {{ Props.item_name }}</b>
    </DashBoardItem>
</template>

<style>
.rounded-4 {
    border-radius: .8rem;
}

@keyframes fade-in {
    0% {
        color: black !important;
        scale: 1;
    }

    100% {
        background-color: #5a69ec !important;
        color: white;
        scale: 1.04
    }

}

.button:hover {
    animation-name: fade-in;
    animation-duration: .2s;
    animation-fill-mode: forwards;
    animation-timing-function: ease-in;
}

.active {
    background-color: #5a69ec !important;
    color: white;
    scale: 1.04
}
</style>