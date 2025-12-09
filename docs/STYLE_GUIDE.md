# TNI Toolkit Style Guide

Complete styling reference for building TNI Toolkit tools. All tools use a **Network Operations Center (NOC)** aesthetic — dark theme, monospace typography, terminal-style green/blue accents.

---

## Table of Contents

1. [Design Tokens](#design-tokens)
2. [Base Template](#base-template)
3. [Layout Components](#layout-components)
4. [UI Components](#ui-components)
5. [Interactive States](#interactive-states)
6. [Patterns & Examples](#patterns--examples)
7. [Responsive Design](#responsive-design)
8. [Best Practices](#best-practices)

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
```

> ⚠️ **Note:** Native `<select>` elements cannot style their `<option>` children consistently across browsers, especially on dark themes. Use the **Custom Dropdown** pattern below for styled dropdowns.

### Custom Dropdown

A fully-styled dropdown replacement for native `<select>`. Use when you need consistent dark theme styling for option lists.

**When to use:**
- Category/filter dropdowns
- Any dropdown where options need custom styling
- When native `<select>` looks jarring on the dark theme

**HTML Structure:**
```html
<div class="custom-select" id="my-select">
    <div class="custom-select-trigger">Select an option</div>
    <div class="custom-select-options">
        <div class="custom-select-option selected" data-value="all">All Items</div>
        <div class="custom-select-option" data-value="category1">Category 1</div>
        <div class="custom-select-option" data-value="category2">Category 2</div>
    </div>
</div>
```

**CSS:**
```css
/* Custom Dropdown Container */
.custom-select {
    position: relative;
}

/* Trigger (visible button) */
.custom-select-trigger {
    width: 100%;
    padding: 10px 12px;
    padding-right: 36px;
    border-radius: 6px;
    border: 1px solid #30363d;
    background: rgba(22, 27, 34, 0.8);
    color: #c9d1d9;
    font-size: 12px;
    font-family: inherit;
    cursor: pointer;
    transition: border-color 0.15s;
}

.custom-select-trigger:hover {
    border-color: #58a6ff;
}

.custom-select-trigger.open {
    border-color: #58a6ff;
    border-bottom-left-radius: 0;
    border-bottom-right-radius: 0;
}

/* Dropdown arrow */
.custom-select-trigger::after {
    content: '▼';
    position: absolute;
    right: 12px;
    top: 50%;
    transform: translateY(-50%);
    font-size: 10px;
    color: #8b949e;
    transition: transform 0.15s;
}

.custom-select-trigger.open::after {
    transform: translateY(-50%) rotate(180deg);
}

/* Options container */
.custom-select-options {
    position: absolute;
    top: 100%;
    left: 0;
    right: 0;
    background: rgba(22, 27, 34, 0.98);
    border: 1px solid #58a6ff;
    border-top: none;
    border-radius: 0 0 6px 6px;
    max-height: 200px;
    overflow-y: auto;
    z-index: 100;
    display: none;
}

.custom-select-options.open {
    display: block;
}

/* Individual options */
.custom-select-option {
    padding: 10px 12px;
    font-size: 12px;
    cursor: pointer;
    transition: background 0.15s;
    border-bottom: 1px solid #21262d;
}

.custom-select-option:last-child {
    border-bottom: none;
}

.custom-select-option:hover {
    background: rgba(88, 166, 255, 0.08);
}

.custom-select-option.selected {
    background: rgba(0, 255, 136, 0.1);
    color: #00ff88;
}
```

**JavaScript:**
```javascript
const trigger = document.getElementById('my-select').querySelector('.custom-select-trigger');
const options = document.getElementById('my-select').querySelector('.custom-select-options');

// Toggle dropdown
trigger.addEventListener('click', () => {
    trigger.classList.toggle('open');
    options.classList.toggle('open');
});

// Close when clicking outside
document.addEventListener('click', (e) => {
    if (!e.target.closest('#my-select')) {
        trigger.classList.remove('open');
        options.classList.remove('open');
    }
});

// Handle selection
options.querySelectorAll('.custom-select-option').forEach(option => {
    option.addEventListener('click', () => {
        const value = option.dataset.value;
        const text = option.textContent;
        
        // Update trigger text
        trigger.textContent = text;
        
        // Update selected state
        options.querySelectorAll('.custom-select-option').forEach(opt => {
            opt.classList.remove('selected');
        });
        option.classList.add('selected');
        
        // Close dropdown
        trigger.classList.remove('open');
        options.classList.remove('open');
        
        // Do something with the value
        console.log('Selected:', value);
    });
});
```

```css
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

---

## Interactive States

### Hover States

```css
/* Card hover - blue highlight */
.card:hover {
    border-color: #58a6ff;
    background: rgba(88, 166, 255, 0.08);
}

/* Selected state - green highlight */
.card.selected {
    border-color: #00ff88;
    background: rgba(0, 255, 136, 0.1);
}

/* Link hover */
a:hover {
    color: #58a6ff;
}

/* Row hover */
tr:hover td {
    background: rgba(88, 166, 255, 0.05);
}
```

### Active/Pressed States

```css
.btn:active {
    transform: translateY(1px);
}
```

### Disabled States

```css
.disabled,
[disabled] {
    opacity: 0.4;
    cursor: not-allowed;
    pointer-events: none;
}
```

### Copy Feedback

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

## Version History

- **v1.0** (2024-12) - Initial style guide based on seed-finder and server-calculator
