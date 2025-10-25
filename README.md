# EXPERIMENT-04-INTERRUPT-GENERATION-USING-SENSOR-AND-VISUALIZING-USING-SERIAL-MONITOR

###  DATE: 21/9/2025

###  NAME: thirunavukkarasu meenakshisundaram
###  ROLL NO : 212224220117
###  DEPARTMENT: IT
### Aim:
To Interface a IR Sensor to digital port of iot development board  and generate an interrupt and visualize on the serial monitor 

### Components required:
STM32 CUBE IDE,  serial port utility monitor,IR Pair Sensor .


## Theory :

An infrared (IR) sensor a proximity sensor, or a ‘nearness’ sensor senses whether there is an object near it or not. The IR stands for Infrared sensor. Infrared is the light out of our visible spectrum.

Working of an IR Sensor
The white LED here is an IR LED which works as the transmitter and the component next to the IR LED is a photodiode that works as the receiver in the IR sensor.

The IR transmitter continuously emits the IR light and the IR receiver keeps on checking for the reflected light. If the light gets reflected back by hitting any object in front it, the IR receiver receives this light. This way the object is detected in the case of the IR sensor.

The blue knob here is a potentiometer. You can control the range i.e. from how far you want to detect the object by changing the value of the potentiometer.

An IR sensor has two small LED indicators – one for power, which is ON the entire time the sensor is ON; the other is the Signal LED which detects the object. The signal LED has two states or situations:

ON (Active) when it detects an object
OFF (Inactive) when it doesn’t detect any object

