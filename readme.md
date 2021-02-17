# Test and study how FMAC works  

    ## **NUCLEO-G474RE_FMAC_Adaptive_FIR_AN5305** = first try  
    ## **NUCLEO-G474RE_FMAC_FIR_DMAToIT** = no activiry  
    ## **NUCLEO-G474RE_FMAC_FIR_PollingToIT** = modify to printout data after FMAC, added waveforms, added excel plot and analysis

### 2021-02-05  
    Added this readme

### 2021-02-06  
    Added waveforms on the duration of each codes  
	
### 2021-02-17  
	Tests are done on **NUCLEO-G474RE_FMAC_FIR_PollingToIT**  
	Use HSE instead of HSI  
    Use _aCalculatedFilteredData1_ and _aCalculatedFilteredData1_ and append data  
	Offset the signal so all of it are positive and no negative before feeding to the FMAC  
	changed GAIN to 0, GAIN = 1  
	Filter using _Low Pass_ and _High Pass_
	Exported to excel and graphs
	
	