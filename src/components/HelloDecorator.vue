<!-- src/components/HelloDecorator.vue -->
<!-- This is an alternative way to define the Hello component using decorators -->
<template>
    <div>
        <div class="greeting">Hello {{name}}{{exclamationMarks}}</div>
        <button @click="decrement">-</button>
        <button @click="increment">+</button>
    </div>
</template>

<script lang="ts">
    // vue-property-decoratorをインポートすることで、Typescriptでコンポーネントを記述することができる。
    import {Component, Prop, Vue} from "vue-property-decorator";
    // import {Component, Prop, Vue} from "vue-property-decorator";

    @Component
    export default class HelloDecorator extends Vue {
        @Prop() name!: string;
        @Prop() initialEnthusiasm!: number;

        enthusiasm = this.initialEnthusiasm;

        increment() {
            this.enthusiasm++;
        }

        decrement() {
            if (this.enthusiasm > 1) {
                this.enthusiasm--;
            }
        }

        get exclamationMarks(): string {
            return Array(this.enthusiasm + 1).join('!');
        }
    }
</script>

<style>
    .greeting {
        font-size: 20px;
    }
</style>
