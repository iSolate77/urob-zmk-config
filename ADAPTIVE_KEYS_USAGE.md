# How to Use Adaptive Keys and Magic Features

## Enabling the Features

Add these defines to your keymap file (e.g., `cradio.keymap`):
```c
#define ADVANCED_COMBOS 1
#define LINGER_KEYS 1
#define ADAPTIVE_KEYS 1
```

## Using Adaptive Keys in Your Keymap

### 1. Magic Comma
Replace your regular comma key with the magic comma:

```c
// Instead of:
&kp COMMA

// Use:
&comma_magic
```

**How it works:**
- Type normally: `, ` produces a comma and space
- Type comma then a letter: `,[letter]` deletes the comma and capitalizes the letter
- Example: typing `,hello` produces `Hello`

### 2. Adaptive Q
Replace your Q key with the adaptive Q:

```c
// Instead of:
&kp Q

// Use:
&ak_Q
```

**How it works:**
- Normally produces `Q`
- After S, E, A, I, L, or N, it automatically produces `QU`
- Examples: `squ`are, `equ`al, `aqu`a, `liqu`id

### 3. Linger Keys for Paired Symbols
Use linger keys for brackets and quotes:

```c
// Instead of regular keys:
&kp LPAR   // (
&kp LBKT   // [
&kp LBRC   // {
&kp DQT    // "
&kp LT     // <

// Use linger keys:
&lk_parens 0 0    // Tap: ( | Hold: () with cursor in middle
&lk_brackets 0 0  // Tap: [ | Hold: [] with cursor in middle
&lk_braces 0 0    // Tap: { | Hold: {} with cursor in middle
&lk_quotes 0 0    // Tap: " | Hold: "" with cursor in middle
&lk_angles 0 0    // Tap: < | Hold: <> with cursor in middle
```

## Example Keymap Integration

Here's how to modify your base layer to use these features:

```c
ZMK_BASE_LAYER(Base,
//╭─────────────┬─────────────┬─────────────┬─────────────┬─────────────╮
    &ak_Q         &kp W         &kp E         &kp R         &kp T         ,
    &kp A         &kp S         &kp D         &kp F         &kp G         ,
    &kp Z         &kp X         &kp C         &kp V         &kp B         ,
                                &lt NAV SPACE &kp LSHFT                   ,
//╰─────────────┴─────────────┴─────────────┴─────────────┴─────────────╯

//╭─────────────┬─────────────┬─────────────┬─────────────┬─────────────╮
    &kp Y         &kp U         &kp I         &kp O         &kp P         ,
    &kp H         &kp J         &kp K         &kp L         &kp SEMI      ,
    &kp N         &kp M         &comma_magic  &kp DOT       &kp SLASH     ,
                                &kp ENTER     &lt NUM BSPC                ,
//╰─────────────┴─────────────┴─────────────┴─────────────┴─────────────╯
)
```

## Tips

1. **Comma Magic Timing**: You have 500ms after typing comma to type a letter for capitalization
2. **Linger Key Timing**: Hold for ~200ms to get paired symbols
3. **Adaptive Q**: Works best with relaxed typing - the context detection has a 250ms window

## Troubleshooting

If adaptive keys aren't working:

1. Make sure you have the required modules in `config/west.yml`:
   - `zmk-adaptive-key`
   - `zmk-helpers`

2. Ensure the behaviors file is included in your keymap:
   ```c
   #ifdef ADAPTIVE_KEYS
   #include "behaviors_advanced.dtsi"
   #endif
   ```

3. Check that you're using the correct binding syntax (e.g., `&comma_magic` not `&comma_magic 0 0`)

## Customization

You can modify the trigger keys and timing in `behaviors_advanced.dtsi`:

- Change trigger letters for adaptive Q
- Adjust timing windows (max-prior-idle-ms)
- Add more adaptive keys for other common patterns