# HeavyWaterInc
Assessment for Heavy Water Inc
>> Execute .ipynb file to generate a pickle file.

1) Creating a virtual environment
When deploying to AWS Lambda, you need to upload a virtual environment that holds your code and dependencies. In your project folder, execute following commands. To avoid conflicts, you should not name your virtual environment the same as your project folder.
>>pip install virtualenv
>>virtualenv your_virtual_environment_name
2) To start your virtual environment:
>>source your_virtual_environment_name/bin/activate
3) Creating a Flask API



5) Creating predictions
Last but not least, we are ready to get some predictions. The predict method receives as argument the data sent to the API. You will need to add some code to process the data to match your model.
6) To run your application, you must create an environment variable to tell Flask which files to execute:
>>export FLASK_APP=predictions.py
8) You should make sure that your code is working locally before deploying it to AWS.

Install Flask then run the second command to start your application:

>>pip install flask
>>flask run
Open a terminal and test your predictions:

Type http://127.0.0.1:5000/html
and then test using the input

Deploying to AWS Lambda
Instead of manually creating and configuring AWS Lambda and the API Gateway, we’re going to use a library called Zappa.

Zappa makes it super easy to build and deploy all Python WSGI applications on AWS Lambda + API Gateway.
Important: Before deploying, make sure to configure your AWS credentials. For more info, visit: http://docs.aws.amazon.com/cli/latest/userguide/cli-chap-getting-started.html

In your virtual environment, install the required packages:

>>pip install zappa sklearn boto numpy scipy
    Then, initialize Zappa. When asked for an app function name, write down predictions.app. (or, the name of your Flask app + .app)

>>zappa init
              AWS Lambda requires your environment to have a maximum size of 50mb, but our packaged environment will be around 100mb. Lucky for us, it is possible for Lambda’s to load code from Amazon S3 without much performance loss (only a few milliseconds).To activate this feature, you must add a new line to your zappa_settings.json

"slim_handler": true
              You’re now ready to deploy. Use the deploy command with the name of the environment you’ve selected when initializing Zappa.

zappa deploy your-environment-name
              When completed, you will see your API URL in the last message. It will look like “https://abcdefg.execute-api.us-east-1.amazonaws.com/your-env-name”






