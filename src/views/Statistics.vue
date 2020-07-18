<template>
    <Layout>
        <Tabs class-prefix="type" :data-source="recordTypeList" :value.sync="type"/>
        <Tabs class-prefix="interval" :data-source="intervalList" :value.sync="interval"/>
        <div>
            type: {{type}}
            <br/>
            interval: {{interval}}
        </div>
    </Layout>
</template>

<style scoped lang="scss">
    ::v-deep .type-tabs-item {
        background: #2D2B2B;
        &.selected {
            background: #E92525;
            &::after {
                display: none;
            }
        }
    }

</style>


<script lang="ts">

  import Vue from 'vue';
  import {Component} from 'vue-property-decorator';
  import Tabs from '@/components/Tabs.vue';
  import intervalList from '@/constants/intervalList';
  import recordTypeList from '@/constants/recordTypeList';

  @Component({
    components: {Tabs},
  })
  export default class Statistics extends Vue {
    type = '-';
    interval = 'day';
    intervalList = intervalList;
    recordTypeList = recordTypeList;
  }
</script>
