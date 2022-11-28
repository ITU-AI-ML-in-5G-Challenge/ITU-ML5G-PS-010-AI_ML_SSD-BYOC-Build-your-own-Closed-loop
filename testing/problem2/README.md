# How to run the code





#### python3 task2.py --model_path ./model_checkpoint2 --input_data ./path/to/testset.csv --output ./predictions_task2.csv

--input_data argument contains the end path to the hidden test set. 

--input_data expects the argument to be the complete path to the single CSV file representing the testset. Your script must parse this argument and be able to read input from this path. The format of the input is CSV (exactly the same as pre-evaluation dataset for this problem)

--output argument defines the path where the predictions are to be dumped in CSV format. Your scripts must parse this argument and be able to save the output prediction in CSV format - one prediction per line. The output CSV file will contain only ONE LABEL per line corresponding to each row in the input CSV. The first line of the output CSV file must exactly be as "Object_Held", referring to the label of the object.

--model_path argument contains the path to the model checkpoint/dump that you have previously trained for this problem.



