Date: 10/24/22

Dataset Title: Epileptic High Frequency Oscillation EEG with Network Analysis 

Dataset Creators: Lin J & Stacey W

Dataset Contact: William Stacey, M.D., Ph.D. wstacey@umich.edu


Code repositiory for data processing scripts:
https://github.com/J4KLin/HFO-Network


Reserach Overview:
High frequency oscillation (HFO) has been known as a promising electrographic biomarker for epiletic tissue for decades.  To this end, we characterized HFO networks through functional connectivity analysis of clinical intracranial EEG data from patients who have undergone resective surgery (pre-processed EEG dataset provided for one good outcome Engel I and one poor outcome Engel III patient).  From the networks, we performed centrality analyses (results of which are also provided) to evaluate how HFO features can be used to predict patient outcome.


Software requirements: 
Matlab R2021a or above (other toolboxes may be required)


Instructions:
1. Unzip "Data.7z" file.
	/BKGEEG		- Preprocessed background (nonHFO) EEG data (.mat)
	/CombinedData	- Final centrality and hfo features for all patients (.mat)
	/HFOEEG		- Preprocessed HFO specific EEG data (.mat)
	/PatientData	- Patient level data (.mat)
	
2. Download and move all "UMHS-xxxx-elecxx.mat" files into the /HFOEEG folder.


Details on file contents:
/Data/BKGEEG/UMHS-xxxx.mat
- Background EEG data that is filtered (80-500 Hz) and smoothed (root mean square RMS)

/Data/HFOEEG/UMHS-xxxx-elecXX.mat
- Up to 500 samples of EEG data during which a HFO was detected on the specified electrode. Like background data this is also filtred and smoothed.

/Data/CombinedData/combinedPatientData.mat
- All centrality and HFO rate features for all patients. Includes critical resection percentage (CReP) and centrality ranks grouped into different percentiles for each electrode type.

/Data/PatientData/UMHS-xxxx.mat
- Patient level data including HFO information, electrode information, patient surgical outcome, and centrality.


Related publication(s):
Lin J, Zochowski M, Shedden K, Stacey W,
"Network dynamics of interictal High Frequency Oscillations predict surgical outcome within the clinical workflow in refractory epilepsy,"
Undergoing submission
