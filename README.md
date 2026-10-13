[![DOI](https://img.shields.io/badge/DOI-10.82901%2Fnemar.nm000463-blue)](https://doi.org/10.82901/nemar.nm000463)

# Network dynamics of HFOs (Pennsieve 280): HFO and background iEEG snippets, derivative BIDS-iEEG

This is a **derivative** dataset. It repackages "Network dynamics of HFOs" by Jack Lin and William C. Stacey on Pennsieve Discover
(dataset 280 version 1, doi:10.26275/2yv6-g6vh, Stacey Lab, University of Michigan; README title "Epileptic High Frequency
Oscillation EEG with Network Analysis"). The release README cites the manuscript "Network dynamics of interictal High Frequency
Oscillations predict surgical outcome within the clinical workflow in refractory epilepsy" (then under submission); it was published
as Lin J, Smith GC, Gliske SV, Zochowski M, Shedden K, Stacey WC. "High frequency oscillation network dynamics predict outcome in
non-palliative epilepsy surgery", Brain Communications 2024;6(1):fcae032, doi:10.1093/braincomms/fcae032 (same code repository
https://github.com/J4KLin/HFO-Network; its Table 1 HFO counts, 216,041 and 441,168, equal the HFO tables of this release). The
article's data statement names a copy of the two patients' data on University of Michigan Deep Blue Data (doi:10.7302/n9rt-sc45).

Two patients who had resective surgery: UMHS-0028 (good outcome) and UMHS-0030 (poor outcome). The raw long-term recordings of
UMHS-0028 are in NEMAR nm000444 (Michigan high-resolution iEEG, same subject label). No continuous recordings are included here.

## Contents

- `sub-<label>/ieeg/sub-<label>_task-hfo_acq-elecNN_ieeg.vhdr` (153 runs: 53 UMHS0028, 100 UMHS0030): one run
  per released file `UMHS-xxxx-elecNN.mat`, i.e. up to 500 snippets around HFOs detected on electrode NN, showing **all** channels.
  Each snippet is 1441 samples at 3600 Hz (the file's `FS` variable; PatientInfo.fs gives the recording rate, 4096 Hz). The snippets
  are concatenated in release order; `events.tsv` has one row per snippet (onset, `snippet`, `hfo_index` into the released HFO table
  and the released per-HFO metadata: start/stop time, detection channel, day, session, sleep stage, ictal state, quality flags).
  Each run has the 80-500 Hz filtered signal of every channel and, as channels `<name>_rms` (type MISC), the RMS envelope.
  For 74549/74549 HFO snippets the detection channel (`hfo_stdChanI`) equals the file's electrode of interest (`elecROI`).
- `sub-<label>/ieeg/sub-<label>_task-background_ieeg.vhdr`: the 500 background (non-HFO) snippets per patient from
  `Data/BKGEEG/UMHS-xxxx.mat`, same layout; events give the released day number and sample interval of each snippet.
- Channel names: UMHS0028: labels/types from NEMAR nm000444 (sub-UMHS0028/ses-0002/ieeg/sub-UMHS0028_ses-0002_task-ltm_acq-day05_channels.tsv) indexed by Electrodes.stdEEGChanIdx; verified: the released SOZ mask maps exactly onto nm000444's soz channels ['AD3', 'AD4', 'AD5', 'AD6', 'AP1']. UMHS0030: E### = Electrodes.stdEEGChanIdx (channel labels not in the release); type MISC (grid/strip/depth not stated per channel).
- `sub-<label>/ieeg/sub-<label>_electrodes.tsv`: `PatientInfo.Electrodes.sejin3DCoords` (origCoords as x/y/z, avgCoords as x_avg/y_avg/z_avg;
  space and units not stated, coordinate system `Other`), SOZ, resected-volume and remaining-contact masks.
- `participants.tsv`: sex, age, ILAE class, seizure focus, pathology and SOZ resection from Lin et al. 2024 Table 1, and the released
  PatientInfo fields (ILAE/outcome as released: 1 and 3; Table 1 gives ILAE 1 and 5).
- `sourcedata/pennsieve-280-v1/`: every released file: the 153 HFO `.mat` files, `data.zip` stored expanded under
  `files/data_zip_expanded/Data/` (BKGEEG, CombinedData/combinedPatientData.mat with the centrality and HFO-rate tables,
  PatientData/UMHS-xxxx.mat, README.txt; CRC-32 of every member verified, `ZIP_MANIFEST.json`), Pennsieve manifest/readme.
  `SOURCE_MANIFEST.json` lists the original SHA-256 of every file. Files are byte-identical to the release except MAT-file header
  creation dates, which were set to day 01 (weekday/time removed, same length).

Signal values are stored as IEEE float32 (source float64; max relative difference 5.95e-08); round trip checked (the written float32
values are identical to the source values cast to float32, for every run). Amplitude units are not stated in the release (units n/a).
Total snippet time: 8.4 h.

## Privacy

All files were scanned (text, MAT strings and headers, HDF5 strings) for names, initials, record numbers, full dates and ages above
89. Patient codes (UMHS-0028, UMHS-0030) are pseudonyms of the public Michigan database. Times are relative (day/session numbers, no
calendar dates). The release README's dataset date and contact e-mail are record metadata and were kept. Key status: destroyed.

## Licence

CC-BY-SA-4.0, as on the source record (Pennsieve: "Creative Commons Attribution - ShareAlike"; DataCite rightsList: Creative Commons
Attribution Share Alike 4.0 International, cc-by-sa-4.0).

## Ethics

Verbatim from the article (Lin et al. 2024, Materials and methods): "All patient data used in this study are approved by the local
Institutional Review Board with written patient consent to share and use their de-identified information."
