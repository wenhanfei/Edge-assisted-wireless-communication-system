# Edge-assisted-wireless-communication-system

## Introduction

*H. Wen, J. Yu, G. Pan, X. Chen, S. Zhang and S. Xu. A Hybrid CNN-LSTM Architecture for High Accurate Edge-Assisted Bandwidth Prediction, Submitted to IEEE Wireless Communications Letters.*  

  This is the Github repository for the detailed introduction of the experimental environment and data acquisition process of this letter. The main purpose of the repository is to demonstrate our edge-assisted wireless communication system, discuss and report issues. This demo shows the architecture of the system and the process of acquiring data. All the experiments in the letter are based on the datasets collected on the prototype platform.
  
  ## Experimental environment
  Our proposed prediction scheme is tested on our OpenAirInterface (OAI) based prototype platform, which consists of software defined evolved packet core (EPC) and RAN using OAI, MEC platform, RF front-end using USRP B210, and commercial UEs, as shown in the following figure. OAI deployment is all in one mode, i.e., the EPC and RAN are deployed in one mini PC. 
  
  The system can interconnect with commercial UEs and provide them with a cellular network for data transmission. We can obtain bandwidth-related RAN information from the RAN side through the MEC server and generate datasets.
  
  <img src="https://github.com/wenhanfei/Edge-assisted-wireless-communication-system/blob/main/Fig. 1. Experimental environment.PNG"  alt="Environment">
  <p align="center">Fig. 1. The snapshot of the edge-assisted wireless communication system.</p>
  The details of hardware and software configurations are listed in the following table.
  <p align="center">Table I   Configurations of OAI-based Prototype Platform.</p>
  
  <div align="center">
  
  Component |Hardware|Software|
  ----|----|----|
  RAN/eNB|Intel i7-8559U|OpenAirInterface (OAI)|
  EPC|Intel i7-8559U|Openair-cn|
  MEC server|Intel i7-8559U|Edgegallery|
  Radio Frequency Front-End|Ettus USRP B210|N/A|
  UEs|6×Huawei Nexus 6P|Android 8.0|
  
  </div>
 

  
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
  * Fourthly, the MEC server collects the RAN information through the flexRAN feedback during the $t$-th transmission period and saves them to the dataset according to a certain format.  The details of RAN information are listed in the following table.


  <div align="center">
  
   <img src="https://github.com/wenhanfei/Edge-assisted-wireless-communication-system/blob/main/Fig. 2. UE connected to cellular network illustration.PNG"  alt="illustration">
  
   </div>
   
   <p align="center">Fig. 2. The snapshoot of UE connected to cellular network illustration.</p>
  
  <p align="center">Table II   The meaning of RAN information</p>
 <div align="center">
  
 RAN information |Meaning of RAN information|
  ----|----|
  $\sigma^{RP}_{i}(t)$|the reference signal received power (RSRP) for the $i$-th user at the time index $(t)$|
  $\sigma^{RQ}_{i}(t)$|the reference signal received quality (RSRQ) for the $i$-th user at the time index $(t)$|
  $\sigma^{CQI}_{i}(t)$|the channel quality indicator (CQI) for the $i$-th user at the time index $(t)$|
  $N^{PRB}_{i}(t)$|the number of allocated  physical resource blocks for the $i$-th user at the time index $(t)$|
 </div>
  
 The datasets collected through the above steps are used to train the bandwidth prediction models and tested on this edge-assisted wireless communication system.
 
 The data training process is performed on the MEC server with the Pytorch platform. When the offline training process is completed, the bandwidth prediction models are hosted on the MEC server. The proposed and baseline prediction schemes acquire RAN context measurement resultsof the previous M = 20 transmission periods, and predict the available bandwidth for the next transmission period.

### Experimental Results
We have shown the performance of the MLP-LSTM prediction scheme, and compared it with the proposed scheme in Fig. 3 and Table III.
We can observe from Fig. 3 that the performance of the MLP-LSTM is slightly worse than the proposed CNN-LSTM. 
As shown in Table III, the proposed CNN-LSTM outperforms the MLP-LSTM in terms of MAE, RMSE, $R^2$ and running time. MLP is a special case of CNN, and each neuron of MLP is connected to all nodes in the previous layer. Thus, its amount of parameters is larger, leading to a longer running time and worse convergence performance.

<img src="https://github.com/wenhanfei/Edge-assisted-wireless-communication-system/blob/main/Fig. 3. The predicted available bandwidth versus the ground-truth available bandwidth.png"  alt="Fig. 3. The predicted available bandwidth versus the ground-truth available bandwidth">

<p align="center">Fig. 3. The predicted available bandwidth versus the ground-truth available bandwidth.</p>

We also plot the CDF of the absolute prediction error of the MLP-LSTM scheme, as shown in Fig~4. The achievable median absolute
error of the proposed CNN-LSTM is 92.34 kbps, which is superior to the MLP-LSTM (153.38 kbps), corresponding to 39.8\% improvement.

<img src="https://github.com/wenhanfei/Edge-assisted-wireless-communication-system/blob/main/Fig. 4. CDF of absolute errors.png"  alt="Fig. 4. CDF of absolute errors">

<p align="center">Fig. 4. CDF of absolute errors for MLP-LSTM and CNN-LSTM prediction schemes.</p>
