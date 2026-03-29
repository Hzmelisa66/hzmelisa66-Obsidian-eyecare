
# 旗舰版_12 Green-eyecare-AmazeH-V2_代码归档

## [Aesthetics] 特性区 (Flagship Features)
- **Celadon Standard Reset (青瓷标准重置版)**：基于 V12 旗舰架构进行 1:1 物理还原，完美继承了 Hue 192 的护眼青瓷绿底座。
- **Precision Reading Scaling (精准阅读缩放)**：正文内容字号在 V3.4 基础上执行了 -8% 的微调，定格于 1.3294rem，提供了最适合长时间深度阅读的视觉比例。
- **Balanced Side-bar Matrix (平衡侧边栏矩阵)**：文件夹文字较 V12 标准缩小 6%，确保了在开启 6px 增强滚动条时，左侧文件树依然具备极佳的呼吸感与排版空间。
- **Standard V12 Double-Star Engine (双星引擎)**：完整保留了 L1 (60%) 至 L5 (98%) 的逆序明度演化逻辑，确保核心导航区的层次感与功能区分。

## [Integrity] 代码块 (Golden Snippets)

### ✅ 2 hzmelisa66-Green-eyecare-V2.css
```css
@charset "UTF-8";

/* =================================================================== */
/* 【Obsidian 旗舰版 - Green-eyecare-AmazeH-V3】重置比例 + 1:1 结构版  */
/* 1. 字体：文件夹 1.128rem (-6%) | 正文 1.3294rem (-8% from V3.4)     */
/* 2. 架构：1:1 物理重置 & 6px 滚动条 (+50%)                            */
/* 3. 配色：OKLCH 护眼青瓷绿 Celadon (192)                              */
/* =================================================================== */

:root {
    /* 核心色彩：护眼青瓷绿 (OKLCH) */
    --celadon-h: 192;
    --celadon-c-base: 0.06;
    
    /* 4px 步进系统 (严格锁定 V12) */
    --grid-unit: 4px;
    --nav-indent-tight: 8px; 
    --nav-radius: 6px;

    /* 初始比例修正 */
    --font-folder: 1.128rem; /* 1.2rem - 6% */
    --font-file: 0.987rem;   /* 1.05rem - 6% */
    --font-content: 1.3294rem; /* 1.445rem * 0.92 */
}

/* --- [1. 基础背景与 UI 锁死] --- */
.theme-light, .theme-dark {
    --background-primary: oklch(94% 0.04 var(--celadon-h)) !important;
    --background-secondary: oklch(90% 0.05 var(--celadon-h)) !important;
    --workspace-background: var(--background-primary) !important;
    --text-normal: #2F4F4F !important;
    --text-accent: #F4A460 !important;
    --divider-color: rgba(95, 158, 160, 0.3) !important;
}

:is(.nav-files-container, .workspace-split.mod-left-split, .workspace-tabs, .workspace-leaf, .view-content) {
    background-color: var(--background-primary) !important;
}

/* --- [2. 文件夹系统：L1-L5 动态逆序明度] --- */
.nav-folder-title {
    margin: 2px 4px 2px 0 !important;
    padding: 6px 10px !important;
    border-radius: var(--nav-radius) !important;
    border: 1px solid rgba(0, 0, 0, 0.03) !important;
    border-left: 6px solid transparent !important;
    transition: background-color 0.2s ease, border-color 0.2s ease !important;
}

/* L1: 顶层 (最深: 60% 明度) */
.nav-files-container > div > .nav-folder > .nav-folder-title {
    background-color: oklch(60% 0.12 var(--celadon-h) / 90%) !important;
    border-left-color: oklch(45% 0.15 var(--celadon-h)) !important;
}
.nav-files-container > div > .nav-folder > .nav-folder-title .nav-folder-title-content {
    color: #FFFFFF !important; 
}

/* L2-L5 逆序阶梯 */
.nav-folder .nav-folder > .nav-folder-title {
    background-color: oklch(75% 0.09 var(--celadon-h) / 75%) !important;
    border-left-color: oklch(60% 0.12 var(--celadon-h)) !important;
}
.nav-folder .nav-folder .nav-folder > .nav-folder-title {
    background-color: oklch(85% 0.06 var(--celadon-h) / 60%) !important;
    border-left-color: oklch(70% 0.09 var(--celadon-h)) !important;
}
.nav-folder .nav-folder .nav-folder .nav-folder > .nav-folder-title {
    background-color: oklch(92% 0.04 var(--celadon-h) / 45%) !important;
    border-left-color: oklch(80% 0.06 var(--celadon-h)) !important;
}
.nav-folder .nav-folder .nav-folder .nav-folder .nav-folder > .nav-folder-title {
    background-color: oklch(98% 0.02 var(--celadon-h) / 30%) !important;
    border-left-color: oklch(90% 0.04 var(--celadon-h)) !important;
}

/* 文本渲染 */
.nav-folder-title-content {
    font-size: var(--font-folder) !important;
    font-weight: 700 !important;
    color: var(--text-normal);
}
.nav-file-title-content {
    font-size: var(--font-file) !important;
    font-weight: 600 !important;
    color: var(--text-normal) !important;
}

/* 布局修正：极致空间利用 */
.tree-item-children {
    padding-left: var(--nav-indent-tight) !important; 
    border-left: 1px solid rgba(0, 0, 0, 0.05) !important;
    margin-left: 2px !important;
}

/* --- [3. 正文系统：1.3294rem (精简后的比例)] --- */
.markdown-source-view.mod-cm6 .cm-content, 
.markdown-source-view.mod-cm6 .cm-line, 
.markdown-rendered, 
.view-header-title {
    color: #2F4F4F !important;
    font-size: var(--font-content) !important; 
    font-weight: 600 !important;
    line-height: 1.8 !important;
}

/* --- [4. 交互反馈与滚动条] --- */
.nav-file-title.is-active, 
.nav-folder-title.is-active {
    background-color: #40E0D0 !important; 
    border-left: 10px solid #191970 !important;
    box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1) !important;
}

::-webkit-scrollbar { width: 6px !important; }
::-webkit-scrollbar-thumb { background-color: #5F9EA0 !important; border-radius: 10px !important; }
```

## [Sanitize] 零污染声明 (Purity Declaration)
- [x] 源码中已彻底清除所有本地物理路径。
- [x] 编码格式：UTF-8 无 BOM。
- [x] 排版：遵循 4px 极致对齐空间标准。
- [x] 审计：Ordinal 12 核心资产物理对齐。

---
*归档日期：2026-03-22*
*归档状态：已完成 (Ordinal 12)*
