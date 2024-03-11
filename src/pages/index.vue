<script setup lang="ts">
import Picker from 'nutui-uniapp/components/picker/picker.vue'
import Popup from 'nutui-uniapp/components/popup/popup.vue'
import type { PickerOption } from 'nutui-uniapp'

const columns = ref<PickerOption[]>([
  { text: '南京市', value: 'NanJing' },
  { text: '无锡市', value: 'WuXi' },
  { text: '海北藏族自治区', value: 'ZangZu' },
  { text: '北京市', value: 'BeiJing' },
  { text: '连云港市', value: 'LianYunGang' },
  { text: '浙江市', value: 'ZheJiang' },
  { text: '江苏市', value: 'JiangSu' },
])

const visible = ref(false)

const val = ref<string[]>([])
let defaultVal: string[] = []
function show() {
  defaultVal = toRaw(val.value)
  visible.value = true
}

function handleConfirm(data: any) {
  val.value = data.selectedValue
  visible.value = false
}
</script>

<template>
  <view>
    <view @click="show">
      <view>val -- {{ val }}</view>
      <view>defaultVal -- {{ defaultVal }}</view>
    </view>
  </view>
  <Popup v-model:visible="visible" position="bottom">
    <Picker :model-value="defaultVal" :columns="columns" @confirm="handleConfirm" @cancel="visible = false" />
  </Popup>
</template>

<style></style>

<route type="home" lang="json">
{}
</route>
