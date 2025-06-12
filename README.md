# ml-project-workflow

## Setup and Requirements
- Create folder for project
- open on vs code, in its terminal
- paste conda create -p venv python==3.8 -y (creating an env for the project)
- to activate it:
- conda activate venv/
- create a READEME.md
- connect github with the folder to commit codes
- start with git init
- create a gitigore in github repository then do git pull
- create a file for : setup.py
- requirements.txt
- then create src folder -> _init_.py file
- pip install -r requirements.txt
- commit in github 

## Loging and Exception
- create folders for:
- components,pipeline
- inside src create exception.py, logger.py, utils.py

### exception.py
```
import sys
import logging

def error_message_detail(error, error_detail: sys):
    """
    Returns a detailed error message with filename, line number, and error message.
    """
    _, _, exc_tb = error_detail.exc_info()
    file_name = exc_tb.tb_frame.f_code.co_filename
    error_message = f"Error occurred in python script: [{file_name}] at line number [{exc_tb.tb_lineno}] with message: [{str(error)}]"
    return error_message


class CustomException(Exception):
    def __init__(self, error_message, error_detail: sys):    
        super().__init__(error_message)
        self.error_message = error_message_detail(error_message, error_detail)

    def __str__(self):
        return self.error_message


```

### logger.py
```
import logging
import os
from datetime import datetime

LOG_FILE=f"{datetime.now().strftime ('%m _%d_%Y_%H_%M_%S')}.log" 
logs_path=os.path.join(os.getcwd(), "logs",LOG_FILE) 
os.makedirs(logs_path, exist_ok=True)

LOG_FILE_PATH=os.path. join(logs_path, LOG_FILE)

logging.basicConfig(
    filename=LOG_FILE_PATH,
    format= "[%(asctime)s]  %(lineno)d  %(name)s - %(levelname)s - %(message)s",
    level=logging.INFO,

)

```
