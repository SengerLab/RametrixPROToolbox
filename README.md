# RametrixPROToolbox
The RametrixTM PRO Toolbox v1.0 for MATLAB

Latest update: March 24, 2019

Please cite: Senger RS, Robjertson JL (2019) The RametrixTM PRO Toolbox v1.0 for MATLAB®. Submitted to PeerJ Computational Sciences

The dataset analyzed in the above article is available here.

The RametrixTM PRO Toolbox v1.0 first requires PCA and DAPC models created by the RametrixTM LITE Toolbox. i.e., the RametrixTM LITE Toolbox must be run before the RametrixTM PRO Toolbox.

The RametrixTM LITE Toolbox is located at: https://github.com/SengerLab/RametrixLITEToolbox

Installation Instructions:

MATLAB R2016a or later is required. Download the 'Rametrix(TM) PRO Toolbox v1.0.mtlbx' file from this GitHub site and move it to the desired location in your file system. Double-click the .mtlbx file to start MATLAB and open the install dialog box. Click 'Install'. 
Functions (described below) are run from the Command Window in MATLAB. An example using the RametrixTM PRO Toolbox v1.0 with the included dataset is also described below.

The RametrixTM PRO Toolbox v1.0 contains two functions:

Function 1: LeaveOneOut.m

This function performs a leave-one-out validation of DAPC models created by the RametrixTM LITE Toolbox.  It is called as a function in the command window using the following command:

Results = LeaveOneOut(keystone, whichfactor, numberofpcs, positive_label, whichspectraset, AdditionalExclusions)

keystone: created by the RametrixTM LITE Toolbox. i.e., type 'keystone' (without quotes) here.

whichfactor: specifies the factor to be examined. This is the number of the column in keystone.RDAModel.Factors. i.e., a numerical value

numberofpcs: the number of PCs to be included in the DAPC model. i.e., a numerical value

positive_label: the title of the positive treatment samples. This must appear exactly as it appears in keystone.RDAModel.Factors. i.e., a label eclosed in quotes

whichspectraset: enter 1, 2, or 3.  1 = truncated spectra; 2 = baselined spectra; 3 = vector normalized spectra. i.e. a numerical value

AdditionalExclusions: enter spectra to be excluded from analysis. These are row numbers in keystone.RDAModel.Factors.  For no exclusions, 
enter [].

Results: an output table containing accuracy (percent predicted correctly); sensitivity (true positive rate); selectivity (true negative rate)


Function 2: RandomAccuracy.m

This function returns accuracy, sensitivity, and selectivity should leave-one-out predictions be assigned by random chance.  It is called as a function in the command window using the following command:

Results = RandomAccuracy(keystone, whichfactor, iterations)

keystone: created by the RametrixTM LITE Toolbox. i.e., type 'keystone' (without quotes) here.

whichfactor: specifies the factor to be examined. This is the number of the column in keystone.RDAModel.Factors. i.e., a numerical value

iterations: the number of iterations to perform. The suggested value here is 100,000. The larger the value, the more accurate the answer.

Results: Results: an output table containing accuracy (percent predicted correctly); sensitivity (true positive rate); selectivity (true negative rate)


Example: Using the included 'Healty Unhealthy Dataset (for RametrixTM LITE v1.1)'

Step 1: Download and unpack 'Healty Unhealthy Dataset (for RametrixTM LITE v1.1)' or 'Healty Unhealthy Dataset (for RametrixTM LITE v1.0)'

Step 2: In MATLAB, load this dataset using the RametrixTM LITE Toolbox v1.0 or v1.1 (see instructions with the RametrixTM LITE Toolbox on how to do this)

Step 3: In the Explore tab, average all spectra and select 'Baselined and Vector Normalized' using the default parameters

Step 4: In the PCA tab, select the factor 'Status' from the drop-down menu and select the 'Run PCA' button. This will generate PCA results.

Step 5: In the DAPC tab, input the number 6 into the 'Number of PCs included box' and select the 'Run DAPC' button. This will generate DAPC results.

Step 6: In the MATLAB Command Window, run the leave-one-out analysis for the DAPC model constructed with 6 PCs by executing the command: Results = LeaveOneOut(keystone, 7, 6, 'Unhealthy', 3, []);

The following results should be obtained: Accuracy = 0.993; Sensitivity = 1; Selectivity = 0.95

Step 7: Repeat the leave-one-out analysis for a DAPC model constructed with 100 PCs by executing the command: Results = LeaveOneOut(keystone, 7, 100, 'Unhealthy', 3, []);

The following results should be obtained: Accuracy = ; Sensitivity = ; Selectivity =

Step 8: Determine the random chance accuracy, sensitivity, and selectivity by executing the command: Results = RandomAccuracy(keystone, 7, 100000)

The following results should be obtained for both 'Healthy' and 'Unhealthy' factors: Random Accuracy = 0.5; Random Sensitivity = 0.5; Random Selectivity = 0.5
