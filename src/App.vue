<script setup>
import { computed, ref } from 'vue';
import CopyRight from './components/copyright.vue'
import DashBoardItem from './components/dash_item.vue'
//import the pages 
import CustomerPage from './pages/customer_manage.vue'
import SettingPage from './pages/setting.vue'
import ReportPage from './pages/report.vue'
import NotificationPage from './pages/notification.vue'


const dash_items = ref({
    "員工管理": "people-outline",
    '通知': "notifications-outline",
    '設定': "hammer-outline",
    '回報': "mail-outline"
})
const pages = ref({
    "員工管理": CustomerPage,
    '通知': NotificationPage,
    '設定': SettingPage,
    '回報': ReportPage
});
console.log(pages)

const current_page = ref("員工管理");

function handle_switch_page(page, b) {
    console.log('switch_tab', page, b);
    if (page !== current_page.value) {
        console.log('調整')
        current_page.value = page;
    }

}

</script>

<template>
    <div class="container-fluid m-0 w-100 py-0 d-inline-flex ps-0 animation" style="height:10vh">
        <div class="col-2 text-start ps-4 d-inline-flex pt-3">
            <div class="button rounded-4 col-3 text-center pt-2 " style="height:50px;">
                <ion-icon name="menu-outline" style="font-size: 32px;" class=""></ion-icon>
            </div>
            <div class="col-10 text-center h5" style="padding-top: .7rem;">
                <span>客戶名稱</span>
            </div>
        </div>
        <div class="col-10 pt-3 d-inline-flex ps-0">
            <input type="text" style="width: 750px;height:50px" class="rounded-3 shadow focus-input">
        </div>
    </div>

    <div class="container-fluid p-0 w-100 m-0">
        <div class="row justify-content-center m-0 pe-4" style="height: 85vh;">
            <div class="col-lg-2  d-lg-flex m-0 py-0 px-4 animation-floating flex-column justify-content-between">
                <div>
                    <template v-for="icon, dash_item in dash_items">
                        <DashBoardItem :item_name="dash_item" :icon_name="icon"
                            @switch_page="handle_switch_page($event, dash_item)"
                            :class="{ active: current_page == dash_item }" class="button">
                        </DashBoardItem>
                    </template>
                </div>

                <div style="margin-bottom: 0 !important;" class="dropdown d-inline-flex row mx-1 p-0" >
                    <button onclick="location.href='/logout'" class="content mb-2 button-black"  style="z-index: -999!important;position: absolute;">logout</button>
                    <DashBoardItem item_name="Timothychen" class="bg-white simple-button avatar" src="/avatar.jpeg" style="font-weight: 100;font-family:'Trebuchet MS', 'Lucida Sans Unicode', 'Lucida Grande', 'Lucida Sans', Arial, sans-serif;"></DashBoardItem>

                </div>
            </div>

            <component class="col-lg-10 col-12 card shadow p-0 animation" :is="pages[current_page]" style="max-height: 85vh">
            </component>
        </div>
    </div>
    <div class="container-fluid w-100">

    </div>

    <CopyRight />

</template>

<style scoped>


.button:hover {
    animation-name: fade-in;
    animation-duration: .2s;
    animation-fill-mode: forwards;
    animation-timing-function: ease-in;
}

input {
    background-color: white;
    border: 1px rgb(177, 177, 177) dashed;
    outline: rgb(177, 177, 177);
    color: #5a69ec !important;
    padding-left: .8rem;
}

a {
    color: #5a69ec;
}

.animation {
    animation-name: appear;
    animation-duration: 1s;
    animation-fill-mode: forwards;
    animation-timing-function: ease;
}

.animation-floating {
    animation-name: floating;
    animation-duration: .3s;
    animation-fill-mode: forwards;
    animation-timing-function: ease-out;
}

.dropdown:hover .content{
    top: -55px;
}

.dropdown .content{
    transition: .3s;
    top: 10px;
}
.dropdown::after{
    content: "";
    margin-top: -100px;
    height: 30px;
    width: 200px;
}


@keyframes simple-button {
    0% {
        scale: 1;
    }

    100% {
        scale: 1.04
    }

}

.simple-button:hover {
    animation-name: simple-button;
    animation-duration: .2s;
    animation-fill-mode: forwards;
    animation-delay: 500ms;
    animation-timing-function: ease-in;
}

.button-black{
    background-color: black;
    transition: .3s;
}
.button-black:hover{
    background-color: black;
    scale: 1.04;
}
.button-black:focus{
    background-color: black;
    scale: 1.05;
}
.avatar{
    border: dashed 4px rgb(74, 95, 164);
}
</style>
