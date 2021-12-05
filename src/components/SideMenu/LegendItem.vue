<template>
    <div class="legend-item">
        <div class="legend-item__marker">
            <div
                class="marker"
                :style="{ '--marker-color': color }"
            />
        </div>
        <div class="legend-item__label">{{ text }}</div>
        <div class="legend-item__counter">{{ counter }}</div>
    </div>
</template>

<script>
export default {
    props: {
        color: {
            type: String,
            default: '#fff',
        },
        text: {
            type: String,
            required: true,
        },
        counter: {
            type: Number,
            default: 0,
        },
    },
};
</script>

<style scoped>
.legend-item {
    display: flex;
    align-items: center;
}

.legend-item .legend-item__marker .marker {
    width: 18px;
    height: 18px;
    background-color: var(--marker-color);
    border: 1px solid #bababa;
    border-radius: 5px;
}

.legend-item .legend-item__label {
    flex-basis: 100%;
    margin: 0 24px;
}

.legend-item .legend-item__counter {
    color: #8e8e8e;
    font-size: 0.9rem;
}
</style>
