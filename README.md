# STM32 Based Token Number Display System

### AIM:
To develop a single sided PCB board for a single digit token number display system with buzzer.

### Requirement:
Proteus Software

### Schematic:

1) Design the circuit using schematic diagram

2) Open pcb layout and convert it to 3d view

3) Configure I/O pins using idle software

4) Change the code such that it is suited for seven segment display

5) upload the elf and run

### Code:
```c

void display(int n)
{
		int x[11][8]={{0,0,1,1,1,1,1,1},{0,0,0,0,0,1,1,0},{0,1,0,1,1,0,1,1},{1,1,0,0,1,1,1,1},{0,1,1,0,0,1,1,0},{0,1,1,0,1,1,0,1},{0,1,1,1,1,1,0,1},{0,0,0,0,0,1,1,1},{0,1,1,1,1,1,1,1},{0,1,1,0,0,1,1,1}};
		if(n>=0 && n<10)
		{
			if(x[n][0]==1)
				HAL_GPIO_WritePin(GPIOA, GPIO_PIN_0, GPIO_PIN_SET);
			else
				HAL_GPIO_WritePin(GPIOA, GPIO_PIN_0, GPIO_PIN_RESET);

			if(x[n][1]==1)
							HAL_GPIO_WritePin(GPIOA, GPIO_PIN_1, GPIO_PIN_SET);
			else
							HAL_GPIO_WritePin(GPIOA, GPIO_PIN_1, GPIO_PIN_RESET);

			if(x[n][2]==1)
							HAL_GPIO_WritePin(GPIOA, GPIO_PIN_2, GPIO_PIN_SET);
						else
							HAL_GPIO_WritePin(GPIOA, GPIO_PIN_2, GPIO_PIN_RESET);
			if(x[n][3]==1)
							HAL_GPIO_WritePin(GPIOA, GPIO_PIN_3, GPIO_PIN_SET);
						else
							HAL_GPIO_WritePin(GPIOA, GPIO_PIN_3, GPIO_PIN_RESET);
			if(x[n][4]==1)
							HAL_GPIO_WritePin(GPIOA, GPIO_PIN_4, GPIO_PIN_SET);
						else
							HAL_GPIO_WritePin(GPIOA, GPIO_PIN_4, GPIO_PIN_RESET);
			if(x[n][5]==1)
							HAL_GPIO_WritePin(GPIOA, GPIO_PIN_5, GPIO_PIN_SET);
						else
							HAL_GPIO_WritePin(GPIOA, GPIO_PIN_5, GPIO_PIN_RESET);
			if(x[n][6]==1)
							HAL_GPIO_WritePin(GPIOA, GPIO_PIN_6, GPIO_PIN_SET);
						else
							HAL_GPIO_WritePin(GPIOA, GPIO_PIN_6, GPIO_PIN_RESET);
			if(x[n][7]==1)
							HAL_GPIO_WritePin(GPIOA, GPIO_PIN_7, GPIO_PIN_SET);
						else
							HAL_GPIO_WritePin(GPIOA, GPIO_PIN_7, GPIO_PIN_RESET);

		}
		else
		{
			HAL_GPIO_WritePin(GPIOA, GPIO_PIN_0, GPIO_PIN_RESET);
			HAL_GPIO_WritePin(GPIOA, GPIO_PIN_1, GPIO_PIN_RESET);
			HAL_GPIO_WritePin(GPIOA, GPIO_PIN_2, GPIO_PIN_RESET);
			HAL_GPIO_WritePin(GPIOA, GPIO_PIN_3, GPIO_PIN_RESET);
			HAL_GPIO_WritePin(GPIOA, GPIO_PIN_4, GPIO_PIN_RESET);
			HAL_GPIO_WritePin(GPIOA, GPIO_PIN_5, GPIO_PIN_RESET);
			HAL_GPIO_WritePin(GPIOA, GPIO_PIN_6, GPIO_PIN_RESET);
			HAL_GPIO_WritePin(GPIOA, GPIO_PIN_7, GPIO_PIN_RESET);

		}

}
/* USER CODE END 0 */

/**
  * @brief  The application entry point.
  * @retval int
  */
int main(void)
{
  /* USER CODE BEGIN 1 */
	GPIO_PinState s1;
	int count=0;
  /* USER CODE END 1 */

  /* MCU Configuration--------------------------------------------------------*/

  /* Reset of all peripherals, Initializes the Flash interface and the Systick. */
  HAL_Init();

  /* USER CODE BEGIN Init */

  /* USER CODE END Init */

  /* Configure the system clock */
  SystemClock_Config();

  /* USER CODE BEGIN SysInit */

  /* USER CODE END SysInit */

  /* Initialize all configured peripherals */
  MX_GPIO_Init();
  /* USER CODE BEGIN 2 */

  /* USER CODE END 2 */

  /* Infinite loop */
  /* USER CODE BEGIN WHILE */
  while (1)
  {
    /* USER CODE END WHILE */
	  display(count);
	  s1=HAL_GPIO_ReadPin(GPIOB, GPIO_PIN_0);
	  if(s1==GPIO_PIN_RESET)
	  {
		  count = (count+1)%10;
		  HAL_Delay(500);

	  }
	  HAL_GPIO_WritePin(GPIOB, GPIO_PIN_1, GPIO_PIN_SET);
	  		  HAL_Delay(3000);
	  		  HAL_GPIO_WritePin(GPIOB, GPIO_PIN_1, GPIO_PIN_RESET);
    /* USER CODE BEGIN 3 */
  }
  /* USER CODE END 3 */
}
```
### PCB Layout:

![pcblayout](https://user-images.githubusercontent.com/75234946/233892575-871687fd-5df7-48cd-8136-fc734d8a9a1d.png)

#### TopLayer:

![toplayer-min](https://user-images.githubusercontent.com/75234946/233893725-86d8eccb-ac35-428b-ba8f-c95f933311a5.png)

#### BottomLayer:

![botlayr](https://user-images.githubusercontent.com/75234946/233892794-ddffa4a2-7662-4366-a898-1357a5c21bad.png)

### 3D View:

![3dview](https://user-images.githubusercontent.com/75234946/234775963-1b46b871-5a80-4f46-a04b-cc45e2c5fdea.png)

### Result:

Thus, a single sided PCB board for a single digit token number display system with buzzer is developed
