<template>
  <el-dialog
    :title="$t('report.rename_report')"
    :visible.sync="dialogVisible"
    width="40%"
    :modal-append-to-body="false"
    :before-close="close">
    <el-form>
      <el-form-item :label="$t('commons.name')">
        <el-input v-model="data.name"></el-input>
      </el-form-item>
    </el-form>

    <span slot="footer" class="dialog-footer">
        <el-button @click="close">{{ $t('commons.cancel') }}</el-button>
        <el-button type="primary" @click="submit">{{ $t('commons.confirm') }}</el-button>
    </span>
  </el-dialog>
</template>

<script>
export default {
  name: "MsRenameReportDialog",
  data() {
    return {
      dialogVisible: false,
      data: {}
    };
  },
  methods: {
    open(data) {
      this.dialogVisible = true;
      this.data = JSON.parse(JSON.stringify(data));
    },
    submit() {
      this.$emit('submit', this.data);
    },
    close() {
      this.dialogVisible = false;
    }
  }
}
</script>

<style scoped>

</style>
