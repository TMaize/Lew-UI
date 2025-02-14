<script lang="ts" setup>
import { Dismiss24Filled } from '@vicons/fluent';
import { Icon } from '@vicons/utils';
import { useLewTo } from '../../../hooks';
import _props from './props';
const { lewTo } = useLewTo();

const props = defineProps(_props);

const emit = defineEmits(['close']);
const close = () => {
    if (props.disabled) {
        return;
    }
    emit('close');
};
</script>

<template>
    <div
        class="lew-tag"
        :class="`lew-tag-${size} lew-tag-${type} ${
            round ? 'lew-tag-round' : ''
        } ${disabled ? 'lew-tag-disabled' : ''} ${to ? 'lew-tag-to' : ''}`"
        @click="lewTo(to)"
    >
        <div class="lew-tag-left"><slot name="left"></slot></div>
        <div class="lew-tag-value">
            <slot></slot>
        </div>
        <div class="lew-tag-right"><slot name="right"></slot></div>
        <div v-if="closable" class="lew-tag-close" @click.stop="close">
            <Icon><Dismiss24Filled /></Icon>
        </div>
    </div>
</template>

<style lang="scss">
.lew-tag {
    display: inline-flex;
    align-items: center;
    justify-content: center;
    border-radius: 3px;
    user-select: none;

    .lew-tag-value {
        display: inline;
        font-weight: normal;
        padding: 0px 3px;
        box-sizing: border-box;
        white-space: nowrap;
    }

    .lew-tag-close {
        display: inline-flex;
        align-items: center;
        justify-content: center;
        width: 8px;
        height: 8px;
        border-radius: 3px;
        margin-left: -3px;
        padding: 5px;
        cursor: pointer;
    }
    .lew-tag-close:hover {
        background-color: rgba($color: #000, $alpha: 0.1);
    }
    .lew-tag-close:active {
        background-color: rgba($color: #000, $alpha: 0.2);
    }
    .lew-tag-left {
        margin-left: 3px;
        display: inline-flex;
        align-items: center;
        box-sizing: border-box;
    }
    .lew-tag-right {
        margin-right: 3px;
        display: inline-flex;
        align-items: center;
    }
}
.lew-tag-to {
    cursor: pointer;
}
.lew-tag-small {
    height: 18px;
    line-height: 18px;
    padding: 0px 2px 0px 2px;
    font-size: 10px;
    .lew-tag-close {
        border-radius: 2px;
        padding: 2px;
        font-size: 12px;
        margin-right: 1px;
    }
}
.lew-tag-medium {
    height: 22px;
    line-height: 22px;
    padding: 0px 4px;
    font-size: 13px;
    .lew-tag-close {
        border-radius: 3px;
        padding: 4px;
        font-size: 13px;
    }
}
.lew-tag-large {
    height: 26px;
    line-height: 26px;
    padding: 0px 5px;
    font-size: 14px;
    .lew-tag-close {
        border-radius: 4px;
        padding: 6px;
        font-size: 14px;
    }
}

.lew-tag-round {
    border-radius: 35px;
    .lew-tag-close {
        border-radius: 35px;
    }
}

.lew-tag-primary {
    background-color: var(--lew-primary-color-light);
    color: var(--lew-primary-text-color);
}
.lew-tag-info {
    color: var(--lew-info-text-color);
    background-color: var(--lew-info-color-light);
}
.lew-tag-success {
    color: var(--lew-success-text-color);
    background-color: var(--lew-success-color-light);
}

.lew-tag-warning {
    color: var(--lew-warning-text-color);
    background-color: var(--lew-warning-color-light);
}
.lew-tag-error {
    color: var(--lew-error-text-color);
    background-color: var(--lew-error-color-light);
}
.lew-tag-normal {
    color: var(--lew-normal-text-color);
    background-color: var(--lew-normal-color-light);
}
.lew-tag-disabled {
    opacity: var(--lew-disabled-opacity);
    cursor: not-allowed;
    .lew-tag-close {
        cursor: not-allowed;
    }
    .lew-tag-close:hover {
        background-color: rgba(0, 0, 0, 0);
    }
}
</style>
