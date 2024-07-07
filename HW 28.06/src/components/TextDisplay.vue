<template>
    <div class="text-display">
        <p>{{ text }}</p>
    </div>
</template>

<script>
export default {
    props: ['initialText'],
    data() {
        return {
            text: this.initialText
        };
    },
    methods: {
        updateText(newText) {
            this.text = newText;
        }
    },
    watch: {
        initialText(newVal) {
            this.text = newVal;
        }
    }
};
</script>

<style scoped>
.text-display {
    margin-bottom: 20px;
}

.text-display p {
    font-size: 18px;
}
</style>
