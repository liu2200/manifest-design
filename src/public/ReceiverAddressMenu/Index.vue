<template>
  <el-form v-if="currentComponent" :mode="form" class="receiver-menu-warp" label-position="top" @click.native.stop>

    <el-tabs v-model="tab" type="border-card">
      <el-tab-pane label="内容" name="content">
        <el-form ref="content-form">
        <el-form-item label="地址格式">
          <el-select class="w-100" v-model="currentComponent.props.addressType" size="small">
            <el-option v-for="item in addressStyleOptions" :key="item.value" :value="item.value" :label="item.label" />
          </el-select>
        </el-form-item>
          <el-form-item label="对齐方式">
            <el-select v-model="currentComponent.props.align" class="w-100" size="small">
              <el-option v-for="item in alignOptions" :key="item.value" :label="item.label" :value="item.value" />
            </el-select>
          </el-form-item>
          <el-form-item label="字体类型">
            <el-select v-model="currentComponent.props.fontFamily" class="w-100" size="small">
              <el-option v-for="item in fontFamilyOptions" :key="item.value" :label="item.label" :value="item.value" />
            </el-select>
          </el-form-item>
          <el-form-item label="字体尺寸">
            <el-select v-model="currentComponent.props.fontSize" class="w-100" size="small">
              <el-option v-for="item in fontSizeOptions" :key="item.value" :label="item.label" :value="item.value" />
            </el-select>
          </el-form-item>
          <el-form-item label="文本行距">
            <el-select v-model="currentComponent.props.lineHeight" class="w-100" size="small">
              <el-option v-for="item in lineHeightOptions" :key="item.value" :label="item.label" :value="item.value" />
            </el-select>
          </el-form-item>
          <el-form-item>
            <el-checkbox v-model="currentComponent.props.isBold">字体加粗</el-checkbox>
          </el-form-item>
        </el-form>
      </el-tab-pane>
      <el-tab-pane label="边框" name="board">
        <el-form ref="board-form">
          <el-form-item>
            <el-checkbox v-model="currentComponent.props.hasBorder">显示边框</el-checkbox>
          </el-form-item>
        </el-form>
      </el-tab-pane>
    </el-tabs>
  </el-form>
</template>

<script>
  import {mapGetters} from 'vuex';
  export default {
    data() {
      return {
        tab: 'content',
        form: {
          addressStyleOptions: '',
        },
        addressStyleOptions: [
          {
            label: '省/州城市街道门牌号',
            value: 'ssqjm'
          },
          {
            label: '门牌号街道区城市省/州',
            value: 'jmqss'
          }
        ],
        alignOptions: [
          {
            label: '左对齐',
            value: 'left',
          },
          {
            label: '右对齐',
            value: 'right',
          },
          {
            label: '居中',
            value: 'center',
          },
        ],
        fontFamilyOptions: [
          {
            label: 'Al Bayan',
            value: 'Al Bayan',
          },
          {
            label: 'monospace',
            value: 'monospace',
          },
          {
            label: 'sans-serif',
            value: 'sans-serif',
          },
        ],
        fontSizeOptions: [
          {
            label: '12px',
            value: '12px',
          },
          {
            label: '14px',
            value: '14px',
          },
          {
            label: '16px',
            value: '16px',
          },
          {
            label: '18px',
            value: '18px',
          },
          {
            label: '24px',
            value: '24px',
          },
          {
            label: '30px',
            value: '30px',
          },
          {
            label: '36px',
            value: '36px',
          },
          {
            label: '48px',
            value: '48px',
          },
          {
            label: '60px',
            value: '60px',
          },
          {
            label: '72px',
            value: '72px',
          },
        ],
        lineHeightOptions: [
          {
            label: '1倍',
            value: '1',
          },
          {
            label: '1.5倍',
            value: '1.5',
          },
          {
            label: '2倍',
            value: '2',
          },
          {
            label: '2.5倍',
            value: '2.5',
          },
          {
            label: '3倍',
            value: '3',
          },
        ],
      };
    },
    computed: {
      ...mapGetters(['activeComponent', 'storeList']),
      currentComponent() {
        const { id = '' } = this.activeComponent;
        return this.storeList.find((item) => item.id === id);
      },
    },
    methods: {
      init() {
        // doing
      },
    },
  };
</script>

<style lang="scss">
  .receiver-menu-warp {
    height: calc(100% - 53px);
    display: flex;
    flex-direction: column;
  }
</style>
