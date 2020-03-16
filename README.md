# aws-lambda-and-serverless-framework

This repo is a place for me to store my course source code, etc, from the following udemy course:

https://www.udemy.com/course/aws-lambda-serverless/


# Environment Setup

## AWS

* Must have an AWS account (duh!)
* Create a new IAM user
  * recommended IAM username: `serverless-admin`
  * enable 'programmatic access', but **do not** enable management console access
  * assign 'AdministratorAccess' policy to this IAM user
    * **NOTE:** The course instructor does not like this, but at the time the course was recorded, that was the official procedure recommended by the Serverless framework team.
  * remember to save the .csv containing the IAM user's access key ID and secret access key somewhere safe (it is your IAM user's equivalent of a username/password for your AWS account!)

## node.js

* Install node.js locally. Version shouldn't matter. Just install newest version.
* Install the 'serverless' package from npm
  * `npm install -g serverless` 
* Configure the 'serverless' package to use the AWS IAM user that you created above.
  * `serverless config credentials --provider aws --key XXX --secret YYY --profile serverless-admin`
  * Just replace XXX and YYY with your IAM user's access key ID and access key value

## serverless

* Typing 'serverless' at the command line will now issue commands to the serverless module
  * On Windows PowerShell this seems to work from anywhere, so I assume the node.js module download also caused serverless to be added to my system path.
  * Something in Windows PowerShell already uses the command 'sls', so that shortcut for the 'serverless' command does not work.
* Try this: `serverless --help`

# The Hello World Python project

## How to create it

Use the following command to create the new project in a subdirectory of your current location:

`serverless create --template aws-python --path hello-world-python`

## How to deploy it

Use the following command to deploy the project to your AWS account:

`serverless deploy -v`

This will create some objects on your AWS account (a CloudFormation stack, an S3 bucket, a role, etc).

You can now go to the AWS Management Console, navigate to the 'Lambda' service, and run a test against the deployed 'hello-world-python-dev-hello' function.

## How to run from your local command line

Use this command:

`serverless invoke -f hello -l`

This first line that comes back is the return value. The rest is the log output (-l means you want the log output).

## How to update the function code

* Make your code change inside 'handler.py' (for the first Hello World function)
* Execute this command:
  * `serverless deploy -v`
* Verify updated function with this command:
  * `serverless invoke -f hello -l`
* NOTE: Update to function will cause a new CloudFormation log stream to be created, replacing previous one

### How to deploy only function update (without changing CloudFormation stacks)

* Make your code change inside 'handler.py' (for the first Hello World function)
* Execute this command:
  * `serverless deploy function -f hello`
* Verify updated function with this command:
  * `serverless invoke -f hello -l`
* NOTE: Update to function will cause a new CloudFormation log stream to be created, replacing previous one

## How to fetch function logs via AWS CLI

Use this command to retrieve and tail the logs for the 'hello' function:

`serverless logs -f hello -t`

In a separate terminal session, invoke the function so some log output will be generated:

`serverless invoke -f hello -l`

After a few seconds, the log output show reach CloudWatch and in turn be displayed in the first console session.

## How to destroy it

`serverless remove`

Will remove the function, and the CloudFormation stacks that were originally created when you deployed.





# unrelated

Love this post in the NVIDIA forums. Happened to find it as I was editing this file.

https://www.nvidia.com/en-us/geforce/forums/geforce-experience/14/239231/why-do-i-need-to-create-an-account-to-download-dri/

Seems I'm not the only one who doesn't understand why GeForce Experience usually demands a login to get drivers for my graphics card.  :)

Strangely, it didn't prompt me for a login today. Just delivered the current driver as one would expect. How did I end up on this tangent?? Guess I just enjoy reading a toxic forums rant one in a while.
