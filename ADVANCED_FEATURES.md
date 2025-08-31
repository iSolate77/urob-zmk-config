# Advanced Features - Inspired by moutis/zmk-config

This document describes the advanced features added to this ZMK configuration, inspired by the excellent work in [moutis/zmk-config](https://github.com/moutis/zmk-config).

## 🎯 Features Overview

### 1. **Enhanced Combo System**
A comprehensive combo system that goes beyond basic key combinations to provide:
- **Smart punctuation combos** - Contextual punctuation placement
- **H-digraph support** - Quick access to common English digraphs (TH, CH, SH, WH, PH, GH)
- **Programming shortcuts** - Arrow functions (->), fat arrows (=>), scope resolution (::)
- **Three-finger macros** - Advanced text expansion and code snippets
- **Editing combos** - Select all, word navigation, home/end with combos

### 2. **Linger Keys**
Hold a key briefly to get paired symbols with the cursor positioned between them:
- `(` → `()` with cursor in middle
- `[` → `[]` with cursor in middle  
- `{` → `{}` with cursor in middle
- `"` → `""` with cursor in middle
- `<` → `<>` with cursor in middle

### 3. **Adaptive Keys**
Context-aware keys that adapt based on what you're typing:
- **QU combo** - Q automatically becomes QU when appropriate
- **Common suffixes** - Quick access to -tion, -ment endings
- **Comma Magic** - Type comma before a letter to capitalize it (comma is deleted)
- **Smart Space** - Auto-capitalize after periods

### 4. **Advanced Behaviors**
- **Sticky app switcher** - Enhanced alt-tab functionality
- **Smart mouse layer** - Intelligent mouse mode activation
- **Programming macros** - Quick code structure generation (if/for/function)
- **Email signatures** - Quick text expansion for common phrases

## 📋 Combo Reference

### Horizontal Combos (Same Row)

#### Left Hand
| Keys | Output | Description |
|------|--------|-------------|
| LT3+LT2 | ESC | Escape |
| LT2+LT1 | Mouse | Smart mouse mode |
| LT1+LT0 | Cmd+Tab | App switcher |
| LM3+LM2 | Tab | Tab/Shift+Alt+Tab |
| LM2+LM1 | Caps Word | Smart capitalization |
| LM1+LM0 | Caps Lock | Toggle caps lock |
| LB4+LB3 | Cmd+A | Select all |
| LB3+LB1 | Cmd+X | Cut |
| LB3+LB2 | Cmd+C | Copy |
| LB2+LB1 | Cmd+V | Paste |
| LB4+LB2 | Cmd+Z | Undo |
| LB1+LB0 | Cmd+Shift+Z | Redo |

#### Right Hand
| Keys | Output | Description |
|------|--------|-------------|
| RT1+RT2 | : | Colon |
| RT2+RT3 | ; | Semicolon |
| RT0+RT1 | ! | Exclamation |
| RT3+RT4 | ? | Question mark |
| RT1+RT3 | Backspace | Delete backward |
| RT0+RT2 | Delete | Delete forward |
| RB0+RB1 | Enter | Return key |

### Vertical Combos (Same Column)

#### Left Hand Symbols
| Keys | Output | Keys | Output |
|------|--------|------|--------|
| LT3+LM3 | @ | LM3+LB3 | ` |
| LT2+LM2 | # | LM2+LB2 | \ |
| LT1+LM1 | $ | LM1+LB1 | = |
| LT0+LM0 | % | LM0+LB0 | ~ |

#### Right Hand Symbols
| Keys | Output | Keys | Output |
|------|--------|------|--------|
| RT0+RM0 | ^ | RM0+RB0 | _ |
| RT1+RM1 | & | RM1+RB1 | - |
| RT2+RM2 | * | RM2+RB2 | / |
| RT3+RM3 | + | RM3+RB3 | \| |

### Three-Finger Combos

#### Programming
| Keys | Output | Description |
|------|--------|-------------|
| RT0+RT1+RT2 | -> | Arrow function |
| RT1+RT2+RT3 | => | Fat arrow |
| LT1+LT2+LT3 | :: | Scope resolution |
| LM1+LM2+LM3 | ... | Ellipsis |

#### Navigation
| Keys | Output | Description |
|------|--------|-------------|
| LB2+LB3+LB4 | Ctrl+Left | Word left |
| RB2+RB3+RB4 | Ctrl+Right | Word right |
| LT2+LT3+LT4 | Home | Beginning of line |
| RT2+RT3+RT4 | End | End of line |

### H-Digraph Combos
Quick access to common English digraphs:
| Keys | Output | Position |
|------|--------|----------|
| RT2+RT4 | TH | T + H key |
| LM2+RT4 | CH | C + H key |
| LM3+RT4 | SH | S + H key |
| LT2+RT4 | WH | W + H key |
| LB3+RT4 | PH | P + H key |
| LT0+RT4 | GH | G + H key |

## 🚀 Activation

To enable these advanced features, add the following to your keymap file (e.g., `cradio.keymap`):

```c
#define ADVANCED_COMBOS 1
#define LINGER_KEYS 1
#define ADAPTIVE_KEYS 1
```

## 🎨 Keymap Visualization

The configuration includes an enhanced keymap visualization system that:
- Shows combo relationships visually
- Highlights adaptive and linger keys
- Groups related combos for easy reference
- Provides layer-specific views

Generate visualizations with:
```bash
just draw
```

## 💡 Usage Tips

1. **Combo Timing**: Fast combos have 18ms timeout, slow combos 30ms
2. **Linger Keys**: Hold for ~200ms to get paired symbols
3. **H-Digraphs**: Natural placement based on letter positions
4. **Comma Magic**: Great for capitalizing words mid-sentence
5. **Three-finger combos**: Use for less frequent but useful shortcuts

## 🔧 Customization

All behaviors and macros are defined in:
- `config/combos_advanced.dtsi` - Combo definitions
- `config/behaviors_advanced.dtsi` - Behavior configurations
- `keymap-drawer/config.yaml` - Visualization settings

## 🙏 Credits

This implementation is inspired by the innovative work in [moutis/zmk-config](https://github.com/moutis/zmk-config), particularly:
- The comprehensive combo system
- Linger key implementation
- Adaptive key concepts
- H-digraph support

Special thanks to moutis for pushing the boundaries of what's possible with ZMK!