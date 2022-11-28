# ITU-ML5G-PS-010-AI_ML_SSD-BYOC-Build-your-own-Closed-loop
This repository contains the code and description of team AI_ML_SSD for 2022 ITU AI/ML in 5G Challenge. We identified 2 problems  based on the Low Latency Closed Loop between the haptic gloves and algorithms and the real robotic hand (Allegro Hand) using MEC (Multi Edge Computing).
##Slip Detection (and Force Estimation)
Given an object being held by an allegro hand, the object may tend to slip from the grip. Using ML models, our goal is to figure out if the object is slipping out of our hands and getting crumpled.  We take the time-series data of the Allegro hand, which includes the force and angle made by the Allegro hand's sixteen actuators with the object, as well as the mass and shape of the object. The values of slip and crumple can either be zero, which means the object is not slipping or crumpling. If the value is one, this means the object is slipping or crumpling. This output is provided for every instance of the given data. If an ML model can predict if the object is slipping and crumpling for every instance, then we can change the force and angle accordingly and make the hand balance the object. For the time being, the use case is to detect slip and crumple. Later, this approach can be extended to changing the force and angle to control the hand so the object is not slipping or crumpling using ML. Slip and crumple detection is very useful for many tasks. For example, if a wire is being connected remotely using the allegro hand, it may slip if not enough force is used to grip it, and if too much force is used, the object will be deformed, etc. The same things can be considered when performing an operation remotely.
 
##Object Detection
The object is currently held by an Allegro hand. Our aim is to predict the shape of the object from 13 different shapes using an ML model. So, the ML model is given the force and angle that the object has on the sixteen actuators of the Allegro hand, as well as the mass of the object. The shape of the object could be a sphere, cube, or cuboid with different dimensions. This is very helpful because if the allegro hand can figure out the shape of the object, it can easily grab it just right.




# Dataset
For dataset visit https://bhartischool.iitd.ac.in/build_a_thon/index.html and download the training dataset for problem statement 1 and 2.
# Description of the Files

- task1.py, this script contains the code that reads the test set  and predicts the specified output for Task Problem Statement I: Slip Detection and Force Estimation in CSV format (one per line). The format of test set will be same as pre-evaluation dataset (i.e., the path will be the root folder containing all CSV files in the testset)

- task2.py, this script contains the code that reads the test set and predicts the specified output for Task Problem Statement II: Object Detection in CSV format (one per line). A sample output is here. The format of test set will be same as pre-evaluation dataset (i.e., the path will be the complete path to ONE AND ONLY CSV file in the testset)

-requirements.txt, this contains the requirements to load the dependent modules for your scripts.

 - task1_training.py, this script contains the code to read a train set and train a model with the data that must be saved/dumped as ./model_checkpoint_task1
 
 - task2_training.py, this script contains the code to read a train set and train a model with the data that must be saved/dumped as ./model_checkpoint_task2
 
 - model_checkpoint1
 - model_checkpoint2

# How to run the files 

#### python3 task1.py --model_path ./model_checkpoint1 --input_data /path/to/testset/directory --output ./path/to/predictions/directory

--input_data argument contains the path to the directory of the hidden test set. 

--input_data expects the path of a root directory where multiple CSV files exist belonging to the test-set. Your script must parse this argument and be able to read all CSV files from this directory path. The format of the input is CSV (exactly the same as the pre-evaluation dataset).

--output argument defines the path to the directory where the predictions are to be dumped. Your scripts must parse this argument and be able to dump/save the output predictions (in CSV format) in the directory (specified by --output argument), corresponding to each input CSV file (with the same filename as that of the input CSV file). Individual output CSV files will contain TWO LABELS (separated with a comma) per line corresponding to each row in the input CSV. The first line of all the output CSV files must exactly be as "Slip, Crumple" referring to the two labels.

--model_path argument contains the path to the model checkpoint/dump that you have previously trained for this problem.



#### python3 task1_training.py --model_path ./model_checkpoint1 --input_data ./path/to/trainset/directory

--input_data argument contains the path to the directory of the training set. 

--input_data expects the path of a root directory containing multiple CSV files belonging to the training set. Your script must parse this argument and be able to read CSV files from this path. The format of the input is (exactly the same as training dataset)

--model_path argument contains the path where the model checkpoint will be dumped.



#### python3 task2.py --model_path ./model_checkpoint2 --input_data ./path/to/testset.csv --output ./predictions_task2.csv

--input_data argument contains the end path to the hidden test set. 

--input_data expects the argument to be the complete path to the single CSV file representing the testset. Your script must parse this argument and be able to read input from this path. The format of the input is CSV (exactly the same as pre-evaluation dataset for this problem)

--output argument defines the path where the predictions are to be dumped in CSV format. Your scripts must parse this argument and be able to save the output prediction in CSV format - one prediction per line. The output CSV file will contain only ONE LABEL per line corresponding to each row in the input CSV. The first line of the output CSV file must exactly be as "Object_Held", referring to the label of the object.

--model_path argument contains the path to the model checkpoint/dump that you have previously trained for this problem.


#### python3 task2_training.py --model_path ./model_checkpoint2 --input_data ./path/to/trainset.csv

--input_data argument contains the path to the training set. Your script must parse this argument and be able to read input from this path. The format of the input is csv (exactly the same as training dataset)

--model_path argument contains the path where the model checkpoint will be dumped.

