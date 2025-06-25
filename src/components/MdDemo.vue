<template>
  <div class="markdown-body">
    <div v-html="md"></div>
  </div>
</template>

<script>
import { createRequire } from 'module';
const require = createRequire(import.meta.url);

import markdownIt from 'markdown-it'

// 引入 Markdown 文件（需要 webpack loader 支持）
const mdContent = require('./test.md')

// 创建 markdown-it 实例
const md = markdownIt()

export default {
  name: 'MarkdownRenderer',
  computed: {
    md() {
      return md.render(mdContent)
    }
  }
}
</script>
