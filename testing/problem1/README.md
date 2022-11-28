
# How to run the code

#### python3 task1.py --model_path ./model_checkpoint1 --input_data /path/to/testset/directory --output ./path/to/predictions/directory

--input_data argument contains the path to the directory of the hidden test set. 

--input_data expects the path of a root directory where multiple CSV files exist belonging to the test-set. Your script must parse this argument and be able to read all CSV files from this directory path. The format of the input is CSV (exactly the same as the pre-evaluation dataset).

--output argument defines the path to the directory where the predictions are to be dumped. Your scripts must parse this argument and be able to dump/save the output predictions (in CSV format) in the directory (specified by --output argument), corresponding to each input CSV file (with the same filename as that of the input CSV file). Individual output CSV files will contain TWO LABELS (separated with a comma) per line corresponding to each row in the input CSV. The first line of all the output CSV files must exactly be as "Slip, Crumple" referring to the two labels.

--model_path argument contains the path to the model checkpoint/dump that you have previously trained for this problem.


