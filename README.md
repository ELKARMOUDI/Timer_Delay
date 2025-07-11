# STM32 Timer-Based LED Blinking (STM32F4)

![STM32F4 LED Blink Demo](https://img.shields.io/badge/STM32-Timer_Interrupt-brightgreen) 
![HAL Library](https://img.shields.io/badge/HAL-STM32CubeF4-blue)

Precision LED control using hardware timers on STM32F4. Eliminates `HAL_Delay()` with interrupt-driven timing.

## 📋 Features
- **Hardware Timer** (TIM2) for accurate timing
- **Interrupt-driven** - No CPU busy waiting
- **Configurable** blink rate via prescaler/period
- **STM32CubeMX** compatible project structure
- **Full HAL integration** with callback system

## ⚙️ Hardware Configuration
| Component       | Configuration                          |
|-----------------|----------------------------------------|
| MCU             | STM32F411RE (Nucleo or compatible)     |
| LED             | Onboard PA5      |
| Clock Source    | HSI 16MHz → PLL @ 84MHz                |
| Timer           | TIM2 @ 1.75kHz interrupt frequency     |

## 🔧 Technical Details
### Clock Configuration (RM0383 §6)
```c
HSI (16MHz) → PLL → 84MHz SYSCLK
PLLM = 16, PLLN = 336, PLLP = 4
APB1 Prescaler = 2 → TIM2 clock = 84MHz
