---
name: klinechart
description: "Use this skill when working with KLineChart - a lightweight, professional-grade financial charting library for K-line (candlestick) charts. This includes creating, customizing, or debugging K-line charts, integrating the library into web projects, working with technical indicators, overlays, figures, and styles. Also use when user mentions klinechart, candlestick chart, financial chart, trading chart, or needs to build trading dashboards."
license: Proprietary. See individual documentation files for terms
metadata:
  builtin_skill_version: "1.0"
---

> **Important:** All documentation paths are relative to this skill directory.
> This is a reference documentation skill - it provides comprehensive guides and API references for the KLineChart library.

# KLineChart Skills Guide

## Overview

**KLineChart** is a lightweight (40k gzipped), professional-grade financial charting library with zero dependencies. It supports K-line (candlestick) charts, technical indicators, overlays, and extensive customization.

## When to Use This Skill

Use this skill when the user wants to:
- Create or customize financial charts (K-line/candlestick charts)
- Integrate KLineChart into web projects
- Work with technical indicators (MA, EMA, MACD, RSI, etc.)
- Add overlays and figures (trend lines, Fibonacci, etc.)
- Configure chart styles and themes
- Build trading dashboards or financial data visualizations
- Debug or troubleshoot KLineChart issues

## Quick Start

### Installation

```bash
# npm
npm install klinecharts

# yarn
yarn add klinecharts

# pnpm
pnpm add klinecharts

# bun
bun add klinecharts
```

### Basic Usage

```javascript
import { KLineChart } from 'klinecharts';

// Create chart instance
const chart = KLineChart.init(document.getElementById('chart'));

// Set data
chart.setData([
  { timestamp: 1609459200000, open: 29000, high: 29500, low: 28500, close: 29200, volume: 1000 },
  // ... more data
]);

// Dispose when done
// KLineChart.dispose(chart);
```

### Using UMD/CDN

```html
<script src="https://unpkg.com/klinecharts/dist/umd/klinecharts.min.js"></script>
<script>
  const chart = klinecharts.init(document.getElementById('chart'));
  chart.setData([...]);
</script>
```

## Documentation Structure

This skill provides comprehensive documentation:

### Core Guides
| Document | Description |
|----------|-------------|
| [guide/quick-start.md](guide/quick-start.md) | Getting started with KLineChart |
| [guide/environment.md](guide/environment.md) | Environment configuration |
| [guide/data-source.md](guide/data-source.md) | Data format and sources |
| [guide/introduction.md](guide/introduction.md) | Overview and features |
| [guide/styles.md](guide/styles.md) | Chart styling options |
| [guide/indicator.md](guide/indicator.md) | Technical indicators |
| [guide/figure.md](guide/figure.md) | Drawing figures (lines, shapes) |
| [guide/overlay.md](guide/overlay.md) | Overlays and annotations |

### API Reference
| Document | Description |
|----------|-------------|
| [api/chart/init.md](api/chart/init.md) | Chart initialization |
| [api/chart/dispose.md](api/chart/dispose.md) | Dispose chart instance |
| [api/chart/registerIndicator.md](api/chart/registerIndicator.md) | Register custom indicators |
| [api/chart/registerFigure.md](api/chart/registerFigure.md) | Register custom figures |
| [api/chart/registerOverlay.md](api/chart/registerOverlay.md) | Register custom overlays |
| [api/chart/registerStyles.md](api/chart/registerStyles.md) | Register custom styles |
| [api/instance/*](api/instance/) | Instance methods (setData, getDataList, etc.) |

### Advanced Topics
| Document | Description |
|----------|-------------|
| [guide/i18n.md](guide/i18n.md) | Internationalization |
| [guide/hot-key.md](guide/hot-key.md) | Keyboard shortcuts |
| [guide/faq.md](guide/faq.md) | Frequently asked questions |
| [guide/v9-to-v10.md](guide/v9-to-v10.md) | Migration guide v9 to v10 |
| [guide/local-development.md](guide/local-development.md) | Local development setup |

### Pro Version
| Document | Description |
|----------|-------------|
| [pro/introduction.md](pro/introduction.md) | Pro version overview |
| [pro/getting-started.md](pro/getting-started.md) | Pro version quick start |
| [pro/data-access.md](pro/data-access.md) | Data access patterns |
| [pro/data-description.md](pro/data-description.md) | Data descriptions |
| [pro/theme.md](pro/theme.md) | Theming |
| [pro/i18n.md](pro/i18n.md) | Pro i18n |
| [pro/api.md](pro/api.md) | Pro API reference |

## Common Use Cases

### Adding Technical Indicators

```javascript
// Add built-in indicators
chart.setIndicator('MA', { period: 5 });
chart.setIndicator('VOL');
chart.setIndicator('MACD');

// Register custom indicator
chart.registerIndicator({
  name: 'MyIndicator',
  calc: (kLineDataList) => {
    return kLineDataList.map(item => ({
      value: (item.high + item.low) / 2
    }));
  },
  precision: 2
});
```

### Customizing Styles

```javascript
chart.setStyles({
  candle: {
    type: 'candle',
    upColor: '#26a69a',
    downColor: '#ef5350',
    noChangeColor: '#888888'
  },
  grid: {
    show: true,
    horizontalLine: { show: true },
    verticalLine: { show: true }
  }
});
```

### Adding Overlays

```javascript
// Add trend line
chart.createOverlay('trendLine', {
  points: [
    { timestamp: 1609459200000, value: 29000 },
    { timestamp: 1612137600000, value: 31000 }
  ]
});
```

## Available Indicators

KLineChart includes built-in indicators:
- **MA** (Moving Average)
- **EMA** (Exponential Moving Average)
- **SMA** (Simple Moving Average)
- **BOLL** (Bollinger Bands)
- **MACD**
- **KDJ**
- **RSI**
- **WR** (Williams %R)
- **CCI**
- **DMI**
- **ATR**
- **OBV**
- And more...

## Important Notes

1. **Data Format**: KLineChart expects data in specific format:
   ```typescript
   interface KLineData {
     timestamp: number;  // Unix timestamp in milliseconds
     open: number;
     high: number;
     low: number;
     close: number;
     volume?: number;
   }
   ```

2. **TypeScript Support**: Full TypeScript definitions included

3. **Framework Agnostic**: Works with React, Vue, Angular, or vanilla JS

4. **Mobile Support**: Responsive design for mobile devices

## Language Versions

English documentation is available in [en-US](en-US/) directory.

## Next Steps

- Start with [guide/quick-start.md](guide/quick-start.md) for initial setup
- Check [guide/indicator.md](guide/indicator.md) for technical indicators
- See [api/chart/init.md](api/chart/init.md) for full API reference
- Explore [pro/introduction.md](pro/introduction.md) for Pro features