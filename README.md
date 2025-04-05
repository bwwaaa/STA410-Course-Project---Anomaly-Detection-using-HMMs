# STA410-Course-Project---Anomaly-Detection-using-HMMs
This repository contains the files for a simulation of system log events and the usage of HMMs, log-likelihoods, and z-scores to detect anomalous behavior. This is a submission for STA410 (Statistical Computation) by Monica Di Gennaro. (Student number: 1006988556, utorid: digenna4)

## Files in this repository
The following files can be found in this repository:
- README.md: the in-depth description of what this project has to offer.
- main_simulation.py: the file with the entire functional code.
- test_hmm_simulation.py: the test file for main_simulation.py.
- visuals.py: a file with visual representations of the anomaly detections.
- main_simulation.ipynb: the .ipynb file of main_simulation.py.

# Overview of the project
## Simulating the System Logs
To simulate system logs the following steps were executed:
- Create fixed amount of normal and abnormal log events.
- Establish a System class that contains functions and attributes to create the base for the simulation.
- Use functions from the "random" library to simulate random actions occurring in system logs, this includes pauses between actions at random times, randomly executing between 10-30 actions, and randomly choosing which log events to perform.
- Use the SimPy library to establish the environment and run the simulation.

## Training the HMM
To train the HMM on the simulated events, the following steps were executed:
- Goal is to train the HMM only on normal sequences of events, so separate the abnormalities from the log events and store only the normal events of the simulation.
- Convert the normal system events into corresponding numbers for the HMM to learn from.
- Normalize the encoded values.
- Train the HMM (using the GuassianHMM function from the hmmlearn library) on the normalized encoded normal sequences.

## Scoring with Log-Likelihoods
Create scores from the HMM by using log-likelihoods. The higher (less negative) score means the user behavior is to be expected/normal, and much lower (very negative) scores mean the user behavior is abnormal. The following steps were executed:
- Convert all system events (normal and abnormal) into corresponding numbers.
- Normalize the encoded values.
- Calculate the log-likelihoods of the normalized values using the HMM.

## Detecting Anomalies using Log-Likelihoods and Z-scores
Calculate the z-scores of the log-likelihood scores to see how one user's sequence of events compares to the rest. If the z-score of a user was found to be < -1 then they are considered suspicious and are flagged. The following steps were executed:
- Calculate the mean and standard deviation of the log-likelihood scores.
- Calculate the z-score using this formula: z = (score - mean) / std
- If the z-score is < -1, print "SUSPICIOUS ACTIVITY DETECTED". 

  
