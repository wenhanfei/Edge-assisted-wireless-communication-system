# Edge-assisted-wireless-communication-system

## Introduction

*H. Wen, J. Yu, G. Pan, X. Chen, S. Zhang and S. Xu. A Hybrid CNN-LSTM Architecture for High Accurate Edge-Assisted Bandwidth Prediction, Submitted to IEEE Wireless Communications Letters.*  

  This is the Github repository for the detailed introduction of the experimental environment and data acquisition process of this letter. The main purpose of the repository is to demonstrate our edge-assisted wireless communication system, discuss and report issues. This demo shows the architecture of the system and the process of acquiring data. All data in this letter are collected by ourselves through this system.
  
  ## Experimental environment
  Our proposed prediction scheme is tested on our OpenAirInterface (OAI) based prototype platform, which consists of software defined evolved packet core (EPC) and RAN using OAI, MEC platform, RF front-end using USRP B210, and commercial UEs, as shown in the following figure. OAI deployment is all in one mode, i.e., the EPC and RAN are deployed in one mini PC. 
  
  The system can interconnect with commercial UEs and provide them with a cellular network for data transmission. We can obtain bandwidth-related RAN information from the RAN side through the MEC server and generate a dataset.
  
  <img src="https://github.com/wenhanfei/Edge-assisted-wireless-communication-system/blob/main/Experimental Environment.PNG"  alt="Environment">
  
  The details of hardware and software configurations are listed in the following table.
  
  Component |Hardware|Software|
  ----|----|----|
  RAN/eNB|Intel i7-8559U|OpenAirInterface (OAI)|
  EPC|Intel i7-8559U|Openair-cn|
  MEC server|Intel i7-8559U|Edgegallery|
  Radio Frequency Front-End|Ettus USRP B210|N/A|
  UEs|6×Huawei Nexus 6P|Android 8.0|

  
  ## Data Collection
  we collect datasets under the following three different transmission conditions based on the edge-assisted wireless communication system.
  ### Configuration Cases
  * Low load: Each UE’s service is set to play live video with the bitrate of 1 M. 
  * High load: Each UE’s service is set to play live video with the bitrate of 15 M.
  * Random load: Each UE’s service is set to play DASH adaptive video stream (adaptive switching between 1 M, 3 M, 5 M, 8 M, 15 M and 20 M).
  
  ### Process 
  
  To generate datasets for different wireless environments, we have done the following implementation work. 
  * Firstly, we open the OAI system, including eNB and EPC (three core network elements, i.e., MME, HSS and SPGW). 
  * Secondly, we switch the commercial UEs from airplane mode to non-airplane mode. The UEs are connected to the cellular network as shown in the figure below.
  * Thirdly, the services of the UEs are set to play live video. The bitrate of live video refers to the above configuration cases.
  * Fourthly, the MEC server collects the RAN information through the flexRAN feedback during the $t$-th transmission period and saves them to the dataset according to a certain format. e.g., $$\sigma^{RP}_{i}(t)$,$\sigma^{RP}_{i}(t)$,$sigma^{RQ}_{i}(t)$,$\sigma^{CQI}_{i}(t)$,$N^{PRB}_{i}(t)$$
   The details of RAN information are listed in the following table.
  
 RAN information |Meaning of RAN information|
  ----|----|
  $\sigma^{RP}_{i}(t)$|the reference signal received power (RSRP) for the $i$-th user at the time index $(t)$|
  $\sigma^{RQ}_{i}(t)$|the reference signal received quality (RSRQ) for the $i$-th user at the time index $(t)$|
  $\sigma^{CQI}_{i}(t)$|the channel quality indicator (CQI) for the $i$-th user at the time index $(t)$|
  $N^{PRB}_{i}(t)$|the number of allocated PRBs for the $i$-th user at the time index $(t)$|

   <img src="https://github.com/wenhanfei/Edge-assisted-wireless-communication-system/blob/main/UE connected to cellular network illustration.PNG"  alt="illustration">


  
