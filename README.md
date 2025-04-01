# PromptLocalModels
Prompt local models based on questions in an excel spreadsheet and store the response back to the spreadsheet in a new sheet...
This uses ollama to run three local models **deepseek-r1**, **llama3**, **mistral**. 

## Rough steps 

### Install the latest Python: 

https://www.python.org/downloads/

### Install Jupyter 

https://jupyter.org/install


### Download ollama

https://ollama.com/download

### Open the command line or terminal

ollama pull llama3.2
ollama pull mistral
ollama pull deepseek-r1

ollama serve 

ollama run llama3.2
ollama run mistral
ollama pull deepseek-r1

Ollama list 

### You should see output similar to this. 

NAME                  ID              SIZE      MODIFIED     
deepseek-r1:latest    0a8c26691023    4.7 GB    47 hours ago    
llama3:latest         365c0bd3c000    4.7 GB    47 hours ago    
mistral:latest        f974a74358d6    4.1 GB    47 hours ago  

### Run Jupyter 

jupyter notebook 

### I use google collab to connect to local Jupyter so I run as follows

jupyter notebook \           
  --NotebookApp.allow_origin='https://colab.research.google.com' \
  --port=8888 \
  --NotebookApp.port_retries=0 > a.txt. 2>&1 &

I then connect to the local Jupyter instance from google collab using the URL + Access key similar to this (from a.txt.) and by using "Connect to local runtime" connect option on the right side...

http://localhost:8888/tree?token=7de6375687ac1392a97c62ed4baa02c88083a791e882c567

### Create a spreadsheet my_prompts.xlsx

-Name the first sheet "Prompts" 
-Add a column "My Prompts"
-Enter a list of prompts (as many as you want) in the column 
-Save the spreadsheet


### Run the notebook 

-(Update the path of the spreadsheetor the name of the filename or columns if required in the notebook before running) 
-The code reads the spreadsheet into a pandas dataframe 
-It sends the prompts one at a time to each model and stores responses in the same dataframe 
-The data frame with the responses is written nback to the spreadsheet 
-The program will add a new sheet named "Model Responses" that has responses from the three models in various columns along with the prompts in the first column 
-The time to execute the notebook depends on the number of questions 
-Start with a small number of questions and see the time it takes before adding lots of questions
-Compare the responses and enjoy 

