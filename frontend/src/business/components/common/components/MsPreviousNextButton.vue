<template>
  <span class="previous-next-button">
    <span class="head-right-tip" v-if="countNum === total">
      {{ $t('test_track.plan_view.pre_case') }} : {{list[index - 1] ? list[index - 1].name : ''}}
    </span>
    <span class="head-right-tip" v-if="countNum !== total">
      {{ $t('test_track.plan_view.next_case') }} : {{list[index + 1] ? list[index + 1].name : ''}}
    </span>

    <el-button plain size="mini" icon="el-icon-arrow-up" :disabled="countNum <= 1" @click="handlePre()"/>
    <span>
      {{ countNum }}/{{ total }}
    </span>
    <el-button plain size="mini" icon="el-icon-arrow-down" :disabled="countNum >= total" @click="handleNext()"/>
  </span>
</template>

<script>
    export default {
      name: "MsPreviousNextButton",
      data() {
        return {

        }
      },
      props: {
        list: {
          type: Array,
          default() {
            return []
          }
        },
        index: {
          type: Number,
          default() {
            return 0
          }
        },
        pageTotal: {
          type: Number,
          default() {
            return 0
          }
        },
        total: {
          type: Number,
          default() {
            return 0
          }
        },
        pageNum: {
          type: Number,
          default() {
            return 0
          }
        },
        pageSize: {
          type: Number,
          default() {
            return 0
          }
        }
      },
      computed: {
        countNum() {
          return this.pageSize * (this.pageNum - 1) + this.index + 1;
        }
      },
      methods: {
        handlePre() {
          this.$emit('pre');
        },
        handleNext() {
          this.$emit('next');
        }
      }
    }
</script>

<style scoped>

  .head-right-tip {
    color: darkgrey;
  }

</style>