![image](https://github.com/vasanthkumarch/EXPERIMENT--04-INTERUPT-GENRATION-USING-SENSOR-AND-VISUALIZING-USING-SERIAL-MONITOR/assets/36288975/9bf61298-1deb-48d7-b88f-bd08e3cc6a83)

Now that we have a little idea about its works, let’s take a look at how to interface it with evive and see it in action.

Connect VCC pin to the +5V pin on evive.
Connect GND pin to evive’s GND pin.
Connect OUT to any gpio and configure that pin as EXTI mode 

### Interrupts


Interrupts are asynchronous (i.e. can happen anytime) events that disrupt the normal flow of your program. This allows the microcontroller to focus on a key task and attend to these events (e.g. pressing a button) as they come without needing to wait for them.

With interrupt, we do not need to continuously check the state of the digital input pin. When an interrupt occurs (a change is detected), the processor stops the execution of the main program and a function is called upon known as ISR or the Interrupt Service Routine. The processor then temporarily works on a different task (ISR) and then gets back to the main program after the handling routine has ended.

![image](https://github.com/vasanthkumarch/EXPERIMENT--04-INTERUPT-GENRATION-USING-SENSOR-AND-VISUALIZING-USING-SERIAL-MONITOR/assets/36288975/cb4ac7aa-30ed-4b97-b3b4-1986db9f1558)
The STM32 ARM microcontroller interrupts are generated in the following manner:

The system runs the ISR and then goes back to the main program. The NVIC and EXTI are configured. The Interrupt Service Routine (ISR) also known as the interrupt service routine handler is defined to enable the external interrupts.

 
Interrupt Lines (EXTI0-EXTI15)
The STM32 ARM microcontroller features 23 event sources which are divided into two sections. The first section corresponds t external pins on each port which are P0-P15. The second section corresponds to RTC, ethernet, USB interrupts. Therefore, in the first section, we have 16 lines corresponding to line0 till line15. All of these map to a pin number.

![image](https://github.com/vasanthkumarch/EXPERIMENT--04-INTERUPT-GENRATION-USING-SENSOR-AND-VISUALIZING-USING-SERIAL-MONITOR/assets/36288975/1110746f-6be2-4d12-9a34-66004e4b307b)


The diagram below shows how the GPIO pins are connected to the 16 interrupt lines:

## Procedure:

 1. click on STM 32 CUBE IDE, the following screen will appear
    
 ![image](https://user-images.githubusercontent.com/36288975/226189166-ac10578c-c059-40e7-8b80-9f84f64bf088.png)

 2. click on FILE, click on new stm 32 project
  
 ![image](https://user-images.githubusercontent.com/36288975/226189215-2d13ebfb-507f-44fc-b772-02232e97c0e3.png)
 
![image](https://user-images.githubusercontent.com/36288975/226189230-bf2d90dd-9695-4aaf-b2a6-6d66454e81fc.png)

3. select the target to be programmed  as shown below and click on next 

![Screenshot 2025-03-11 134231](https://github.com/user-attachments/assets/09e61f3d-224f-4ca8-96d4-7336869df5c7)

4.select the program name 

![image](https://user-images.githubusercontent.com/36288975/226189316-09832a30-4d1a-4d4f-b8ad-2dc28f137711.png)


5. corresponding ioc file will be generated automatically
   
   ![Screenshot 2025-03-11 134528](https://github.com/user-attachments/assets/df427edd-e24a-4612-a858-aeae859b379f)


6.select the appropriate pins as gipo, in or out, USART or required options and configure 

![Screenshot 2025-03-11 134617](https://github.com/user-attachments/assets/125ee548-30b1-4c88-932f-adf07984522f)
![Screenshot 2025-03-11 134642](https://github.com/user-attachments/assets/0adfbb58-4cad-408a-9300-f4808b53cac4)


7.click on cntrl+S , automaticall C program will be generated 

![Screenshot 2025-03-11 134709](https://github.com/user-attachments/assets/70b83b79-1569-4f14-99d5-e2adbb4e692d)

8. edit the program and as per required
   
![image](https://user-images.githubusercontent.com/36288975/226189461-a573e62f-a109-4631-a250-a20925758fe0.png)

9. use project and build all
    
![image](https://user-images.githubusercontent.com/36288975/226189554-3f7101ac-3f41-48fc-abc7-480bd6218dec.png)

10. once the project is build
    
![image](https://user-images.githubusercontent.com/36288975/226189577-c61cc1eb-3990-4968-8aa6-aefffc766b70.png)

11. connect the iot board to power supply and usb

12. After connecting open the STM cube programmer

![Screenshot 2025-03-11 135208](https://github.com/user-attachments/assets/bb67ab6b-81a5-450c-b170-4276a9b87ef2)


13. Connect the STM board through the COM port, then upload the corresponding project ELF file/Hex file or Bin file in Erasing & Programming Window,while ensuring the board is in flash mode, and click on 'Start Program'.

    ![image](https://github.com/user-attachments/assets/9383531d-8204-4697-9321-55afb6abee2e)

14.  After the file download is complete, switch your board to run mode and press the reset button to see the output

15. click on the serial port utility 
![image](https://github.com/user-attachments/assets/72d35bbb-5261-4986-a24f-cfa2c00e26d6)

16. click on the run to observe the values 
 

## STM 32 CUBE PROGRAM :
```C
#include "main.h"

#include "stm32wlxx_hal.h"   // 🔹 CORRECTED: Required HAL header for the STM32WLxx series (Matching -DSTM32WLE5xx build flag)
#include "stdio.h"
#include "stdbool.h"

// --- Global Variables for Interrupt Communication ---
UART_HandleTypeDef huart2;

// Volatile flag to signal the main loop that an interrupt occurred
volatile bool g_state_changed = false;
// Volatile variable to store the actual pin state read in the interrupt
volatile GPIO_PinState g_current_pin_state;

// Forward declaration needed for the compiler
void Error_Handler(void);

// --- PUTCHAR PROTOTYPE MACROS for printf redirection (Prototypes only) ---
#if defined(ICCARM) || defined(__ARMCC_VERSION)
#define PUTCHAR_PROTOTYPE int fputc(int ch, FILE *f)
#elif defined(GNUC)
// NOTE: We rely on the explicit function definition below for the body,
// but keep this macro definition in case it is used elsewhere.
#define PUTCHAR_PROTOTYPE int __io_putchar(int ch)
#endif

// --- Function Prototypes ---
void SystemClock_Config(void);
static void MX_GPIO_Init(void);
static void MX_USART2_UART_Init(void);

int main(void)
{
    HAL_Init();
    SystemClock_Config();
    MX_GPIO_Init();
    MX_USART2_UART_Init();

    printf("System Initialized (Interrupt-Driven IR Sensor)\n");

    // Main loop runs continuously
    while (1)
    {
        // Check the volatile flag set by the interrupt
        if (g_state_changed)
        {
            g_state_changed = false; // Acknowledge and clear the flag immediately

            // Process the event (slow I/O and non-critical operations here)
            if (g_current_pin_state == GPIO_PIN_RESET)
            {
                // IR Sensor is typically active LOW (RESET) when an obstacle is present
                HAL_GPIO_WritePin(GPIOB, GPIO_PIN_5, GPIO_PIN_SET);
                printf("Obstacle Detected (PB4 LOW) - LED ON\n");
            }
            else
            {
                // IR Sensor is typically active HIGH (SET) when no obstacle is present
                HAL_GPIO_WritePin(GPIOB, GPIO_PIN_5, GPIO_PIN_RESET);
                printf("Obstacle Cleared (PB4 HIGH) - LED OFF\n");
            }

            // Add a small delay for debouncing after an event is registered,
            // preventing the main loop from spamming the UART on noisy edges.
            HAL_Delay(50);
        }
    }
}

/**
  * @brief EXTI line detection callback (Called by the HAL driver after interrupt).
  * @param GPIO_Pin: Specifies the pins connected EXTI line
  */
void HAL_GPIO_EXTI_Callback(uint16_t GPIO_Pin)
{
    // Ensure the interrupt is from the intended pin (PB4)
    if (GPIO_Pin == GPIO_PIN_4)
    {
        // Read the current state of the pin that triggered the interrupt
        g_current_pin_state = HAL_GPIO_ReadPin(GPIOB, GPIO_PIN_4);
        g_state_changed = true; // Signal the main loop to process the event
    }
}

// IRQ HANDLER FIXED: Using the specific handler name EXTI4_IRQHandler,
// which is required for linking in many CubeMX/HAL projects.
void EXTI4_IRQHandler(void)
{
    // Clears the interrupt flag for PB4
    HAL_GPIO_EXTI_IRQHandler(GPIO_PIN_4);
}

// --- printf Redirection Implementation (GCC) ---
int __io_putchar(int ch) // 🔹 FIX: Explicitly define the GCC function signature to resolve syntax error
{
    // Transmits single character over UART2 with max delay (blocking)
    HAL_UART_Transmit(&huart2, (uint8_t *)&ch, 1, HAL_MAX_DELAY);
    return ch;
}

// --- System Clock Configuration ---
void SystemClock_Config(void)
{
    RCC_OscInitTypeDef RCC_OscInitStruct = {0};
    RCC_ClkInitTypeDef RCC_ClkInitStruct = {0};

    // NOTE: This regulator config might need adjustment for STM32WLxx,
    // but leaving as is to maintain original clock structure where possible.
    __HAL_PWR_VOLTAGESCALING_CONFIG(PWR_REGULATOR_VOLTAGE_SCALE2);

    RCC_OscInitStruct.OscillatorType = RCC_OSCILLATORTYPE_MSI;
    RCC_OscInitStruct.MSIState = RCC_MSI_ON;
    RCC_OscInitStruct.MSICalibrationValue = RCC_MSICALIBRATION_DEFAULT;
    RCC_OscInitStruct.MSIClockRange = RCC_MSIRANGE_6;
    RCC_OscInitStruct.PLL.PLLState = RCC_PLL_NONE;

    if (HAL_RCC_OscConfig(&RCC_OscInitStruct) != HAL_OK) Error_Handler();

    RCC_ClkInitStruct.ClockType = RCC_CLOCKTYPE_HCLK3 | RCC_CLOCKTYPE_HCLK |
                                  RCC_CLOCKTYPE_SYSCLK | RCC_CLOCKTYPE_PCLK1 |
                                  RCC_CLOCKTYPE_PCLK2;
    RCC_ClkInitStruct.SYSCLKSource = RCC_SYSCLKSOURCE_MSI;
    RCC_ClkInitStruct.AHBCLKDivider = RCC_SYSCLK_DIV1;
    RCC_ClkInitStruct.APB1CLKDivider = RCC_HCLK_DIV1;
    RCC_ClkInitStruct.APB2CLKDivider = RCC_HCLK_DIV1;
    RCC_ClkInitStruct.AHBCLK3Divider = RCC_SYSCLK_DIV1;

    if (HAL_RCC_ClockConfig(&RCC_ClkInitStruct, FLASH_LATENCY_0) != HAL_OK) Error_Handler();
}

// --- UART Initialization ---
static void MX_USART2_UART_Init(void)
{
    huart2.Instance = USART2;
    huart2.Init.BaudRate = 115200;
    huart2.Init.WordLength = UART_WORDLENGTH_8B;
    huart2.Init.StopBits = UART_STOPBITS_1;
    huart2.Init.Parity = UART_PARITY_NONE;
    huart2.Init.Mode = UART_MODE_TX_RX;
    huart2.Init.HwFlowCtl = UART_HWCONTROL_NONE;
    huart2.Init.OverSampling = UART_OVERSAMPLING_16;

    if (HAL_UART_Init(&huart2) != HAL_OK) Error_Handler();
}

// --- GPIO Initialization ---
static void MX_GPIO_Init(void)
{
    // Enable GPIOB Clock (for sensor/LED) and GPIOA Clock (for UART2)
    __HAL_RCC_GPIOB_CLK_ENABLE();
    __HAL_RCC_GPIOA_CLK_ENABLE(); 

    GPIO_InitTypeDef GPIO_InitStruct = {0};

    // 1. Configure UART2 Pins (PA2 = TX, PA3 = RX - Common setup for USART2)
    GPIO_InitStruct.Pin = GPIO_PIN_2 | GPIO_PIN_3;
    GPIO_InitStruct.Mode = GPIO_MODE_AF_PP;
    GPIO_InitStruct.Pull = GPIO_NOPULL;
    GPIO_InitStruct.Speed = GPIO_SPEED_FREQ_LOW;
    GPIO_InitStruct.Alternate = GPIO_AF7_USART2; // Set Alternate Function to USART2
    HAL_GPIO_Init(GPIOA, &GPIO_InitStruct); // Initialize on GPIOA

    // 2. Configure PB4 for IR Sensor Input with Interrupt
    // Use RISING_FALLING mode to detect state change in both directions (obstacle in, obstacle out)
    GPIO_InitStruct.Pin = GPIO_PIN_4;
    GPIO_InitStruct.Mode = GPIO_MODE_IT_RISING_FALLING;
    GPIO_InitStruct.Pull = GPIO_NOPULL;
    HAL_GPIO_Init(GPIOB, &GPIO_InitStruct);

    // 3. Configure PB5 for LED Output
    GPIO_InitStruct.Pin = GPIO_PIN_5;
    GPIO_InitStruct.Mode = GPIO_MODE_OUTPUT_PP;
    GPIO_InitStruct.Pull = GPIO_NOPULL;
    GPIO_InitStruct.Speed = GPIO_SPEED_FREQ_LOW;
    HAL_GPIO_Init(GPIOB, &GPIO_InitStruct);

    // Set and Enable EXTI Interrupt
    HAL_NVIC_SetPriority(EXTI4_IRQn, 0, 0);
    HAL_NVIC_EnableIRQ(EXTI4_IRQn);
}

// --- Error Handler ---
void Error_Handler(void)
{
    // In case of error, enter infinite loop and disable interrupts
    __disable_irq();
    while (1)
    {
        // Add error indication logic here (e.g., fast LED blink)
    }
}

#ifdef USE_FULL_ASSERT
void assert_failed(uint8_t *file, uint32_t line)
{
    printf("Wrong parameters value: file %s on line %lu\r\n", file, line);
}
#endif
```


## Output screen shots of serial port utility   :
 
<img width="1909" height="669" alt="image" src="https://github.com/user-attachments/assets/f965ed40-d0ae-4419-b4c0-0725360feb2f" />



 ## Circuit board :

<img width="441" height="659" alt="491905783-be6a769e-2554-4503-91bc-3b48f841fc6c" src="https://github.com/user-attachments/assets/14d453f2-8e12-4f1c-84a7-c60ee30b1612" />


 
## Result :
Interfacing a  IR SENSOR and interrupt is generated using external interrupt mode , visualized on serial port 
