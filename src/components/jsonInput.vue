<template>
  <div class="input-area">
    <el-input
      v-model="inputText"
      type="textarea"
      :rows="4"
      :placeholder="placeholder"
      resize="none"
      @input="handleInput"
    >
    </el-input>
    <div class="input-footer">
      <span class="word-count">{{ inputText.length }}/2000</span>
      <el-button type="primary" size="small" @click="handleSubmit"> 发送 </el-button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'InputArea',
  data() {
    return {
      inputText: '',
      placeholder: '请输入内容...',
    }
  },
  methods: {
    handleInput(value) {
      this.$emit('input', value)
    },
    handleSubmit() {
      if (this.inputText.trim()) {
        this.$emit('submit', this.inputText)
        this.inputText = ''
      }
    },
  },
}
</script>

<style scoped>
.input-area {
  width: 100%;
  border-radius: 4px;
  background: #fff;
  padding: 10px;
}

.input-footer {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-top: 10px;
}

.word-count {
  color: #999;
  font-size: 12px;
}
</style>
