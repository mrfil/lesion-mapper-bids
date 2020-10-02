## Lesion Mapper

T2 FLAIR lesion volume is an important biomarker in aging and pathophysiology. The purpose of this software is to provide an easily usable and openly accessible method for quantifying lesions from MR images that does not require manual adjustments or multiple contrasts. The tool is provided as a BIDS-app, which assumes that you have fmriprep derivatives for T1-weighted anatomical images, and a T2-FLAIR image organized according to BIDS structure. 



### Acknowledgements

lesion_mapper - A tool for mappping white matter hyperintensities. Publication at: Wetter, Hubbard, Motl, Sutton. Brain Behav. 2016 Jan 28;6(3):e00440. https://doi.org/10.1002/brb3.440

For research purposes only! Please see LICENSE.txt

Ben Zimmerman <bzimme5@illinois.edu>
Nate Wetter <nwetter2@illinois.edu>
Brad Sutton <bsutton@illinois.edu>
Magnetic Resonance Functional Imaging Lab <mrfil.bioen.illinois.edu>
University of Illinois at Urbana-Champaign <illinois.edu>

### Usage 
This version of lesion_mapper assumes that you 


lesion_mapper <bids_root> <fmriprep_dir> <out_dir> <analysis_level> <options>

Required parameters:
  -bids_root <dir> : This should be the root of the BIDS dataset
  -fmriprep_dir <dir>: This should be the root of the BIDS derivatives folder (by default this searches for bids_root/derivatives/fmriprep)
  -out_dir <dir>: This is the output directory
  -analysis_level: This is the processing stage (either "participant" or "group")

Options:
  --participant_label: The label(s) of the participant(s) that should be analyzed. The label corresponds to sub-<participant_label> from the BIDS spec (so it does not include    "sub-"). If this parameter is not provided all subjects will be analyzed. Multiple participants can be specified with a space separated list.
  -wmthr <float> : White matter propability threshold for standard space masking.
    Between 0 and 1. Higher numbers increase false negatives.
    Lower numbers increase false positives. Default is 0.7.
    Use -1 to skip this step.
  -midline <int> : Remove lesions that are within <int> millimeters of touching
    the saggital midline plane. Should be greater than or equal to zero.
    If set to zero, lesions crossing the midline will be removed.
    Default is 4. Use -1 to skip this step.
    Will be skipped if -wmthr is skipped.
  -midmax <int>  : Only remove parts of midline lesions that are within
    <int> mm of midline. Should be greater than or equal to -midline.
    Default is 9. Use -1 to skip this constraint and allow all lesions
    contiguous with those selected via -midline to be removed.
  -no2fast : Skip secondary fast step. Results should be more sensitive and
    less specific.
  -v             : Verbose.
  -png           : Generate png image outputs.
