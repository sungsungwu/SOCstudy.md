# SOCStudyJournal.md

study journal lab3

about this lab

![image](https://hackmd.io/_uploads/SJu_m5cvT.png)

此為我所設計之lab3架構

輸入(data)透過 AXI_S_Slave之protocol來接收並存進BRAM
Tap由AXI-Lite產生並存進BRAM

兩者相乘並相加，結果經累加後由AXI_S_Master輸出

------------------------------------------------
FSM

![image](https://hackmd.io/_uploads/HkmTT9qDa.png)
![image](https://hackmd.io/_uploads/rkS06c9Da.png)

![image](https://hackmd.io/_uploads/BkzSCqqwT.png)

此次Lab的FSM設計，分為AXI-Lite之read與write之state，AXI-S之protocol分為idle、輸入階段、計算與輸出。

------------------------------------------------
AXI-Lite raddr
![image](https://hackmd.io/_uploads/SyywL9cvp.png)

AXI-Lite之protocol如上圖所示

arvaild+arready-->read addr


因為read addr需等待arready來才開始接收，因此我令arvaild<=1
![image](https://hackmd.io/_uploads/ryPH5c9PT.png)

而關於arvaild，則是在read addr的階段才會拉為1

![image](https://hackmd.io/_uploads/Skd0q55DT.png)

------------------------------------------------

AXI-Lite rdata

rdata和raddr相似，rvaild+rready-->read data，而rdata則是需要等rvaild來才會read data，因此同理我直接將rready拉為1，rvaild則是rdata階段才會拉起來。

![image](https://hackmd.io/_uploads/r1EB2cqPT.png)


![image](https://hackmd.io/_uploads/SJtl25qDT.png)

------------------------------------------------
AXI-Lite wdata waddr

![image](https://hackmd.io/_uploads/rJxch5cva.png)

write之protocol和read類似，圖如下。

![image](https://hackmd.io/_uploads/BJzraqcv6.png)

![image](https://hackmd.io/_uploads/SyWUT5cP6.png)


------------------------------------------------

waveform

![image](https://hackmd.io/_uploads/BkYYeiqDp.png)

![image](https://hackmd.io/_uploads/B1hcls5vp.png)

![image](https://hackmd.io/_uploads/Skiigj5vp.png)

![image](https://hackmd.io/_uploads/H1Angicva.png)

圖中輸入與輸出信號皆有正確接收與輸出，計算部分也有計算正確。

------------------------------------------------


