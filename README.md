# Edge-assisted-wireless-communication-system

## Introduction

*H. Wen, J. Yu, G. Pan, X. Chen, S. Zhang and S. Xu. A Hybrid CNN-LSTM Architecture for High Accurate Edge-Assisted Bandwidth Prediction, Submitted to IEEE Wireless Communications Letters.*  

  This is the Github repository for the detailed introduction of the experimental environment and data acquisition process of this letter. The main purpose of the repository is to demonstrate the built edge-assisted wireless communication system, discuss and report issues. This demo shows the architecture of the system and the process of acquiring data. All data in this letter are collected by ourselves through this system.
  
  ## Experimental environment
  Our proposed prediction scheme is tested on our OpenAirInterface (OAI) based prototype platform, which consists of software-defined EPC, RAN, radio frequency front-end (i.e., USRP), MEC server, and several commercial UEs, as shown in the following figure. The EPC and RAN are all in one mini PC. 
  
  Component |Hardware|Software|
  ----|----|----|
  RAN/eNB|Intel i7-8559U|OpenAirInterface (OAI)|
  EPC|Intel i7-8559U|Openair-cn|
  MEC server|Intel i7-8559U|Edgegallery|
  Radio Frequency Front-End|Ettus USRP B210|N/A|
  UEs|6×Huawei Nexus 6P|Android 8.0|

  
  <img src="https://github.com/wenhanfei/Edge-assisted-wireless-communication-system/blob/main/Experimental Environment.PNG"  alt="Environment">
  
  ## Data Collection
  
