<script setup>
import TableElement from '../components/table_element.vue';
</script>


<template>
    <CustomerPage>
        <div class="card-header">
            <ul class="nav nav-pills card-header-pills text-center">
                <li class="nav-item me-2 mt-1">
                    <a class="nav-link nav-button" href="#" id="last" style="width: 100px">上月</a>
                </li>
                <li class="nav-item">
                    <a class="nav-link mt-1 nav-button" href="#" id="this" style="width: 100px">本月</a>
                </li>

                <li class="nav-item mx-2 ms-auto">
                    <button class="nav-link active button" id="setting_button" style="width: 50px;height:45px;"
                        data-bs-toggle="modal" data-bs-target="#exampleModalsalary"><ion-icon name="cog-outline"
                            class="element-rotate" id="setting_icon"
                            style="font-size:28px;margin-left:-5px"></ion-icon></button>
                </li>

                <li class="nav-item mx-2">
                    <a class="nav-link button" href="#" id="salary"
                        style="width: 50px;height:45px;padding-top:.6rem"><ion-icon name="cash-outline"
                            style="font-size: 28px;margin-left:-5px"></ion-icon></a>
                </li>
            </ul>
        </div>
        <div class="card-body pt-0 rounded-4" style="overflow-y: scroll;">
            <TableElement :label="['id','名稱','工作地點','工作時數','加班時數','刪除']" :delete_button=true>
            </TableElement>
        </div>
    </CustomerPage>
</template>

<style>

@keyframes fade-in {
    0% {
        color: black;
        scale: 1;
    }

    100% {
        background-color: #5a69ec;
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
.nav-button:hover {
    animation-name: fade-in-scaless;
    animation-duration: .2s;
    animation-fill-mode: forwards;
    animation-timing-function: ease-in;
}
@keyframes fade-in-scaless {
    0% {
        color: black;
    }

    100% {
        background-color: #5a69ec;
        color: white;
    }

}

</style>