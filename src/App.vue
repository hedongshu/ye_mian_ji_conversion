<template>
  <div>
    <div>
      <input
        type="file"
        name=""
        id=""
      >
    </div>

    <div>
      <!-- 经验公式 -->
      <div>
        <check-component
          span='经验公式'
          :value='0'
          v-model="conversionType"
        />

      </div>

      <!-- 校正系数 -->
      <div>
        <check-component
          span='校正系数'
          :value='1'
          v-model="conversionType"
        />

        <div>
          <h3>数据采集类型</h3>

        </div>
      </div>
    </div>

    <div>
      <button type="button">开始转换</button>
    </div>

  </div>
</template>

<script lang="ts">
import { defineComponent, reactive, ref, watch } from "vue";
import CheckComponent from "@/components/Check.vue";

interface AppConfig {
  conversion_type: string;
}

enum conversionTypeEnum {
  "经验公式",
  "校正系数",
}
enum collectTypeEnum {
  "LAI-2200",
  "DHP",
  "TRAC",
}
enum treeTypeEnum {
  "阔叶林",
  "针叶林",
  "针阔混交",
}

export default defineComponent({
  components: {
    CheckComponent,
  },
  setup() {
    const conversionType = ref<conversionTypeEnum>(
      conversionTypeEnum["经验公式"]
    );
    const collectType = ref<collectTypeEnum>(collectTypeEnum["LAI-2200"]);
    const treeType = ref<treeTypeEnum>(treeTypeEnum["阔叶林"]);

    watch(conversionType, (value) => {
      console.log(value);
    });

    return {
      conversionType,
      collectType,
      treeType,
    };
  },
  computed: {},
});
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}
</style>
