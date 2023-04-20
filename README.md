## Lesion Mapper

T2 FLAIR lesion volume is an important biomarker in aging and pathophysiology. The purpose of this software is to provide an easily usable and openly accessible method for quantifying lesions from MR images that does not require manual adjustments or multiple contrasts. The tool is provided as a BIDS-app, which assumes that you have fmriprep derivatives for T1-weighted anatomical images, and a T2-FLAIR image organized according to BIDS structure.



### Acknowledgements

This tool is derived from https://github.com/mrfil/lesion-mapper. Please cite the following publication when using the tool:

Wetter, N. C., Hubbard, E. A., Motl, R. W., & Sutton, B. P. (2016). Fully automated open‐source lesion mapping of T2‐FLAIR images with FSL correlates with clinical disability in MS. Brain and Behavior, 6(3). https://doi.org/10.1002/brb3.440

For research purposes only! Please see LICENSE.txt

[Grace Clements](mailto:gracemc2@illinois.edu)
[Ben Zimmerman](mailto:bzimmerman@nunm.edu)
[Paul Camacho](mailto:pcamach2@illinois.edu)
[Nate Wetter](mailto:nwetter2@illinois.edu)  
[Brad Sutton](mailto:bsutton@illinois.edu)  
[Magnetic Resonance Functional Imaging Lab](http://mrfil.bioen.illinois.edu)  
[University of Illinois at Urbana-Champaign](https://illinois.edu)  

### Usage

The lesion-mapper app assumes that your T1-weighted anatomical and T2 FLAIR data is formatted according to BIDS. It also assumes that your T1-weighted data has been preprocessed with fmriprep.

The lesion-mapper app has the following command line arguments:

		usage: lesion-mapper bids_dir fmriprep_dir output_dir {participant,group}
		              	[--participant_label PARTICIPANT_LABEL [PARTICIPANT_LABEL ...]]
		              	[-midline INT]
				[-midmax INT]
				[-no2fast]
				[-v]
				[-png]
				[-h]




		positional arguments:

						bids_dir         
					The directory with the input dataset formatted
		                        according to the BIDS standard.

      			fmriprep_dir     
					The directory with the fmriprep (or equivalent) pre-processed derivatives.

      			output_dir       
					The directory where the output files should be stored.
		                        If you are running a group level analysis, this folder
		                        should be prepopulated with the results of
		                        the participant level analysis.

      			{participant,group}   
					Level of the analysis that will be performed. Multiple
		                        participant level analyses can be run independently
		                        (in parallel).

		optional arguments:

						--participant_label PARTICIPANT_LABEL [PARTICIPANT_LABEL ...]
		                        The label(s) of the participant(s) that should be
		                        analyzed. The label corresponds to
		                        sub-<participant_label> from the BIDS spec (so it does
		                        not include "sub-"). If this parameter is not provided
		                        all subjects will be analyzed. Multiple participants
		                        can be specified with a space separated list.
      			-midline            <int>
                            		Remove lesions that are within <int> millimeters of touching
                            		the saggital midline plane. Should be greater than or equal to zero.
                            		If set to zero, lesions crossing the midline will be removed.
                            		Default is 4. Use -1 to skip this step.
                            		Will be skipped if -wmthr is skipped.
      			-midmax             <int>  
                            		Only remove parts of midline lesions that are within
                            		<int> mm of midline. Should be greater than or equal to -midline.
                            		Default is 9. Use -1 to skip this constraint and allow all lesions
                            		contiguous with those selected via -midline to be removed.
      			-no2fast
                            		Skip secondary fast step. Results should be more sensitive and less specific.
      			-v                    
                            		Verbose
      			-png
                            		Generate png image outputs
      			-h                    
                            		Show this help message and exit
