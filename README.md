
# EXPERIMENT-01-INTERFACING-A-DIGITAL-OUTPUT-TO-IOT-DEVELOPMENT-BOARD

###  DATE:17/08/2024 

###  NAME: Anbuselvan.S
###  ROLL NO : 212223240008
###  DEPARTMENT: AIML

## Aim: 
To Interface a Digital output (LED) to ARM IOT development board and write a  program to blink an led 
## Components required: 
STM32 CUBE IDE, ARM IOT development board,  STM programmer tool.
## Theory 
### ARM7 Processor and LPC2148 Microcontroller

## What is an ARM7 Processor?

The ARM7 processor is commonly used in embedded system applications. It provides a balance between classic and new Cortex series, making it an excellent choice for learning hardware and software design. This processor is well-documented by NXP Semiconductors, making it a good fit for apprentices seeking to gain in-depth knowledge.

## LPC2148 Microcontroller

The LPC2148 microcontroller is designed by Philips (NXP Semiconductor) and is equipped with several in-built features and peripherals. These features make it a reliable and efficient choice for application developers. The LPC2148 is a 16-bit or 32-bit microcontroller based on the ARM7 family.

### Features of LPC2148

The main features of the LPC2148 microcontroller include:

1. **Architecture and Packaging:**
   - 16-bit or 32-bit ARM7 family-based microcontroller.
   - Available in a small LQFP64 package.

2. **Programming:**
   - In-System Programming (ISP) or In-Application Programming (IAP) using on-chip boot loader software.

3. **Memory:**
   - On-chip static RAM: 8 kB - 40 kB.
   - On-chip flash memory: 32 kB - 512 kB.
   - Wide interface: 128-bit.
   - Accelerator allows 60 MHz high-speed operation.

4. **Performance:**
   - Takes 400 milliseconds to erase the full chip.
   - Takes 1 millisecond to program 256 bytes.

5. **Debugging:**
   - Embedded Trace interfaces and Embedded ICE RT for real-time debugging with high-speed instruction tracing.
   - On-chip Real Monitor software.

6. **USB Support:**
   - 2 kB of endpoint RAM and USB 2.0 full-speed device controller.
   - 8 kB on-chip RAM near USB with DMA.

7. **Analog and Digital Input/Output:**
   - One or two 10-bit ADCs offering 6 or 14 analog inputs with a low conversion time of 2.44 μs per channel.
   - 10-bit DAC providing changeable analog output.
   - 32-bit timers (2), PWM unit, and watchdog.
   - Low-power Real-Time Clock (RTC) with 32 kHz clock input.

8. **Serial Interfaces:**
   - Two 16C550 UARTs.
   - Two I2C buses with 400 kbit/s speed.

9. **GPIO and Interrupts:**
   - 5V tolerant fast general-purpose I/O pins in a small LQFP64 package.
   - 21 external interrupt pins.

10. **Clocking:**
    - 60 MHz maximum CPU clock available from the programmable on-chip phase-locked loop (PLL) with a settling time of 100 μs.
    - Integrated oscillator operates with an external crystal ranging from 1 MHz to 25 MHz.

11. **Power Management:**
    - Power-saving modes include idle and power down.
    - Individual enable/disable of peripheral functions and peripheral clock scaling for additional power optimization.

 
 

