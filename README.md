# MountainCarVerification
Scripts for closed loop verification of mountain car with generated environmental models. this directory should be a child of the /verisig directory

# To run a single interval with printing: 
From the verisig directory, run the following: 

    ./verisig --flowstar-cmd=./flowstar/flowstar MountainCarVerification/SingleNoiseModel.xml MountainCarVerification/networks/Generator2x50_100_Decay1TestLoss1.035e-06.yml MountainCarVerification/networks/Contraster1x50_Decay5TestLoss47.74.yml MountainCarVerification/networks/CompositeRegressor3x20_20_20_Decay0.001TestLoss5.15e-06Composite.yml MountainCarVerification/networks/ControllerSigmoid16x16.yml

* The initial intervals can be specified in SingleNoiseModel.yml
* The second network specifies the noise type, and the x3 paramter in the .yml files corresponds to the noise parameter.
* Blur noise should be verifiable between [0, 0.3]
* Contrast noise should be verifiable between [0.3, 2]
# To run multiple intervals in parallel without printing: 

from the base MountainCarVerification directory, run the following: 

    python3 SingleNoise_multirunner.py -t blur -i 0.00025 -s -0.5 -n 1

* The -t parameter specifies the type (either contrast or blur)
* The -i parameter specifies the x1 interval size
* The -s parameter specifies the left side of the starting intervals
* The -n parameter specifies the number of cores/intervals execute
