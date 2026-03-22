# 旗舰版_13 Amaze-V12-Blue-Eyecare-V1_代码归档

## [Aesthetics] 特性区 (Flagship Features)
- **Deep Sea Inverse Matrix (深海逆序矩阵)**：基于 V3 护眼绿的 OKLCH 偏移算法，实现了 Hue 220 的深海蓝演化，具备极强的视觉镇静效果。
- **1:1 Dimensional Restoration (1:1 维度还原)**：严格锁定文件夹字号 (1.128rem) 与正文字号 (1.3294rem)，确保了从绿色版切换至蓝色版时，排版密度无任何波动。
- **Ocean-Tone Typography (海系文字色彩)**：内容文字色彩由青瓷绿版调整为靛青 (#1A2B3C)，显著提升了在蓝色背景下的阅读锐度。
- **Flagship 6px Scrollbar (蓝色旗舰版滚动条)**：宽度定格于 6px，滑块颜色采用 Ocean Blue (#2980B9)，整体视觉统一性极高。

## [Integrity] 代码块 (Golden Snippets)

### ✅ 1 hzmelisa66-Blue-Eyecare-V1.css
```css
@charset "UTF-8";

/* =================================================================== */
/* 【Obsidian 旗舰版 - Amaze-V12-Blue-Eyecare-V4】1:1 克隆·深海蓝版     */
/* 1. 字体：文件夹 1.128rem | 正文 1.3294rem (基于 V3.5 1:1 还原)      */
/* 2. 架构：1:1 物理死锁 & 6px 蓝色滚动条                               */
/* 3. 配色：OKLCH 深海护眼蓝 Deep Sea Blue (220)                       */
/* =================================================================== */

:root {
    /* 核心色彩：深海护眼蓝 (OKLCH) */
    --amaze-h: 220;
    --amaze-c-base: 0.06;
    
    /* 4px 步进系统 (严格锁定 V12) */
    --grid-unit: 4px;
    --nav-indent-tight: 8px; 
    --nav-radius: 6px;

    /* 1:1 物理比例还原 */
    --font-folder: 1.128rem; 
    --font-file: 0.987rem;   
    --font-content: 1.3294rem; 
}

/* --- [1. 基础背景与 UI 锁死] --- */
.theme-light, .theme-dark {
    --background-primary: oklch(94% 0.04 var(--amaze-h)) !important;
    --background-secondary: oklch(90% 0.05 var(--amaze-h)) !important;
    --workspace-background: var(--background-primary) !important;
    --text-normal: #1A2B3C !important;
    --text-accent: #3498DB !important;
    --divider-color: rgba(52, 152, 219, 0.3) !important;
}

:is(.nav-files-container, .workspace-split.mod-left-split, .workspace-tabs, .workspace-leaf, .view-content) {
    background-color: var(--background-primary) !important;
}

/* --- [2. 文件夹系统：L1-L5 动态逆序明度 (蓝色版)] --- */
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
    background-color: oklch(60% 0.12 var(--amaze-h) / 90%) !important;
    border-left-color: oklch(45% 0.15 var(--amaze-h)) !important;
}
.nav-files-container > div > .nav-folder > .nav-folder-title .nav-folder-title-content {
    color: #FFFFFF !important; 
}

/* L2-L5 逆序阶梯 */
.nav-folder .nav-folder > .nav-folder-title {
    background-color: oklch(75% 0.09 var(--amaze-h) / 75%) !important;
    border-left-color: oklch(60% 0.12 var(--amaze-h)) !important;
}
.nav-folder .nav-folder .nav-folder > .nav-folder-title {
    background-color: oklch(85% 0.06 var(--amaze-h) / 60%) !important;
    border-left-color: oklch(70% 0.09 var(--amaze-h)) !important;
}
.nav-folder .nav-folder .nav-folder .nav-folder > .nav-folder-title {
    background-color: oklch(92% 0.04 var(--amaze-h) / 45%) !important;
    border-left-color: oklch(80% 0.06 var(--amaze-h)) !important;
}
.nav-folder .nav-folder .nav-folder .nav-folder .nav-folder > .nav-folder-title {
    background-color: oklch(98% 0.02 var(--amaze-h) / 30%) !important;
    border-left-color: oklch(90% 0.04 var(--amaze-h)) !important;
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

/* --- [3. 正文系统：1.3294rem (蓝色版)] --- */
.markdown-source-view.mod-cm6 .cm-content, 
.markdown-source-view.mod-cm6 .cm-line, 
.markdown-rendered, 
.view-header-title {
    color: #1A2B3C !important;
    font-size: var(--font-content) !important; 
    font-weight: 600 !important;
    line-height: 1.8 !important;
}

/* --- [4. 交互反馈与滚动条] --- */
.nav-file-title.is-active, 
.nav-folder-title.is-active {
    background-color: #3498DB !important; 
    border-left: 10px solid #1A2B3C !important;
    box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1) !important;
}

::-webkit-scrollbar { width: 6px !important; }
::-webkit-scrollbar-thumb { background-color: #2980B9 !important; border-radius: 10px !important; }
```

## [Sanitize] 零污染声明 (Purity Declaration)
- [x] 源码中已彻底清除所有本地物理路径。
- [x] 编码格式：UTF-8 无 BOM。
- [x] 排版：遵循 4px 极致对齐空间标准。
- [x] 审计：Ordinal 13 核心资产物理对齐。

---
*归档日期：2026-03-22*
*归档状态：已完成 (Ordinal 13)*
