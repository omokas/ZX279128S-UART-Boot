
# zx279128s UART Boot

This project is aimed at reverse engineering the boot modes of zx279128s CPU used by recent ZTE routers and repeaters and goes through details of how UART boot works with this CPU and possible uses.




## Boot Modes


<img width="862" height="819" alt="uart_boot_datasheet" src="https://github.com/user-attachments/assets/ecadc7e7-dad0-45ee-af24-468945b435a3" />



From the datasheet we can see that **SSP0_FS0** and **SSP0_TXD** lines are responsible for setting **STRAP_BOOT_MODE1** and **STRAP_BOOT_MODE0** bits respectively.


| Boot Mode  | STRAP_BOOT_MODE1 | STRAP_BOOT_MODE0 |
| ---------- | ---------------- | ---------------- |
| UART Boot  | 0                | 0                |
| NAND Flash | 0                | 1                |
|  SPI NOR   | 1                | 0                |
|  SPI NAND  | 1                | 1                |

## UART Boot example - H3601P (Vodafone GR)

This device is equipped with a **TSSOP48 NAND FLash S34ML01G200TF100** so the **STRAP_BOOT_MODE1** has been set to **0** and **STRAP_BOOT_MODE0** has been set to **1**. 

<img width="612" height="720" alt="STRAP_BOOT_MODE1_resized" src="https://github.com/user-attachments/assets/8e12de56-fb22-4755-beb0-727550868081" />
<img width="612" height="720" alt="STRAP_BOOT_MODE0_resized" src="https://github.com/user-attachments/assets/c25597ec-b768-4479-8be2-cd098c4588b1" />


The modification that needs to be done is change **STRAP_BOOT_MODE0** from **1** to **0**



## UART Boot example - H3621P (PPC GR)

This device is equipped with a **SPI NAND Flash HeYangTek HYF1GQ4UTACAE** so both **STRAP_BOOT_MODE1** and **STRAP_BOOT_MODE0** has been set to **1**.

<img width="612" height="720" alt="UARTBOOT1" src="https://github.com/user-attachments/assets/802c61ac-d8df-42b8-86b0-8fcf48da9b5e" />
<img width="612" height="720" alt="UARTBOOT2" src="https://github.com/user-attachments/assets/637c933c-fbbc-41f7-9eb9-a26b1d799623" />


The modification that needs to be done is change both **STRAP_BOOT_MODE1** and **STRAP_BOOT_MODE0** from **1** to **0**
