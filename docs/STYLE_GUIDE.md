# TNI Toolkit Style Guide

Complete styling reference for building TNI Toolkit tools. All tools use a **Network Operations Center (NOC)** aesthetic — dark theme, monospace typography, terminal-style green/blue accents.

---

## Table of Contents

1. [Design Tokens](#design-tokens)
2. [Base Template](#base-template)
3. [Master CSS](#master-css)
4. [Layout Components](#layout-components)
5. [UI Components](#ui-components)
6. [Patterns & Examples](#patterns--examples)
7. [Responsive Design](#responsive-design)
8. [Best Practices](#best-practices)
9. [File Format Standards](#file-format-standards)

---

## Design Tokens

### Colors

```css
/* Background */
--bg-gradient: linear-gradient(135deg, #0a0e14 0%, #1a1f2e 50%, #0d1117 100%);
--surface: rgba(22, 27, 34, 0.8);
--surface-dark: rgba(22, 27, 34, 0.6);

/* Borders */
--border: #30363d;
--border-light: rgba(48, 54, 61, 0.5);

/* Text */
--text-primary: #c9d1d9;
--text-secondary: #8b949e;
--text-muted: #7d8590;

/* Accent Colors */
--accent-green: #00ff88;          /* Primary action, success, selected */
--accent-green-dim: #238636;      /* Success backgrounds */
--accent-blue: #58a6ff;           /* Info, links, hover states */
--accent-orange: #f0883e;         /* Warnings, costs, attention */
--accent-red: #f85149;            /* Errors, destructive actions */

/* Transparent Variants (for backgrounds) */
--accent-green-bg: rgba(0, 255, 136, 0.08);
--accent-green-bg-hover: rgba(0, 255, 136, 0.15);
--accent-green-bg-strong: rgba(0, 255, 136, 0.1);
--accent-blue-bg: rgba(88, 166, 255, 0.08);
--accent-blue-bg-hover: rgba(88, 166, 255, 0.1);
--accent-orange-bg: rgba(240, 136, 62, 0.08);
--accent-red-bg: rgba(248, 81, 73, 0.15);
--accent-red-bg-hover: rgba(248, 81, 73, 0.25);
```

### Typography

```css
/* Font Stack */
font-family: "JetBrains Mono", "Fira Code", "SF Mono", Consolas, monospace;

/* Scale */
--text-xs: 10px;    /* Fine print, metadata */
--text-sm: 11px;    /* Small labels, stats */
--text-base: 12px;  /* Body text */
--text-md: 13px;    /* Panel headers */
--text-lg: 14px;    /* Card titles */
--text-xl: 20px;    /* Page title */
--text-2xl: 28px;   /* Hero/logo */

/* Weights */
--font-normal: 400;
--font-medium: 500;
--font-semibold: 600;
--font-bold: 700;
```

### Spacing

```css
--space-1: 4px;
--space-2: 8px;
--space-3: 10px;
--space-4: 12px;
--space-5: 15px;
--space-6: 16px;
--space-7: 20px;
--space-8: 24px;
--space-9: 30px;
--space-10: 40px;
```

### Borders & Radius

```css
--radius-sm: 4px;
--radius-md: 6px;
--radius-lg: 8px;

--border-width: 1px;
--border-style: solid;
```

### Shadows & Effects

```css
/* Glow effect for primary elements */
--glow-green: 0 0 20px rgba(0, 255, 136, 0.3);
--glow-green-strong: 0 0 30px rgba(0, 255, 136, 0.4);

/* Card hover shadow */
--shadow-hover: 0 0 20px rgba(0, 255, 136, 0.1);
```

### Transitions

```css
--transition-fast: 0.15s ease;
--transition-base: 0.2s ease;
```

---

## Base Template

Start every new tool with this template:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>TNI [Tool Name]</title>
    <style>
        * { box-sizing: border-box; margin: 0; padding: 0; }
        
        body {
            font-family: "JetBrains Mono", "Fira Code", "SF Mono", Consolas, monospace;
            background: linear-gradient(135deg, #0a0e14 0%, #1a1f2e 50%, #0d1117 100%);
            color: #c9d1d9;
            min-height: 100vh;
            padding: 24px;
            line-height: 1.6;
        }
        
        .container {
            max-width: 1200px;
            margin: 0 auto;
        }
        
        /* === HEADER === */
        .header {
            text-align: center;
            border-bottom: 1px solid #30363d;
            padding-bottom: 16px;
            margin-bottom: 24px;
        }
        
        h1 {
            color: #00ff88;
            text-shadow: 0 0 20px rgba(0, 255, 136, 0.3);
            margin: 0 0 8px 0;
            font-size: 20px;
            font-weight: 600;
            letter-spacing: 2px;
            text-transform: uppercase;
        }
        
        h1 span { color: #58a6ff; }
        
        .subtitle { color: #8b949e; font-size: 12px; }
        .stats { color: #7d8590; font-size: 11px; margin-top: 8px; }
        
        /* === PANELS === */
        .panel {
            background: rgba(22, 27, 34, 0.8);
            border: 1px solid #30363d;
            border-radius: 6px;
            padding: 20px;
            margin-bottom: 20px;
        }
        
        .panel h2 {
            margin: 0 0 12px 0;
            padding-bottom: 12px;
            border-bottom: 1px solid #30363d;
            color: #58a6ff;
            font-size: 13px;
            font-weight: 600;
            text-transform: uppercase;
            letter-spacing: 1px;
        }
        
        /* === FOOTER === */
        .site-footer {
            margin-top: 40px;
            padding-top: 16px;
            border-top: 1px solid #30363d;
            text-align: center;
            font-size: 11px;
            color: #7d8590;
        }
        
        .site-footer a {
            color: #8b949e;
            text-decoration: none;
            transition: color 0.15s;
        }
        
        .site-footer a:hover { color: #58a6ff; }
        .site-footer .sep { margin: 0 8px; color: #30363d; }
        
        /* === RESPONSIVE === */
        @media (max-width: 600px) {
            body { padding: 16px; }
        }
    </style>
</head>
<body>
    <div class="container">
        <header class="header">
            <h1>TNI <span>[TOOL NAME]</span></h1>
            <p class="subtitle">Brief description of what the tool does</p>
        </header>
        
        <div class="panel">
            <h2>📋 Section Title</h2>
            <!-- Content here -->
        </div>
        
        <footer class="site-footer">
            <a href="https://github.com/salvo-praxis/tni-toolkit" target="_blank">TNI Toolkit</a>
            <span class="sep">|</span>
            <a href="https://store.steampowered.com/app/2939600/Tower_Networking_Inc/" target="_blank">Tower Networking Inc. on Steam</a>
        </footer>
    </div>
    
    <script>
        // Tool logic here
    </script>
</body>
</html>
```

---

## Master CSS

Complete, production-ready CSS for all TNI Toolkit components. Copy the entire stylesheet to use in new tools.

```css
/* ================================================================== */
/* TNI TOOLKIT - MASTER STYLESHEET                                    */
/* Version: 1.0.0                                                     */
/* Updated: 2025-12                                                   */
/* ================================================================== */

/* === RESET & BASE === */
* { box-sizing: border-box; margin: 0; padding: 0; }

body {
    font-family: "JetBrains Mono", "Fira Code", "SF Mono", Consolas, monospace;
    background: linear-gradient(135deg, #0a0e14 0%, #1a1f2e 50%, #0d1117 100%);
    color: #c9d1d9;
    min-height: 100vh;
    padding: 24px;
    line-height: 1.6;
}

/* === LAYOUT === */
.container {
    max-width: 1200px;
    margin: 0 auto;
}

.grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(180px, 1fr));
    gap: 12px;
}

.flex-row {
    display: flex;
    gap: 12px;
    flex-wrap: wrap;
}

/* === HEADER === */
.header {
    text-align: center;
    border-bottom: 1px solid #30363d;
    padding-bottom: 16px;
    margin-bottom: 24px;
}

h1 {
    color: #00ff88;
    text-shadow: 0 0 20px rgba(0, 255, 136, 0.3);
    margin: 0 0 8px 0;
    font-size: 20px;
    font-weight: 600;
    letter-spacing: 2px;
    text-transform: uppercase;
}

h1 span { color: #58a6ff; }

.subtitle {
    color: #8b949e;
    font-size: 12px;
    margin: 0;
}

/* === PANELS === */
.panel {
    background: rgba(22, 27, 34, 0.8);
    border: 1px solid #30363d;
    border-radius: 6px;
    padding: 20px;
    margin-bottom: 16px;
}

.panel h2 {
    margin: 0;
    padding-bottom: 12px;
    border-bottom: 1px solid #30363d;
    color: #58a6ff;
    font-size: 13px;
    font-weight: 600;
    text-transform: uppercase;
    letter-spacing: 1px;
    line-height: 1.3;
}

.panel h2 + * { margin-top: 12px; }
.panel > *:last-child { margin-bottom: 0; }

/* === CARDS === */
.card {
    background: rgba(22, 27, 34, 0.8);
    border: 1px solid #30363d;
    border-radius: 6px;
    padding: 12px;
    cursor: pointer;
    transition: all 0.15s;
}

.card:hover {
    border-color: #58a6ff;
    background: rgba(88, 166, 255, 0.08);
}

.card.selected {
    border-color: #00ff88;
    background: rgba(0, 255, 136, 0.1);
}

.card.disabled {
    opacity: 0.4;
    cursor: not-allowed;
    pointer-events: none;
}

.card-name {
    color: #c9d1d9;
    font-size: 12px;
    font-weight: 500;
}

.card-meta {
    color: #7d8590;
    font-size: 10px;
    margin-top: 4px;
}

/* === BUTTONS === */
.btn {
    display: inline-flex;
    align-items: center;
    gap: 6px;
    padding: 8px 14px;
    border-radius: 4px;
    font-size: 11px;
    font-family: inherit;
    font-weight: 500;
    cursor: pointer;
    transition: all 0.15s;
    text-decoration: none;
}

.btn-primary {
    background: rgba(0, 255, 136, 0.15);
    border: 1px solid #00ff88;
    color: #00ff88;
}

.btn-primary:hover {
    background: rgba(0, 255, 136, 0.25);
}

.btn-secondary {
    background: rgba(88, 166, 255, 0.1);
    border: 1px solid #30363d;
    color: #8b949e;
}

.btn-secondary:hover {
    border-color: #58a6ff;
    color: #58a6ff;
}

.btn-danger {
    background: rgba(248, 81, 73, 0.15);
    border: 1px solid #f85149;
    color: #f85149;
}

.btn-danger:hover {
    background: rgba(248, 81, 73, 0.25);
}

/* === FORM INPUTS === */
input[type="text"],
input[type="search"],
input[type="number"] {
    width: 100%;
    padding: 10px 12px;
    border-radius: 6px;
    border: 1px solid #30363d;
    background: rgba(22, 27, 34, 0.8);
    color: #c9d1d9;
    font-size: 12px;
    font-family: inherit;
    transition: border-color 0.15s;
}

input:focus {
    outline: none;
    border-color: #58a6ff;
}

input::placeholder {
    color: #8b949e;
}

/* === CUSTOM DROPDOWN === */
.dropdown {
    position: relative;
}

.dropdown-selected {
    padding: 10px 12px;
    padding-right: 32px;
    border-radius: 6px;
    border: 1px solid #30363d;
    background: rgba(22, 27, 34, 0.8);
    color: #c9d1d9;
    font-size: 12px;
    cursor: pointer;
    transition: all 0.15s;
    position: relative;
}

.dropdown-selected::after {
    content: "▼";
    position: absolute;
    right: 12px;
    top: 50%;
    transform: translateY(-50%);
    font-size: 8px;
    color: #8b949e;
    transition: transform 0.15s;
}

.dropdown-selected:hover {
    border-color: #58a6ff;
}

.dropdown.open .dropdown-selected {
    border-color: #58a6ff;
    border-bottom-left-radius: 0;
    border-bottom-right-radius: 0;
}

.dropdown.open .dropdown-selected::after {
    transform: translateY(-50%) rotate(180deg);
}

.dropdown-options {
    position: absolute;
    top: 100%;
    left: 0;
    right: 0;
    background: rgba(22, 27, 34, 0.95);
    border: 1px solid #58a6ff;
    border-top: none;
    border-bottom-left-radius: 6px;
    border-bottom-right-radius: 6px;
    max-height: 200px;
    overflow-y: auto;
    z-index: 100;
    display: none;
}

.dropdown.open .dropdown-options {
    display: block;
}

.dropdown-option {
    padding: 10px 12px;
    font-size: 12px;
    color: #8b949e;
    cursor: pointer;
    transition: all 0.1s;
}

.dropdown-option:hover {
    background: rgba(88, 166, 255, 0.15);
    color: #c9d1d9;
}

.dropdown-option.selected {
    background: rgba(0, 255, 136, 0.15);
    color: #00ff88;
}

/* === TABLES === */
.table {
    width: 100%;
    border-collapse: collapse;
    font-size: 12px;
    line-height: 1.3;
}

.table th {
    text-align: left;
    color: #58a6ff;
    font-weight: 600;
    padding: 0 12px 10px 12px;
    border-bottom: 1px solid #30363d;
    font-size: 11px;
    text-transform: uppercase;
}

.table td {
    padding: 10px 12px;
    border-bottom: 1px solid rgba(48, 54, 61, 0.5);
    color: #8b949e;
}

.table tr:last-child td {
    border-bottom: none;
    padding-bottom: 0;
}

.table tr:hover td {
    background: rgba(88, 166, 255, 0.05);
}

/* === TAGS === */
.tag {
    background: rgba(0, 255, 136, 0.15);
    border: 1px solid #00ff88;
    color: #00ff88;
    padding: 6px 12px;
    border-radius: 4px;
    font-weight: 500;
    font-size: 11px;
    display: inline-flex;
    align-items: center;
    gap: 8px;
}

.tag .remove {
    cursor: pointer;
    opacity: 0.7;
}

.tag .remove:hover {
    opacity: 1;
}

/* === CALLOUTS === */
.callout {
    background: rgba(240, 136, 62, 0.08);
    border: 1px solid #f0883e;
    border-radius: 6px;
    padding: 16px;
}

.callout-header {
    color: #f0883e;
    font-size: 12px;
    font-weight: 600;
    margin-bottom: 8px;
}

.callout-success {
    background: rgba(0, 255, 136, 0.08);
    border-color: #00ff88;
}

.callout-success .callout-header {
    color: #00ff88;
}

.callout-error {
    background: rgba(248, 81, 73, 0.08);
    border-color: #f85149;
}

.callout-error .callout-header {
    color: #f85149;
}

/* === PROGRESS / STAT BARS === */
.stat-bar {
    display: flex;
    align-items: center;
    gap: 10px;
}

.stat-label {
    font-size: 11px;
    color: #8b949e;
    min-width: 50px;
}

.stat-track {
    flex: 1;
    height: 8px;
    background: rgba(22, 27, 34, 0.8);
    border-radius: 4px;
    overflow: hidden;
}

.stat-fill {
    height: 100%;
    background: #00ff88;
    border-radius: 4px;
    transition: width 0.3s ease;
}

.stat-fill.warning { background: #f0883e; }
.stat-fill.danger { background: #f85149; }

.stat-value {
    font-size: 11px;
    color: #c9d1d9;
    min-width: 40px;
    text-align: right;
}

/* === TOOLTIP === */
.tooltip {
    position: fixed;
    background: #238636;
    color: #fff;
    padding: 6px 12px;
    border-radius: 4px;
    font-weight: 500;
    font-size: 11px;
    pointer-events: none;
    opacity: 0;
    transition: opacity 0.15s;
    z-index: 1000;
}

.tooltip.show { opacity: 1; }

/* === EMPTY STATE === */
.empty-state {
    text-align: center;
    color: #8b949e;
    padding: 40px;
    font-size: 12px;
}

.empty-state small {
    display: block;
    margin-top: 8px;
    color: #7d8590;
}

/* === CODE DISPLAY === */
code {
    background: rgba(0, 0, 0, 0.3);
    padding: 2px 6px;
    border-radius: 3px;
    font-size: 11px;
    color: #00ff88;
}

.code-value {
    font-size: 1.4em;
    font-weight: 600;
    color: #00ff88;
    text-align: center;
    padding: 10px 20px;
    background: rgba(0, 255, 136, 0.08);
    border: 1px solid #238636;
    border-radius: 4px;
    letter-spacing: 4px;
    cursor: pointer;
}

.code-value:hover {
    background: rgba(0, 255, 136, 0.15);
}

/* === CUSTOM SCROLLBAR === */
::-webkit-scrollbar {
    width: 8px;
    height: 8px;
}

::-webkit-scrollbar-track {
    background: rgba(22, 27, 34, 0.5);
    border-radius: 4px;
}

::-webkit-scrollbar-thumb {
    background: #30363d;
    border-radius: 4px;
}

::-webkit-scrollbar-thumb:hover {
    background: #58a6ff;
}

/* === FOOTER === */
.site-footer {
    margin-top: 40px;
    padding-top: 16px;
    border-top: 1px solid #30363d;
    text-align: center;
    font-size: 11px;
    color: #7d8590;
}

.site-footer a {
    color: #8b949e;
    text-decoration: none;
    transition: color 0.15s;
}

.site-footer a:hover { color: #58a6ff; }
.site-footer .sep { margin: 0 8px; color: #30363d; }

/* === RESPONSIVE === */
@media (max-width: 600px) {
    body { padding: 16px; }
    .container { max-width: 100%; }
    .grid { grid-template-columns: 1fr; }
    h1 { font-size: 18px; }
}
```

---

## Layout Components

### Container

```css
.container {
    max-width: 1200px;  /* Or 1100px for narrower layouts */
    margin: 0 auto;
    padding: 24px;
}
```

### Grid Layouts

```css
/* Auto-fill responsive grid */
.grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
    gap: 10px;
}

/* Larger cards */
.grid-lg {
    grid-template-columns: repeat(auto-fill, minmax(320px, 1fr));
    gap: 15px;
}

/* Two-column info layout */
.grid-2 {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 20px;
}
```

### Flex Layouts

```css
/* Horizontal group with wrap */
.flex-row {
    display: flex;
    align-items: center;
    gap: 15px;
    flex-wrap: wrap;
}

/* Space between header */
.flex-between {
    display: flex;
    justify-content: space-between;
    align-items: center;
}

/* Vertical stack */
.flex-col {
    display: flex;
    flex-direction: column;
    gap: 8px;
}
```

---

## UI Components

### Panel (Container Card)

```css
.panel {
    background: rgba(22, 27, 34, 0.8);
    border: 1px solid #30363d;
    border-radius: 6px;
    padding: 20px;
    margin-bottom: 20px;
}

.panel h2 {
    margin: 0 0 12px 0;
    padding-bottom: 12px;
    border-bottom: 1px solid #30363d;
    color: #58a6ff;
    font-size: 13px;
    font-weight: 600;
    text-transform: uppercase;
    letter-spacing: 1px;
}
```

### Interactive Card

```css
.card {
    background: rgba(22, 27, 34, 0.8);
    border: 1px solid #30363d;
    border-radius: 6px;
    padding: 12px;
    cursor: pointer;
    transition: all 0.15s;
}

.card:hover {
    border-color: #58a6ff;
    background: rgba(88, 166, 255, 0.08);
}

.card.selected {
    border-color: #00ff88;
    background: rgba(0, 255, 136, 0.1);
}

.card.disabled {
    opacity: 0.4;
    cursor: not-allowed;
}
```

### Buttons

```css
/* Primary Button (Green) */
.btn-primary {
    display: inline-flex;
    align-items: center;
    gap: 6px;
    padding: 8px 14px;
    border-radius: 4px;
    font-size: 11px;
    font-family: inherit;
    font-weight: 500;
    text-decoration: none;
    cursor: pointer;
    transition: all 0.15s;
    background: rgba(0, 255, 136, 0.15);
    border: 1px solid #00ff88;
    color: #00ff88;
}

.btn-primary:hover {
    background: rgba(0, 255, 136, 0.25);
}

/* Secondary Button (Subtle) */
.btn-secondary {
    background: rgba(88, 166, 255, 0.1);
    border: 1px solid #30363d;
    color: #8b949e;
}

.btn-secondary:hover {
    border-color: #58a6ff;
    color: #58a6ff;
}

/* Danger Button (Red) */
.btn-danger {
    background: rgba(248, 81, 73, 0.15);
    border: 1px solid #f85149;
    color: #f85149;
}

.btn-danger:hover {
    background: rgba(248, 81, 73, 0.25);
}
```

### Tags / Badges

```css
/* Selected/Active Tag */
.tag {
    background: rgba(0, 255, 136, 0.15);
    border: 1px solid #00ff88;
    color: #00ff88;
    padding: 6px 12px;
    border-radius: 4px;
    font-weight: 500;
    font-size: 11px;
    display: inline-flex;
    align-items: center;
    gap: 8px;
}

/* Removable Tag */
.tag .remove {
    cursor: pointer;
    opacity: 0.7;
}

.tag .remove:hover {
    opacity: 1;
}
```

### Form Inputs

```css
/* Text Input */
input[type="text"],
input[type="search"],
input[type="number"] {
    width: 100%;
    padding: 10px 12px;
    border-radius: 6px;
    border: 1px solid #30363d;
    background: rgba(22, 27, 34, 0.8);
    color: #c9d1d9;
    font-size: 12px;
    font-family: inherit;
    transition: border-color 0.15s;
}

input:focus {
    outline: none;
    border-color: #58a6ff;
}

input::placeholder {
    color: #8b949e;
}

/* Select Dropdown */
select {
    padding: 10px 12px;
    border-radius: 6px;
    border: 1px solid #30363d;
    background: rgba(22, 27, 34, 0.8);
    color: #c9d1d9;
    font-size: 12px;
    font-family: inherit;
    cursor: pointer;
}

select:focus {
    outline: none;
    border-color: #58a6ff;
}

/* Checkbox (styled as card) */
.checkbox-card {
    display: flex;
    align-items: center;
    gap: 10px;
    padding: 10px 12px;
    background: rgba(22, 27, 34, 0.6);
    border: 1px solid #30363d;
    border-radius: 4px;
    cursor: pointer;
    transition: all 0.15s;
}

.checkbox-card:hover {
    border-color: #58a6ff;
}

.checkbox-card.checked {
    border-color: #00ff88;
    background: rgba(0, 255, 136, 0.08);
}
```

### Custom Dropdown

Native `<select>` elements don't style well on dark themes. Use this custom dropdown pattern instead:

```html
<div class="dropdown">
    <div class="dropdown-selected">Select server...</div>
    <div class="dropdown-options">
        <div class="dropdown-option">Server 01</div>
        <div class="dropdown-option selected">Server 02</div>
        <div class="dropdown-option">Server 03</div>
    </div>
</div>
```

```css
/* Custom Dropdown Container */
.dropdown {
    position: relative;
}

.dropdown-selected {
    padding: 10px 32px 10px 12px;
    border: 1px solid #30363d;
    border-radius: 6px;
    background: rgba(22, 27, 34, 0.8);
    color: #c9d1d9;
    cursor: pointer;
}

.dropdown-selected::after {
    content: "▼";
    position: absolute;
    right: 12px;
    color: #8b949e;
}

.dropdown-options {
    position: absolute;
    top: 100%;
    left: 0;
    right: 0;
    background: rgba(22, 27, 34, 0.95);
    border: 1px solid #58a6ff;
    border-top: none;
    max-height: 150px;
    overflow-y: auto;
    display: none;
}

.dropdown.open .dropdown-options {
    display: block;
}

.dropdown-option {
    padding: 10px 12px;
    cursor: pointer;
}

.dropdown-option:hover {
    background: rgba(88, 166, 255, 0.15);
}

.dropdown-option.selected {
    background: rgba(0, 255, 136, 0.15);
    color: #00ff88;
}
```

```javascript
// Toggle dropdown on click
document.querySelectorAll('.dropdown').forEach(dropdown => {
    dropdown.addEventListener('click', () => dropdown.classList.toggle('open'));
});

// Close when clicking outside
document.addEventListener('click', e => {
    if (!e.target.closest('.dropdown')) {
        document.querySelectorAll('.dropdown.open').forEach(d => d.classList.remove('open'));
    }
});
```

### Tables

```css
.table {
    width: 100%;
    border-collapse: collapse;
    font-size: 12px;
}

.table th {
    text-align: left;
    color: #58a6ff;
    font-weight: 600;
    padding: 10px 12px;
    border-bottom: 1px solid #30363d;
    font-size: 11px;
    text-transform: uppercase;
    letter-spacing: 0.5px;
}

.table td {
    padding: 12px;
    border-bottom: 1px solid rgba(48, 54, 61, 0.5);
    vertical-align: top;
}

.table tr:hover td {
    background: rgba(88, 166, 255, 0.05);
}

.table a {
    color: #00ff88;
    text-decoration: none;
}

.table a:hover {
    text-decoration: underline;
}
```

### Callout / Alert Box

```css
/* Warning/Info Callout */
.callout {
    background: rgba(240, 136, 62, 0.08);
    border: 1px solid #f0883e;
    border-radius: 6px;
    padding: 16px;
}

.callout-header {
    color: #f0883e;
    font-size: 12px;
    font-weight: 600;
    margin-bottom: 8px;
    display: flex;
    align-items: center;
    gap: 6px;
}

.callout p {
    color: #8b949e;
    font-size: 11px;
    margin-bottom: 8px;
}

/* Success Callout */
.callout-success {
    background: rgba(0, 255, 136, 0.08);
    border-color: #00ff88;
}

.callout-success .callout-header {
    color: #00ff88;
}

/* Error Callout */
.callout-error {
    background: rgba(248, 81, 73, 0.08);
    border-color: #f85149;
}

.callout-error .callout-header {
    color: #f85149;
}
```

### Tooltip

```css
.tooltip {
    position: fixed;
    background: #238636;
    color: #fff;
    padding: 6px 12px;
    border-radius: 4px;
    font-weight: 500;
    font-size: 11px;
    pointer-events: none;
    opacity: 0;
    transition: opacity 0.15s;
    z-index: 1000;
}

.tooltip.show {
    opacity: 1;
}
```

### Progress / Stats Bar

```css
.stat-bar {
    display: flex;
    align-items: center;
    gap: 10px;
    margin-bottom: 8px;
}

.stat-label {
    font-size: 11px;
    color: #8b949e;
    min-width: 80px;
}

.stat-track {
    flex: 1;
    height: 8px;
    background: rgba(22, 27, 34, 0.8);
    border-radius: 4px;
    overflow: hidden;
}

.stat-fill {
    height: 100%;
    background: #00ff88;
    border-radius: 4px;
    transition: width 0.3s ease;
}

.stat-fill.warning {
    background: #f0883e;
}

.stat-fill.danger {
    background: #f85149;
}

.stat-value {
    font-size: 11px;
    color: #c9d1d9;
    min-width: 50px;
    text-align: right;
}
```

### Empty State

```css
.empty-state {
    text-align: center;
    color: #8b949e;
    padding: 40px;
    font-size: 12px;
}

.empty-state small {
    display: block;
    margin-top: 8px;
    color: #7d8590;
}
```

### Copy Feedback

For copyable elements that show visual feedback when clicked:

```css
.copyable {
    cursor: pointer;
    transition: background 0.15s;
}

.copyable:hover {
    background: rgba(0, 255, 136, 0.15);
}

.copyable.copied {
    background: rgba(35, 134, 54, 0.3);
}
```

---

## Patterns & Examples

### Resource Meter (CPU/Memory/Storage)

```html
<div class="stat-bar">
    <span class="stat-label">CPU</span>
    <div class="stat-track">
        <div class="stat-fill" style="width: 75%"></div>
    </div>
    <span class="stat-value">12/16</span>
</div>
```

### Selectable Item Grid

```html
<div class="grid">
    <div class="card" onclick="toggle(this)">
        <div class="card-name">Item Name</div>
        <div class="card-desc">Description text</div>
        <div class="card-meta">💰 500</div>
    </div>
</div>
```

### Copyable Code/Value

```html
<div class="code-value" onclick="copy('VALUE', this)" title="Click to copy">
    VALUE
</div>
```

```css
.code-value {
    font-size: 1.4em;
    font-weight: 600;
    color: #00ff88;
    text-align: center;
    padding: 10px;
    background: rgba(0, 255, 136, 0.08);
    border: 1px solid #238636;
    border-radius: 4px;
    letter-spacing: 4px;
    cursor: pointer;
    transition: background 0.15s;
}

.code-value:hover {
    background: rgba(0, 255, 136, 0.15);
}
```

### Inline Code

For inline code references in text (filenames, commands, values):

```html
<code>tni-store.json</code>
<code>program install dns-lite on 123 using 456</code>
```

```css
code {
    background: rgba(0, 0, 0, 0.3);
    padding: 2px 6px;
    border-radius: 3px;
    font-size: 11px;
    color: #00ff88;
}
```

**Inline in sentences:**
```html
<p>Edit the <code>_meta.last_updated</code> field before submitting.</p>
<p>Run <code>ping 192.168.1.1</code> to test connectivity.</p>
```

### Filter/Search Box

```html
<div class="search-box">
    <input type="text" id="search" placeholder="Filter items...">
</div>
```

```css
.search-box {
    margin-bottom: 15px;
}
```

---

## Responsive Design

### Breakpoints

```css
/* Mobile: 600px and below */
@media (max-width: 600px) {
    body {
        padding: 16px;
    }
    
    .container {
        padding: 16px;
    }
    
    h1 {
        font-size: 18px;
    }
    
    .grid {
        grid-template-columns: 1fr;
    }
    
    .flex-row {
        flex-direction: column;
        align-items: stretch;
    }
}
```

### Container Max-Widths

- Default tools: `max-width: 1200px`
- Narrower/reading layouts: `max-width: 1100px`
- Compact tools: `max-width: 900px`

---

## Best Practices

### DO ✓

- Use the established color tokens
- Keep font sizes consistent with the scale
- Use `transition: all 0.15s` for hover effects
- Include the standard footer on all tools
- Test offline functionality
- Embed all data directly in the HTML
- Use semantic emoji in headers (📋 📊 🎯 etc.)

### DON'T ✗

- Import external CSS or JS files
- Use colors outside the palette
- Use fonts other than the monospace stack
- Create separate CSS/JS files
- Rely on network requests for data
- Use heavy animations or effects
- Forget the mobile breakpoint

### Accessibility

- Maintain sufficient color contrast (green on dark passes)
- Use `cursor: pointer` on clickable elements
- Include `title` attributes on interactive elements
- Keep font sizes readable (minimum 10px)

---

## Emoji Reference

Use these consistently in headers:

| Emoji | Usage |
|-------|-------|
| 📋 | Selection, configuration |
| 📊 | Data, statistics, results |
| 🎯 | Results, matches, targets |
| 🛠️ | Tools, settings |
| 🗺️ | Roadmap, planning |
| 💰 | Cost, currency |
| ⚡ | Power, energy |
| 📜 | Policy, rules |
| 🦄 | Unique/rare items |
| ✓ | Complete, done |
| ○ | Pending, incomplete |

---

## File Format Standards

All project files include standardized headers for version tracking, attribution, and changelog. This ensures consistency across all file types and makes contributions traceable.

### JSON Files

JSON data files include a `_meta` object as the first key:

```json
{
  "_meta": {
    "game": "Tower Networking Inc.",
    "dataset": "dataset-name",
    "version": "1.0.0",
    "last_updated": "YYYY-MM-DD",
    "description": "What this dataset contains",
    "sources": [...],
    "contributors": ["Name or Handle"],
    "corrections": [...],
    "future_additions": [...]
  }
}
```

See [CONTRIBUTING.md](../CONTRIBUTING.md) for full `_meta` structure with all fields.

### HTML Files

HTML tools include a comment header **before** `<!DOCTYPE html>`:

```html
<!--
╔══════════════════════════════════════════════════════════════════════════════╗
║  Tool Name                                                                   ║
╠══════════════════════════════════════════════════════════════════════════════╣
║  Version: X.Y.Z                                                              ║
║  Updated: YYYY-MM-DD                                                         ║
║  Part of: TNI Toolkit (https://github.com/salvo-praxis/tni-toolkit)          ║
╠══════════════════════════════════════════════════════════════════════════════╣
║  Description:                                                                ║
║    Brief description of what this tool does.                                 ║
║                                                                              ║
║  Features:                                                                   ║
║    - Feature 1                                                               ║
║    - Feature 2                                                               ║
║                                                                              ║
║  Contributors:                                                               ║
║    - Name (contribution type)                                                ║
║                                                                              ║
║  Changelog:                                                                  ║
║    X.Y.Z - Description of changes                                            ║
╚══════════════════════════════════════════════════════════════════════════════╝
-->
```

### YAML Files

YAML configuration files (GitHub Actions, CI/CD, etc.) use comment headers:

```yaml
# ============================================================================
# TNI Toolkit - [File Type/Purpose]
# File: [path/to/file.yml]
# Name: [Workflow or Config Name]
# Version: X.Y.Z
# Updated: YYYY-MM-DD
# Part of: TNI Toolkit (https://github.com/salvo-praxis/tni-toolkit)
# Description:
#   Brief description of what this file does.
#   Can span multiple lines if needed.
# Contributors:
#   - Name (@handle) - contribution type
#   - Claude - contribution type
# Changelog:
#   X.Y.Z - Description of changes
# ============================================================================
```

**YAML Header Fields:**

| Field | Required | Description |
|-------|----------|-------------|
| File | Yes | Path relative to repo root |
| Name | Yes | Human-readable name (for workflows: matches `name:` key) |
| Version | Yes | Semantic version (X.Y.Z) |
| Updated | Yes | Last modified date (YYYY-MM-DD) |
| Part of | Yes | Project name and repo URL |
| Description | Yes | What the file does |
| Contributors | Yes | List of contributors with roles |
| Changelog | Yes | Version history with descriptions |

### Python Files

Python scripts use docstring headers:

```python
#!/usr/bin/env python3
"""
TNI Toolkit - [Script Name]
File: [path/to/script.py]
Version: X.Y.Z
Updated: YYYY-MM-DD
Part of: TNI Toolkit (https://github.com/salvo-praxis/tni-toolkit)

Description:
    Brief description of what this script does.
    Can span multiple lines if needed.

Contributors:
    - Name (@handle) - contribution type
    - Claude - contribution type

Changelog:
    X.Y.Z - Description of changes
"""
```

### Shell Scripts (Bash/PowerShell)

Shell scripts use comment headers:

**Bash:**
```bash
#!/bin/bash
# ============================================================================
# TNI Toolkit - [Script Name]
# File: [path/to/script.sh]
# Version: X.Y.Z
# Updated: YYYY-MM-DD
# Part of: TNI Toolkit (https://github.com/salvo-praxis/tni-toolkit)
# Description:
#   Brief description of what this script does.
# Contributors:
#   - Name (@handle) - contribution type
# Changelog:
#   X.Y.Z - Description of changes
# ============================================================================
```

**PowerShell:**
```powershell
<#
============================================================================
TNI Toolkit - [Script Name]
File: [path/to/script.ps1]
Version: X.Y.Z
Updated: YYYY-MM-DD
Part of: TNI Toolkit (https://github.com/salvo-praxis/tni-toolkit)
Description:
    Brief description of what this script does.
Contributors:
    - Name (@handle) - contribution type
Changelog:
    X.Y.Z - Description of changes
============================================================================
#>
```

---

## Version History

- **v1.2** (2025-12) - Added Master CSS section (complete copy-paste stylesheet); added Custom Dropdown component; consolidated Interactive States into UI Components (Copy Feedback moved, hover/selected/disabled states already in Interactive Card)
- **v1.1** (2025-12) - Added File Format Standards section (JSON, HTML, YAML, Python, Shell)
- **v1.0** (2025-12) - Initial style guide based on seed-finder and server-calculator
