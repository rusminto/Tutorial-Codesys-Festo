# Tutorial Festo CPX-E-CEC-C1

## Persiapan
1. Unduh codesys ([Open Link](https://www.festo.com/net/en-gb_gb/SupportPortal/Downloads/648097/708369/CODESYS_V35SP12Patch6_pbF(ee4b68c69baf).zip))
2. Unduh Festo Field Device Tools ([Open Link](https://www.festo.com/net/et_ee/SupportPortal/Downloads/647947/711716/2021.05.18.1[FestoFieldDeviceTool2.10.4.46788].exe))
3. Unduh device yg sesuai (CPX-E-CEC-C1) ([Open Link](https://www.festo.com/net/en-gb_gb/SupportPortal/Default.aspx?tab=4&q=5226780)) :
   - Tekan __File and language versions__ di __Target Support Package CODESYS__
   - Pilih Version 3.5.12.224 (29.01.2020)
4. Jalankan file setup di dalam zip codesys
5. Install Festo Field Device Tools
6. Install CPX-E-CEC-C1 driver

## Membuat Project Baru
1. Hubungkan PLC dengan PC menggunakan kabel LAN
2. Buka Festo Field Device Tools, cek IP yg dipakai oleh PLC.  
![image](https://user-images.githubusercontent.com/43722553/124556876-0e6bb380-de63-11eb-9529-b4b720225080.png)
3. Pastikan IP PC terhubung pada jaringan yg sama dengan PLC (192.168.88.0/24).  
![image](https://user-images.githubusercontent.com/43722553/124556993-2cd1af00-de63-11eb-9cba-620430082327.png)
4. Buka Codesys
5. Pilih New Project
6. Pilih Empty Template
7. Pada Device Tree (Tab paling kiri), klik kiri pada project baru
8. Kemudian pilih __Add Device__
9. Pilih PLC > CPX-E-CEC-C1
10. Double Click di Device Tree (CPX-E-CEC-C1) dan tekan "Add Gateway" lalu OK.  
![image](https://user-images.githubusercontent.com/43722553/124691051-5fcc7f00-df05-11eb-90f9-3a50daa7530c.png)
11. Tekan Add Device, tunggu beberapa saat
12. Pada Device Tree (Tab paling kiri), klik kanan pada POU.  
![image](https://user-images.githubusercontent.com/43722553/124557578-df097680-de63-11eb-9c07-e6a302ce5585.png)
12. Pada Device Tree (Tab paling kiri), klik kanan pada Task.  
![image](https://user-images.githubusercontent.com/43722553/124557777-11b36f00-de64-11eb-8993-fe7074ff62eb.png)
13. Kemudian buka Tab POU, tuliskan source code berikut :   
![image](https://user-images.githubusercontent.com/43722553/124557901-3a3b6900-de64-11eb-9bef-440094ee5a17.png)
14. Lalu tekan tombol login untuk menghubungkan source code dengan PLC.  
![image](https://user-images.githubusercontent.com/43722553/124557998-57703780-de64-11eb-9899-240cef54af85.png)
16. Untuk menyimpan program ke PLC saat booting dapat dengan menekan __Craete Boot Application__.  
![image](https://user-images.githubusercontent.com/43722553/124558187-871f3f80-de64-11eb-87ba-fe376a98f6b1.png)
18. Supaya source code dapat diambil dari PLC dapat menekan __Source download to connected device__ (hanya bisa di-run ketika sudah login)


# Main Project

## Common configuration
```
	+-----------+           +-----------+
	|    PLC    | <-------- |    PC     |
	|           | --------> | (CODESYS) |
	+-----------+           +-----------+

	PLC directly connected to PC, which a compiler had been installed
```

## Trial configuration
```
	+-----------+           +-----------+           +-----------+
	|    PLC    | <-------- |  Capture  | <-------- |    PC     |
	|           | --------> |  Device   | --------> | (CODESYS) |
	+-----------+           +-----------+           +-----------+

	- Capture device forwards packet from PC->PLC or PLC->PC
```


## Desired Result
### Capture data from PLC
```
	+-----------+           +-----------+
	|  Capture  | <-------- |    PC     |
	|  Device   | --------> | (CODESYS) |
	+-----------+           +-----------+

	- Capturing binary sent from PC and save it as file
	- Capture device can be recognized as PLC if PC scans the network
```

### Download compiled binary to PLC from Remote PC
```
	+-----------+           +-----------+
	|    PLC    | <-------- |   Remote  |
	|           | --------> |     PC    |
	+-----------+           +-----------+

	captured binary file is saved in Remote PC
```


#### Notes
	- CODESYS : IDE & PLC Code compiler
