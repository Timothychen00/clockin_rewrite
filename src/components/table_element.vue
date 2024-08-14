<script setup>
import { computed, ref } from 'vue';

const Props = defineProps({
    label: Array,
    delete_button: Boolean,
})

const columns = computed(() => {
    console.log(Props.label.length)
    return Props.label.length
})

</script>

<template>
    <TableElement class="d-flex p-0 row ps-3" style="overflow-y:scroll;">
        <div class="d-flex tb-top row py-1 mt-2 mb-2">
            <template v-for="index in columns">
                <div class="col tb-head">{{ Props.label[index - 1] }}</div>
            </template>
        </div>
        <div class="d-flex row mt-1 ">
            <template v-for="index in columns - 1">
                <div class="col tb-element">1</div>
            </template>
            <div class="col tb-element ps-5 pe-0 d-inline-flex justify-content-end">
                <button class="bg-danger h-100 pt-0 simple-button " style="width: 120px;">刪除</button>
            </div>
        </div>
        <template v-for="_ in 10">
            <div class="d-flex row">
                <template v-for="index in columns - 1">
                    <div class="col tb-element">1</div>
                </template>
                <div class="col tb-element ps-5 pe-0 d-inline-flex justify-content-end">
                    <button class="bg-danger h-100 pt-0 simple-button" style="width: 120px;" >刪除</button>
                </div>
            </div>
        </template>
    </TableElement>
</template>

<style scoped>
.tb-element:nth-of-type(1) {
    border: rgb(186, 186, 186) solid 1px;
    border-top-left-radius: 1rem;
    border-bottom-left-radius: 1rem;
    border-right: 0;
}

.tb-element:last-of-type {
    border: rgb(186, 186, 186) solid 1px;
    border-top-right-radius: 1rem;
    border-bottom-right-radius: 1rem;
    border-left: 0;
    /* border-radius: 1rem; */
}

.tb-element {
    height: var(--height);
    --height: 50px;
    line-height: var(--height);
    margin-bottom: 6px;
    color: rgb(0, 0, 0);
    box-shadow: 0 1px 1px rgb(215, 215, 215);
    background: rgb(255, 255, 255);
    border-top: 1px solid rgb(186, 186, 186);
    border-bottom: 1px solid rgb(186, 186, 186);
}

.tb-head {
    border-bottom: 1px solid grey;
    margin-top: 0;
    height: 30px;
    font-weight: 500;
}

.tb-head::after {
    content: '';
}
.simple-button:hover {
    scale: 1.04;
}
.simple-button {
    scale: 1.00;
    animation-fill-mode: forwards;
    transition: .1s;
    animation-timing-function: ease-in;
}
</style>
