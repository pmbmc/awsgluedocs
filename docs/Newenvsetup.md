#### Working with VENV

When working with pythin venv you will probably require specific libraries inside the venv

To activate the venv shell go to the venv folder

        example : /home/user/pycharmlocation/projectname/venv

You then need to run the activate from the venv directory

        source ./bin/activate
        
Now you will see (venv) to the left of your prompt indicating that you are in the venv
This allows you to use pip to install required libraries into your venv

For example: Install the aws boto3 library with pip install

        pip install boto3
        
