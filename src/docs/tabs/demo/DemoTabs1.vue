<script setup lang="ts">
import { ref } from 'vue';
import { LewMessage } from 'lew-ui';

type Options = {
    label: string;
    value: string;
    activeIndex: number;
};

const options = ref([
    { label: '北京', value: '1' },
    { label: '上海', value: '2' },
    { label: '广州', value: '3' },
    { label: '深圳', value: '4' },
    { label: '乌鲁木齐', value: '5' },
]);

let value = ref('');

const change = (e: Options) => {
    console.log(e);
    LewMessage.info(e.label);
};
</script>

<template>
    <lew-tabs
        style="width: 400px"
        v-model="value"
        :options="options"
        @update:change="change"
    />
</template>
