<script setup>
import { ref } from 'vue';
const current_date=ref(new Date());
const current_year=current_date.value.getFullYear();
console.log(current_year)
</script>

<template>
    <CopyRight>
        <div class="container-fluid text-center text-secondary pt-2 vw-100">
            <span class="text-center">
                Copyright © Timothychen & Timhu {{current_year}}
            </span>
        </div>
    </CopyRight>
</template>

<style></style>