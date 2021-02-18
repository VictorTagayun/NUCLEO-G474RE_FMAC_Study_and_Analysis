# Test and study how FMAC works  
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
 * Use _aCalculatedFilteredData1_ and _aCalculatedFilteredData1_ and append data  
 * Offset the signal so all of it are positive and no negative before feeding to the FMAC  
 * changed GAIN to 0, GAIN = 1  
 * Filter using _Low Pass_ and _High Pass_
 * Exported to excel and graphs

### 2021-02-18  
 * uploaded excel waveforms

## Excel waveforms  

* ### Initially worked on orig data AC Int input then converted to Float  

  Input conveted to Float  
  ![Input conveted to float](https://raw.githubusercontent.com/VictorTagayun/NUCLEO-G474RE_FMAC_Study_and_Analysis/main/NUCLEO-G474RE_FMAC_FIR_PollingToIT/captured_data%26plot/no_offset_Float_Input.png)  
  
  Input FFT using excel and some arbitrary sampling rate  
  ![Input FFT ](https://raw.githubusercontent.com/VictorTagayun/NUCLEO-G474RE_FMAC_Study_and_Analysis/main/NUCLEO-G474RE_FMAC_FIR_PollingToIT/captured_data%26plot/no_offset_Float_Input_FFT.png)  
  
  Low pass filter output  
  ![Low pass filter output](https://raw.githubusercontent.com/VictorTagayun/NUCLEO-G474RE_FMAC_Study_and_Analysis/main/NUCLEO-G474RE_FMAC_FIR_PollingToIT/captured_data%26plot/no_offset_Float_LPF_output.png)  
  
  Low pass filter coeffs  
  ![Low pass filter coeffs](https://raw.githubusercontent.com/VictorTagayun/NUCLEO-G474RE_FMAC_Study_and_Analysis/main/NUCLEO-G474RE_FMAC_FIR_PollingToIT/captured_data%26plot/no_offset_Float_LPF_coeffs.png)  
  
  High pass filter output  
  ![High pass filter output](https://raw.githubusercontent.com/VictorTagayun/NUCLEO-G474RE_FMAC_Study_and_Analysis/main/NUCLEO-G474RE_FMAC_FIR_PollingToIT/captured_data%26plot/no_offset_Float_HPF_output.png)  
  
  High pass filter coeffs  
  ![High pass filter coeffs](https://raw.githubusercontent.com/VictorTagayun/NUCLEO-G474RE_FMAC_Study_and_Analysis/main/NUCLEO-G474RE_FMAC_FIR_PollingToIT/captured_data%26plot/no_offset_Float_HPF_coeffs.png)  
  
  Very low pass filter  
  ![Very low pass filter](https://github.com/VictorTagayun/NUCLEO-G474RE_FMAC_Study_and_Analysis/blob/main/NUCLEO-G474RE_FMAC_FIR_PollingToIT/captured_data%26plot/no_offset_Float_VLPF_output.png)
  
  Very low pass filter coeffs  
  ![Very low pass filter coeffs](https://raw.githubusercontent.com/VictorTagayun/NUCLEO-G474RE_FMAC_Study_and_Analysis/main/NUCLEO-G474RE_FMAC_FIR_PollingToIT/captured_data%26plot/no_offset_Float_VLPF_coeffs.png)  
  
* ### Now we add DC offset to simulate input going to the ADC pin like a voltage feedback where input is only positive  

  Input Int w/ offset  
  ![Input int w/ offset](https://github.com/VictorTagayun/NUCLEO-G474RE_FMAC_Study_and_Analysis/blob/main/NUCLEO-G474RE_FMAC_FIR_PollingToIT/captured_data&plot/DC_offset_Int_Input.png?raw=true)  
  
  Low pass filter output  
  ![](https://github.com/VictorTagayun/NUCLEO-G474RE_FMAC_Study_and_Analysis/blob/main/NUCLEO-G474RE_FMAC_FIR_PollingToIT/captured_data&plot/DC_offset_Int_LPF_output.png?raw=true)
  
  Low pass filter output calculated FFT using excel  
  ![](https://github.com/VictorTagayun/NUCLEO-G474RE_FMAC_Study_and_Analysis/blob/main/NUCLEO-G474RE_FMAC_FIR_PollingToIT/captured_data%26plot/DC_offset_Int_LPF_output_FFT.png)
  
  Low pass filter coeffs  
  ![](https://github.com/VictorTagayun/NUCLEO-G474RE_FMAC_Study_and_Analysis/blob/main/NUCLEO-G474RE_FMAC_FIR_PollingToIT/captured_data%26plot/DC_offset_Int_LPF_coeffs.png)
  
  High pass filter output  
  ![](https://github.com/VictorTagayun/NUCLEO-G474RE_FMAC_Study_and_Analysis/blob/main/NUCLEO-G474RE_FMAC_FIR_PollingToIT/captured_data%26plot/DC_offset_Int_HPF_output.png)
  
  High pass filter output calculated FFT using excel  
  ![](https://github.com/VictorTagayun/NUCLEO-G474RE_FMAC_Study_and_Analysis/blob/main/NUCLEO-G474RE_FMAC_FIR_PollingToIT/captured_data%26plot/DC_offset_Int_HPF_output_FFT.png)
  
  High pass filter coeffs  
  ![](https://github.com/VictorTagayun/NUCLEO-G474RE_FMAC_Study_and_Analysis/blob/main/NUCLEO-G474RE_FMAC_FIR_PollingToIT/captured_data%26plot/DC_offset_Int_HPF_coeffs.png)
  
  
