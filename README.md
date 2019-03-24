# RametrixPROToolbox
The RametrixTM PRO Toolbox v1.0 for MATLAB

Please cite: Senger RS, Robjertson JL (2019) The RametrixTM PRO Toolbox v1.0 for MATLAB®. Submitted to PeerJ Computational Sciences

The RametrixTM PRO Toolbox v1.0 first requires PCA and DAPC models created by the RametrixTM LITE Toolbox. i.e., the RametrixTM LITE Toolbox must be run before the RametrixTM PRO Toolbox.

The RametrixTM LITE Toolbox is located at: https://github.com/SengerLab/RametrixLITEToolbox

The RametrixTM PRO Toolbox v1.0 contains two functions:

Function 1: LeaveOneOut.m
This function performs a leave-one-out validation of DAPC models created by the RametrixTM LITE Toolbox.  It is called as a function in the command window using the following command:

Results = LeaveOneOut(keystone, whichfactor, numberofpcs, positive_label, whichspectraset, AdditionalExclusions)

keystone: created by the RametrixTM LITE Toolbox. i.e., type 'keystone' (without quotes) here.
whichfactor: specifies the factor to be examined. This is the number of the column in keystone.RDAModel.Factors. i.e., a numerical value
numberofpcs: the number of PCs to be included in the DAPC model. i.e., a numerical value
positive_label: the title of the positive treatment samples. This must appear exactly as it appears in keystone.RDAModel.Factors. i.e., a label eclosed in quotes
whichspectraset: enter 1, 2, or 3.  1 = truncated spectra; 2 = baselined spectra; 3 = vector normalized spectra. i.e. a numerical value
AdditionalExclusions: enter spectra to be excluded from analysis. These are row numbers in keystone.RDAModel.Factors.  For no exclusions, enter [].
Results: an output table containing accuracy (percent predicted correctly); sensitivity (true positive rate); selectivity (true negative rate)

Example: Results = LeaveOneOut(keystone, 40, 'Treated', 3, []); 

Function 2: RandomAccuracy.m
This function returns accuracy, sensitivity, and selectivity should leave-one-out predictions be assigned by random chance.  It is called as a function in the command window using the following command:

Results = RandomAccuracy(keystone, whichfactor, iterations)

keystone: created by the RametrixTM LITE Toolbox. i.e., type 'keystone' (without quotes) here.
whichfactor: specifies the factor to be examined. This is the number of the column in keystone.RDAModel.Factors. i.e., a numerical value
iterations: the number of iterations to perform. The suggested value here is 100,000. The larger the value, the more accurate the answer.
Results: Results: an output table containing accuracy (percent predicted correctly); sensitivity (true positive rate); selectivity (true negative rate)

Example: Results = RandomAccuracy(keystone, 12, 100000)
