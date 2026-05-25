# AGENTS.md

本仓库只保留**轻量维护约定**，不再使用仓库内的 OpenSpec、skills、命令编排或其他 AI 治理框架。

## 项目定位

- 项目：`gpu-fft`
- 技术栈：TypeScript、WebGPU、WGSL、Vite、Vitest
- 当前目标：删除冗余、修复漂移、保持低维护成本

## 真源

- 实现：`src/`
- 对外说明：`README.md` 与 `docs/`
- 变更历史：根目录 `CHANGELOG.md`（唯一 changelog）
- WGSL shader 真源：`src/shaders/sources.ts`

## 维护原则

- 优先删除冗余和死代码，而不是继续扩张功能面
- `createSpectrumAnalyzer()` 与 `createImageFilter()` 为 **CPU-only utility**
- 不新增仓库内 AI workflow、skills、agent 命令目录
- 对外文档保持简洁、可验证，不写夸张叙事

## 验证

```bash
npm run lint && npm run format:check && npm run typecheck && npm test
```

包、发布或文档相关改动额外执行：

```bash
npm run build
npm run smoke:package
npm run docs:build
```
