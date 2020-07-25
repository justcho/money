<template>
    <Layout>
        <div class="navBar">
            <span class="leftIcon"></span>
            <span class="title">标签自定义</span>
            <span class="rightIcon"></span>
        </div>
        <div class="tags">
            <router-link class="tag"
                         v-for="tag in tags" :key="tag.id"
                         :to="`/labels/edit/${tag.id}`">
                <span>{{tag.name}}</span>
                <Icon name="right"/>
            </router-link>
        </div>
        <div class="createTag-wrapper">
            <Button class="createTag"
                    @click="createTag">新建标签
            </Button>
        </div>

    </Layout>

</template>

<script lang="ts">

  import Vue from 'vue';
  import {Component} from 'vue-property-decorator';
  import Button from '@/components/Button.vue';
  import {mixins} from 'vue-class-component';
  import TagHelper from '@/mixins/TagHelper';


  @Component({
    components: {Button},
  })
  export default class Labels extends mixins(TagHelper) {
    get tags(){
      return this.$store.state.tagList;
    }
    beforeCreate() {
      this.$store.commit('fetchTags');
    }
  }
</script>

<style lang="scss" scoped>
    .navBar {
        text-align: center;
        font-size: 24px;
        height: 64px;
        color: white;
        background: #2D2B2B;
        display: flex;
        align-items: center;
        justify-content: space-between;


        > .leftIcon {
            width: 24px;
            height: 24px;
        }

        > .rightIcon {
            width: 24px;
            height: 24px;
        }
    }
    .tags {
        background: #ffffff;
        font-size: 16px;
        padding-left: 16px;

        > .tag {
            min-height: 44px;
            display: flex;
            align-items: center;
            justify-content: space-between;
            border-bottom: 1px solid #e6e6e6;

            svg {
                width: 18px;
                height: 18px;
                color: #666;
                margin-right: 16px;
            }
        }
    }

    .createTag {
        background: #E92525;
        color: white;
        border-radius: 4px;
        border: none;
        height: 40px;
        padding: 0 16px;

        &-wrapper {
            text-align: center;
            padding: 16px;
            margin-top: 44-16px;
        }
    }
</style>
