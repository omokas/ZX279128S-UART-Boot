
# zx279128s UART Boot

This project is aimed at reverse engineering the boot modes of zx279128s CPU used by recent ZTE routers and repeaters and goes through details of how UART boot works with this CPU and possible uses.




## Boot Modes


<img width="560" height="532" alt="uart_boot_datasheet" src="https://github.com/user-attachments/assets/726b665d-a46b-4d12-9e48-165c8ace3dac" />



From the datasheet we can see that **SSP0_FS0** and **SSP0_TXD** lines are responsible for setting **STRAP_BOOT_MODE1** and **STRAP_BOOT_MODE0** bits respectively.


| Boot Mode  | STRAP_BOOT_MODE1 | STRAP_BOOT_MODE0 |
| ---------- | ---------------- | ---------------- |
| UART Boot  | 0                | 0                |
| NAND Flash | 0                | 1                |
|  SPI NOR   | 1                | 0                |
|  SPI NAND  | 1                | 1                |

## UART Boot example - H3601P (Vodafone GR)

This device is equipped with a **TSSOP48 NAND FLash S34ML01G200TF100** so the **STRAP_BOOT_MODE1** has been set to **0** and **STRAP_BOOT_MODE0** has been set to **1**. 

The modification that needs to be done is change **STRAP_BOOT_MODE0** from **1** to **0**

## UART Boot example - H3621P (PPC GR)

This device is equipped with a **SPI NAND Flash HeYangTek HYF1GQ4UTACAE** so both **STRAP_BOOT_MODE1** and **STRAP_BOOT_MODE0** has been set to **1**.

The modification that needs to be done is change both **STRAP_BOOT_MODE1** and **STRAP_BOOT_MODE0** from **1** to **0**
