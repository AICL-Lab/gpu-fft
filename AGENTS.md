# AGENTS.md

本文件是本仓库面向所有 AI coding agent 的**项目级真源说明**。

## 1. 项目定位

- 项目：`gpu-fft`
- 技术栈：TypeScript、WebGPU、WGSL、Vite、Vitest
- 当前阶段：**收尾 / 规范化 / 低维护准备阶段**
- 工作目标：优先修复治理漂移、文档冗余、工程配置失配、规范不一致；**不主动扩张产品范围**

## 2. 质量门禁

### Canonical validation chain

```bash
npm run lint && npm run format:check && npm run typecheck && npm test
```

### 补充检查（打包/发布相关）

```bash
npm run build && npm run smoke:package
```

### 原则

- 保留最少但有效的自动化
- 发现陈旧或失配配置时，优先删除或收敛，而不是继续叠加

## 3. 项目关键事实

- `src/shaders/sources.ts` 是 WGSL shader 的唯一真源；不再维护独立 `.wgsl` 参考副本
- `createSpectrumAnalyzer()` 和 `createImageFilter()` 是 **CPU-only**
- `npm run build` 会先清空 `dist/`，避免陈旧包产物残留
- `enableBankConflictOptimization` 已接入 shader padding，默认关闭；是否启用应基于目标硬件 profile
- `workgroupSize` 目前固定为 256

## 4. 变更同步要求

以下变更必须同步更新相关表面：

- 公开 API 变化：实现 + README/docs
- 工作流变化：`AGENTS.md` + `CLAUDE.md` + Copilot 指令 + 相关工程文件
- 文档定位变化：README + docs 首页 + GitHub About / homepage

## 5. 预期行为

理想 agent 行为：

- 先读规范，再改代码
- 先消歧义，再加复杂度
- 先合并真源，再删除旧入口
- 先保证表述准确，再追求"看起来完整"
