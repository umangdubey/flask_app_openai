Initial Setup for Flask backend with openai

  ## Installing
  
  Start with cloning this repo
  
  ### [Optional - Recommended] Using a python venv environment
  
  Install and setup virtual environment
  ```
  python3 -m venv .venv
  ```
  
  To activate your virtualenv
  ```
  source ./venv/bin/activate
  ```

  To exit the virtual environment
  ```
  deactivate
  ```
  
  ### App setup

  Install the required dependencies
  ```
  pip install -r requirements.txt
  ```

  ## Running in local

  ### Environment variables

  Add the following environment variables for the app to work:
  
  | Variable | Description |
  |----------|-------------|
  |OPENAI_API_KEY|The OpenAI API key. [Generate here](https://openai.com/api/)|

  ### Debug mode

  ```
  python main.py
  ```

  ### Non-debug mode

  ```
  python app.py
  ```

## API Documentation

To check app health, go to `<server>:<port>/` or `<server>:<port>/isAlive`

  # PDF Summary

    Used to generate summary from text-based PDF file input
    
    **URL**: `/pdfSummary`
    
    **Method**: `POST`
    
    **Auth required**: NO
    
    **Input data format - Form data**
    
    enctype: 'multipart/form-data'
    
    ```
    input_file: [Text-based PDF file uploaded in the input]
    ```
    
    **Constraints**
    
    For the file being uploaded to the server, currently a limit of 1MB has been set as the max size. This can be configured during deployment in the code, and hence the max size is binding on the client. Any file larger than that will elicit an HTTP 413 response.
    
    **Data example**
    
    ```
    input_file: <great_depression.pdf>
    ```
    
    ## Success Response
    
    **Code**: `200 OK`
    
    **Content example**
    
    ```json
    {
        "input": "The Great Depression was a severe worldwide economic depression that took place mostly...",
        "message": "Request complete",
        "status": "200",
        "summary": "The Great Depression was a severe worldwide economic depression that took place..."
    }
    ```

  # Text Summary

Used to generate summary from text input

**URL**: `/summary`

**Method**: `POST`

**Auth required**: NO

**Input data format - Form data**

Content-Type: application/x-www-form-urlencoded

```
input: [input text to be summarized]
```

**Data example**

```
input: The Great Depression was a severe worldwide economic depression that took place mostly...
```

## Success Response

**Code**: `200 OK`

**Content example**

```json
{
    "input": "The Great Depression was a severe worldwide economic depression that took place mostly...",
    "message": "Request complete",
    "status": "200",
    "summary": "The Great Depression was a severe worldwide economic depression that took place..."
}
```
