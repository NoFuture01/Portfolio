# Custom Mechanical Keyboard

This project involved designing and building a custom mechanical keyboard with a unique layout, custom PCB, programmable firmware, RGB lighting, and support for programmable macros.

The keyboard is built around an **ATmega32 microcontroller** and uses **QMK firmware** to provide a fully customizable keymap, multiple layers, macros, RGB lighting effects, and additional keyboard functionality.

## Project Requirements

- Custom keyboard layout
- ATmega32 microcontroller as the main controller
- QMK firmware support
- USB-C connectivity
- Programmable keymap and macros
- Multiple keyboard layers
- RGB lighting and underglow effects
- Custom-designed PCB

<br>

# Hardware

![Schematic](images/Schematic.png)

The hardware design is relatively simple, with the ATmega32 acting as the main controller of the keyboard.

Decoupling capacitors were added throughout the circuit to improve power stability, filter high-frequency noise, and reduce the possibility of unintended microcontroller resets.

## USB Interface

A USB-C connector was implemented to allow the keyboard to communicate with a computer and to provide power to the device.

A USB6B1 protection IC was added to protect the USB data lines from electrostatic discharge and other electrical disturbances.

A reset button was also included, as it is required to place the microcontroller into the bootloader mode used for programming and flashing QMK firmware.

## ISP Programming

In addition to USB programming, a 5-pin SPI programming connector was included for direct programming of the ATmega32.

This provides an alternative programming method during development, debugging, and firmware recovery.

## Keyboard Matrix

The keyboard was designed using a matrix consisting of:

- 19 columns
- 4 rows

Each key switch is connected through a diode to prevent ghosting and allow reliable detection of multiple simultaneous key presses.

RGB LEDs were also included to provide additional customization and lighting effects.

<br>

## PCB

![PCB](images/PCB.png)

Designing the PCB was one of the most challenging parts of the project.

The layout includes mounting holes and cutouts required for stabilizers used with larger keys. These mechanical requirements reduced the available routing area and made trace routing significantly more challenging.

Almost all 42 available ATmega32 pins were used, requiring careful component placement and routing. As a result, nearly all of the available PCB area was utilized.

This project provided valuable experience in:

- Complex PCB trace routing
- High-density component placement
- Keyboard matrix design
- Mechanical design constraints
- Integrating electrical and mechanical requirements into a single PCB

<br>

# Software

The keyboard firmware was developed using **QMK**, based on existing keyboard templates and modified to support the custom hardware layout.

The firmware provides:

- Custom key mappings
- Multiple keyboard layers
- Programmable macros
- RGB underglow control
- Multiple RGB lighting animations
- Adjustable RGB brightness
- Adjustable RGB color
- Function key layer
- Bootloader access directly from the keyboard

The main keyboard layout uses a custom 75% ISO-style layout.

An additional function layer provides access to function keys, RGB controls, and bootloader functionality.

## Base Layer

The main layer contains the standard keyboard layout, navigation controls, numeric keypad functions, and custom macros.

| Row | Key Layout |
|---|---|
| 1 | `TAB` `Q` `W` `E` `R` `T` `Y` `U` `I` `O` `P` `\` `[` `BACKSPACE` `1` `2` `3` `DELETE` `ESC` |
| 2 | `CAPS LOCK` `A` `S` `D` `F` `G` `H` `J` `K` `L` `;` `'` `]` `ENTER` `4` `5` `6` `-` `RAGE QUIT` |
| 3 | `LEFT SHIFT` `Z` `X` `C` `V` `B` `N` `M` `,` `.` `/` `` ` `` `RIGHT SHIFT` `UP` `7` `8` `9` `=` `SCROLL LOCK` |
| 4 | `LEFT CTRL` `LEFT GUI` `LEFT ALT` `SPACE` `SPACE` `RIGHT ALT` `RIGHT CTRL` `RIGHT GUI` `FUNCTION LAYER` `LEFT` `DOWN` `RIGHT` `0` `.` `*` `PRINT SCREEN` |

The base layer also includes a custom macro for quickly triggering the **Rage Quit** function.

## Function Layer

The function layer is accessed through a momentary layer switch.

This layer provides access to function keys, RGB controls, and the QMK bootloader.

| Function | Control |
|---|---|
| `F1` | Function Key 1 |
| `F2` | Function Key 2 |
| `F3` | Function Key 3 |
| `F4` | Function Key 4 |
| `F5` | Function Key 5 |
| `F6` | Function Key 6 |
| `F7` | Function Key 7 |
| `F8` | Function Key 8 |
| `F9` | Function Key 9 |
| `F10` | Function Key 10 |
| `UG_VALD` | Decrease RGB brightness |
| `UG_VALU` | Increase RGB brightness |
| `UG_HUED` | Decrease RGB hue |
| `UG_HUEU` | Increase RGB hue |
| `UG_PREV` | Previous RGB animation |
| `UG_TOGG` | Toggle RGB lighting |
| `UG_NEXT` | Next RGB animation |
| `QK_BOOT` | Enter QMK bootloader |

Using QMK made it possible to easily modify the keyboard layout and expand its functionality without changing the hardware.

The firmware can be updated to add new layers, macros, shortcuts, or lighting configurations.

<br>

# Final Product

![Product](images/Product.png)

The completed project successfully demonstrated:

- Custom keyboard layout design
- ATmega32-based embedded system development
- USB-C integration
- Custom keyboard matrix implementation
- Complex PCB routing
- Integration of mechanical stabilizer requirements
- QMK firmware development
- Multiple programmable keyboard layers
- Custom macros
- RGB lighting and animation control
- USB and SPI programming support

This project combined embedded programming, PCB design, electronics, and mechanical constraints into a single custom hardware platform. It provided valuable experience in designing a complete product from the initial schematic and PCB layout to firmware development and final assembly.