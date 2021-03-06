# Test and study how FMAC (Filter Math ACcelerator) works  
 * **NUCLEO-G474RE_FMAC_Adaptive_FIR_AN5305** = first try but did not proceed, just print out data of 2 tones  
 * **NUCLEO-G474RE_FMAC_FIR_DMAToIT** = no activiry  
 * **NUCLEO-G474RE_FMAC_FIR_PollingToIT** = modify to printout data after FMAC, added waveforms, added excel plot and analysis

### 2021-02-05  
 * Added this readme

### 2021-02-06  
 * Added waveforms on the duration of each codes  
	
### 2021-02-17  
 * Tests are done on **NUCLEO-G474RE_FMAC_FIR_PollingToIT**  
 * Use HSE instead of HSI  
 * Use _aCalculatedFilteredData1_ and _aCalculatedFilteredData2_ and append data  
 * Offset the signal so all of it are positive and no negative before feeding to the FMAC  
 * changed GAIN to 0, GAIN = 1  
 * Filter using _Low Pass_ and _High Pass_
 * Exported to excel and graphs

### 2021-02-18  
 * uploaded excel waveforms  
 
### 2021-03-03  
 * Added Sine1k_15k from [NUCLEO-G474RE_2tonegenerator](https://github.com/VictorTagayun/NUCLEO-G474RE_DAC_DMA_LL-HAL_TIM6/blob/5ec467271cf4406628f2ed793f6c2472c98abc50/NUCLEO-G474RE_2tonegenerator/Core/Inc/waveforms.h#L9) and check if still can apply filter.

## Excel waveforms  

* ### Initially worked on original data of AC signal Integer input then converted to Float. This is not necessary as FMAC will process Q15

  Input conveted to Float
  
  ![Input conveted to float](https://raw.githubusercontent.com/VictorTagayun/NUCLEO-G474RE_FMAC_Study_and_Analysis/main/NUCLEO-G474RE_FMAC_FIR_PollingToIT/captured_data%26plot/no_offset_Float_Input.png)  
  
  Input FFT using excel and some arbitrary sampling rate  
  
  ![Input FFT ](https://raw.githubusercontent.com/VictorTagayun/NUCLEO-G474RE_FMAC_Study_and_Analysis/main/NUCLEO-G474RE_FMAC_FIR_PollingToIT/captured_data%26plot/no_offset_Float_Input_FFT.png)  
  
  Low pass filter coeffs  
  
  ![Low pass filter coeffs](https://raw.githubusercontent.com/VictorTagayun/NUCLEO-G474RE_FMAC_Study_and_Analysis/main/NUCLEO-G474RE_FMAC_FIR_PollingToIT/captured_data%26plot/no_offset_Float_LPF_coeffs.png)  

  Low pass filter output  
  
  ![Low pass filter output](https://raw.githubusercontent.com/VictorTagayun/NUCLEO-G474RE_FMAC_Study_and_Analysis/main/NUCLEO-G474RE_FMAC_FIR_PollingToIT/captured_data%26plot/no_offset_Float_LPF_output.png)  
  
  
  High pass filter coeffs  
  
  ![High pass filter coeffs](https://raw.githubusercontent.com/VictorTagayun/NUCLEO-G474RE_FMAC_Study_and_Analysis/main/NUCLEO-G474RE_FMAC_FIR_PollingToIT/captured_data%26plot/no_offset_Float_HPF_coeffs.png)  

  High pass filter output  
  
  ![High pass filter output](https://raw.githubusercontent.com/VictorTagayun/NUCLEO-G474RE_FMAC_Study_and_Analysis/main/NUCLEO-G474RE_FMAC_FIR_PollingToIT/captured_data%26plot/no_offset_Float_HPF_output.png)  
  
  
  Very low pass filter coeffs  
  
  ![Very low pass filter coeffs](https://raw.githubusercontent.com/VictorTagayun/NUCLEO-G474RE_FMAC_Study_and_Analysis/main/NUCLEO-G474RE_FMAC_FIR_PollingToIT/captured_data%26plot/no_offset_Float_VLPF_coeffs.png)  

  Very low pass filter  
  
  ![Very low pass filter](https://github.com/VictorTagayun/NUCLEO-G474RE_FMAC_Study_and_Analysis/blob/main/NUCLEO-G474RE_FMAC_FIR_PollingToIT/captured_data%26plot/no_offset_Float_VLPF_output.png)
  
  
* ### Now add DC offset to simulate input going to the ADC pin like a voltage feedback where input is only positive, These data are not converted to float and all are Q15  

  Input Integer w/ offset. Signals are 2 frequencies
  
  ![Input int w/ offset](https://github.com/VictorTagayun/NUCLEO-G474RE_FMAC_Study_and_Analysis/blob/main/NUCLEO-G474RE_FMAC_FIR_PollingToIT/captured_data&plot/DC_offset_Int_Input.png?raw=true)  
  

  Low pass filter coeffs  
  
  ![](https://github.com/VictorTagayun/NUCLEO-G474RE_FMAC_Study_and_Analysis/blob/main/NUCLEO-G474RE_FMAC_FIR_PollingToIT/captured_data%26plot/DC_offset_Int_LPF_coeffs.png)

  Low pass filter output, high frequency signal is removed  
  
  ![](https://github.com/VictorTagayun/NUCLEO-G474RE_FMAC_Study_and_Analysis/blob/main/NUCLEO-G474RE_FMAC_FIR_PollingToIT/captured_data&plot/DC_offset_Int_LPF_output.png?raw=true)

  Low pass filter output calculated FFT using excel  
  
  ![](https://github.com/VictorTagayun/NUCLEO-G474RE_FMAC_Study_and_Analysis/blob/main/NUCLEO-G474RE_FMAC_FIR_PollingToIT/captured_data%26plot/DC_offset_Int_LPF_output_FFT.png)
  

  High pass filter coeffs
  
  ![](https://github.com/VictorTagayun/NUCLEO-G474RE_FMAC_Study_and_Analysis/blob/main/NUCLEO-G474RE_FMAC_FIR_PollingToIT/captured_data%26plot/DC_offset_Int_HPF_coeffs.png)

  High pass filter output, low frequency signal is removed  
  
  ![](https://github.com/VictorTagayun/NUCLEO-G474RE_FMAC_Study_and_Analysis/blob/main/NUCLEO-G474RE_FMAC_FIR_PollingToIT/captured_data%26plot/DC_offset_Int_HPF_output.png)
  
  High pass filter output calculated FFT using excel 
  
  ![](https://github.com/VictorTagayun/NUCLEO-G474RE_FMAC_Study_and_Analysis/blob/main/NUCLEO-G474RE_FMAC_FIR_PollingToIT/captured_data%26plot/DC_offset_Int_HPF_output_FFT.png)
  
  
  Sine1k_15k input Line  
  
  ![](https://github.com/VictorTagayun/NUCLEO-G474RE_FMAC_Study_and_Analysis/blob/main/NUCLEO-G474RE_FMAC_FIR_PollingToIT/captured_data%26plot/Sine48_1k_15k_line.png)
  
  Sine1k_15k input Bar  
  
  ![](https://github.com/VictorTagayun/NUCLEO-G474RE_FMAC_Study_and_Analysis/blob/main/NUCLEO-G474RE_FMAC_FIR_PollingToIT/captured_data%26plot/Sine48_1k_15k_bar.png)

  Sine1k_15k output HPF  
  
  ![](https://github.com/VictorTagayun/NUCLEO-G474RE_FMAC_Study_and_Analysis/blob/main/NUCLEO-G474RE_FMAC_FIR_PollingToIT/captured_data%26plot/Sine48_1k_15k_output_HPF.png)

  Sine1k_15k output LPF  
  
  ![](https://github.com/VictorTagayun/NUCLEO-G474RE_FMAC_Study_and_Analysis/blob/main/NUCLEO-G474RE_FMAC_FIR_PollingToIT/captured_data%26plot/Sine48_1k_15k_output_LPF.png)


### Other References :

[STM32F429I-DISC1_FIR_FFT_wth_Print Project](https://github.com/VictorTagayun/STM32F429I-DISC1_CMSIS_DSP_Tutorial)

[CMSIS DSP](https://github.com/VictorTagayun/NUCLEO-G474RE_CMSIS_DSP_Tutorial)

[Use of FMAC for **Real Time** FIR/IIR Filter](https://github.com/VictorTagayun/NUCLEO-G474RE_RealTime_FIR_IIR_FMAC)


*Disclaimer:*
[Updated Disclaimer](https://github.com/VictorTagayun/GlobalDisclaimer)

*The projects posted here are for my Personal reference, learning and educational purposes only.*
*The purpose of a certain project may be for testing a module and may be just a part of a whole project.*
*It should not be used in a production or commercial environment.*
*Any cause of injury and/or death is the sole responsibility of the user.*