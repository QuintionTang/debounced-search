<template>
    <div :class="$style.container">
        <label :class="$style.label">搜索关键字</label>
        <input
            placeholder="关键字"
            :class="$style.input"
            v-model="query"
            type="text"
        />
        <div :class="$style.result" v-if="query">输入的关键字：{{ query }}</div>
    </div>
</template>

<script>
import { watch, defineComponent } from "vue";
import useDebouncedRef from "./composables/useDebouncedRef";
export default defineComponent({
    setup() {
        const query = useDebouncedRef("", 400);

        watch(query, (newQuery) => {
            // 发起API请求
            console.log({ newQuery });
        });

        return {
            query,
        };
    },
});
</script>

<style module>
*,
*::before,
*::after {
    box-sizing: border-box;
}
.label {
    display: block;
    line-height: 30px;
}
.container {
    width: 1000px;
    margin: 0px auto;
    font-size: 12px;
    font-family: "Microsoft YaHei", "微软雅黑", "pingfang sc", "宋体", Arial,
        Helvetica, sans-serif;
}
.result {
    padding: 15px;
    background: #efefef;
}
.input {
    width: 100%;
    padding: 10px;
    border-radius: 5px;
    border: 1px solid #444;
    margin-top: 5px;
    margin-bottom: 20px;
}
</style>
