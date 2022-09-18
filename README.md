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
  * Low load: Each UE’s service is set to play live video with the bitrate of 1 M. 
  * High load: Each UE’s service is set to play live video with the bitrate of 15 M.
  * Random load: Each UE’s service is set to play DASH adaptive video stream (adaptive switching between 1 M, 3 M, 5 M, 8 M, 15 M and 20 M).
  
  ### Process 
  
  To generate datasets for different wireless environments, we have done the following implementation work. Firstly, we open the OAI system, including eNB and EPC (three core network elements, i.e., MME, HSS and SPGW). Secondly, we switch the commercial UEs from airplane mode to non-airplane mode. The UE are connected to the cellular network as shown in the figure below.
  
  <img src="https://github.com/wenhanfei/Edge-assisted-wireless-communication-system/blob/main/Illustration of UE connecting to cellular network.PNG"  alt="Environment">
  