## Procedure:
 1. click on STM 32 CUBE IDE, the following screen will appear 
 ![image](https://user-images.githubusercontent.com/36288975/226189166-ac10578c-c059-40e7-8b80-9f84f64bf088.png)

 2. click on FILE, click on new stm 32 project 
 ![image](https://user-images.githubusercontent.com/36288975/226189215-2d13ebfb-507f-44fc-b772-02232e97c0e3.png)
![image](https://user-images.githubusercontent.com/36288975/226189230-bf2d90dd-9695-4aaf-b2a6-6d66454e81fc.png)
3. select the target to be programmed  as shown below and click on next 

![image](https://user-images.githubusercontent.com/36288975/226189280-ed5dcf1d-dd8d-43ae-815d-491085f4863b.png)

4.select the program name 
![image](https://user-images.githubusercontent.com/36288975/226189316-09832a30-4d1a-4d4f-b8ad-2dc28f137711.png)


5. corresponding ioc file will be generated automatically 
![image](https://user-images.githubusercontent.com/36288975/226189378-3abbdee2-0df6-470f-a3cd-79c74e3d3ad8.png)

6.select the appropriate pins as gipo, in or out, USART or required options and configure 
![image](https://user-images.githubusercontent.com/36288975/226189403-f7179f1a-3eae-4637-826b-ab4ec35ba1e1.png)
![image](https://user-images.githubusercontent.com/36288975/226189425-2b2414ce-49b3-4b61-a260-c658cb2e4152.png)


7.click on cntrl+S , automaticall C program will be generated 
![image](https://user-images.githubusercontent.com/36288975/226189443-8b43451d-0b14-47e4-a20b-cc09c6ad8458.png)
![image](https://user-images.githubusercontent.com/36288975/226189450-85ffa969-2ffb-4788-81e5-72d60fdda0f1.png)
8. edit the program and as per required 
![image](https://user-images.githubusercontent.com/36288975/226189461-a573e62f-a109-4631-a250-a20925758fe0.png)

9. use project and build all 
![image](https://user-images.githubusercontent.com/36288975/226189554-3f7101ac-3f41-48fc-abc7-480bd6218dec.png)
10. once the project is bulild 
![image](https://user-images.githubusercontent.com/36288975/226189577-c61cc1eb-3990-4968-8aa6-aefffc766b70.png)

11. click on debug option 
![image](https://user-images.githubusercontent.com/36288975/226189625-37daa9a3-62e9-42b5-a5ce-2ac63345905b.png)


12. connect the stm nucleo board and click on run 
![image](https://user-images.githubusercontent.com/36288975/226189649-b5dff389-91df-4eca-b84a-1127c6562637.png)






## STM 32 CUBE PROGRAM :
```
#include "main.h"


void SystemClock_Config(void);
static void MX_GPIO_Init(void);

int main(void)
{

  while (1)
  {
	  HAL_GPIO_WritePin(GPIOA, GPIO_PIN_0, GPIO_PIN_SET);
	  HAL_Delay(2000);
	  HAL_GPIO_WritePin(GPIOA, GPIO_PIN_0, GPIO_PIN_RESET);
	  HAL_Delay(2000);

  }
}

void SystemClock_Config(void)
{
  RCC_OscInitTypeDef RCC_OscInitStruct = {0};
  RCC_ClkInitTypeDef RCC_ClkInitStruct = {0};

  __HAL_PWR_VOLTAGESCALING_CONFIG(PWR_REGULATOR_VOLTAGE_SCALE2);

  RCC_OscInitStruct.OscillatorType = RCC_OSCILLATORTYPE_MSI;
  RCC_OscInitStruct.MSIState = RCC_MSI_ON;
  RCC_OscInitStruct.MSICalibrationValue = RCC_MSICALIBRATION_DEFAULT;
  RCC_OscInitStruct.MSIClockRange = RCC_MSIRANGE_6;
  RCC_OscInitStruct.PLL.PLLState = RCC_PLL_NONE;
  if (HAL_RCC_OscConfig(&RCC_OscInitStruct) != HAL_OK)
  {
    Error_Handler();
  }

  RCC_ClkInitStruct.ClockType = RCC_CLOCKTYPE_HCLK3|RCC_CLOCKTYPE_HCLK
                              |RCC_CLOCKTYPE_SYSCLK|RCC_CLOCKTYPE_PCLK1
                              |RCC_CLOCKTYPE_PCLK2;
  RCC_ClkInitStruct.SYSCLKSource = RCC_SYSCLKSOURCE_MSI;
  RCC_ClkInitStruct.AHBCLKDivider = RCC_SYSCLK_DIV1;
  RCC_ClkInitStruct.APB1CLKDivider = RCC_HCLK_DIV1;
  RCC_ClkInitStruct.APB2CLKDivider = RCC_HCLK_DIV1;
  RCC_ClkInitStruct.AHBCLK3Divider = RCC_SYSCLK_DIV1;

  if (HAL_RCC_ClockConfig(&RCC_ClkInitStruct, FLASH_LATENCY_0) != HAL_OK)
  {
    Error_Handler();
  }
}

static void MX_GPIO_Init(void)
{
  GPIO_InitTypeDef GPIO_InitStruct = {0};

  __HAL_RCC_GPIOA_CLK_ENABLE();

  HAL_GPIO_WritePin(GPIOA, GPIO_PIN_0, GPIO_PIN_RESET);

  GPIO_InitStruct.Pin = GPIO_PIN_0;
  GPIO_InitStruct.Mode = GPIO_MODE_OUTPUT_PP;
  GPIO_InitStruct.Pull = GPIO_NOPULL;
  GPIO_InitStruct.Speed = GPIO_SPEED_FREQ_LOW;
  HAL_GPIO_Init(GPIOA, &GPIO_InitStruct);

}

void Error_Handler(void)
{

  __disable_irq();
  while (1)
  {
  }
}

#ifdef  USE_FULL_ASSERT
#endif
```
## OUTPUT  :
 
 
 
 
## Result :
Interfacing a digital output with ARM microcontroller based IOT development is executed and the results are verified.
