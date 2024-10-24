<script setup>

import SettingAny from './setting/SettingAny.vue';
import SettingString from './setting/SettingString.vue';
import SettingAccordion from './setting/group/SettingAccordion.vue';
import SettingColumn from './setting/group/SettingColumn.vue';
import SettingRow from './setting/group/SettingRow.vue';
import SettingTab from './setting/group/SettingTab.vue';
import SettingGroup from './setting/group/SettingGroup.vue'

const props = defineProps(['settings', 'depth']);
const settingTypes = {
  'string': SettingString,
  'row': SettingRow,
  'column': SettingColumn,
  'tab': SettingTab,
  'accordion': SettingAccordion,
  'group': SettingGroup,
};

function getComponent(type) {
  return settingTypes[type] ?? SettingAny;
};

function hasItems(setting) {
  return setting.hasOwnProperty('items') && Array.isArray(setting.items) && setting.items.length > 0;
}

</script>
<template>
  <template v-for="setting in settings">
    <component :is="getComponent(setting.type)" :setting="setting" :depth="props.depth+4">
      <RecursiveFactorySetting v-if="hasItems(setting)" :settings="setting.items" :depth="props.depth+4" />
    </component>
  </template>
</template>
