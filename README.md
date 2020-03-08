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




# unrelated

Love this post in the NVIDIA forums. Happened to find it as I was editing this file.

https://www.nvidia.com/en-us/geforce/forums/geforce-experience/14/239231/why-do-i-need-to-create-an-account-to-download-dri/

Seems I'm not the only one who doesn't understand why GeForce Experience usually demands a login to get drivers for my graphics card.  :)

Strangely, it didn't prompt me for a login today. Just delivered the current driver as one would expect. How did I end up on this tangent?? Guess I just enjoy reading a toxic forums rant one in a while.
