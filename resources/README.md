# Guide to Using the Postman collection and environments Provided

Here are the various files one needs to inspect/ try out the Central registry and Sahamati Token issuance service

## Pre-requisites

1. [Postman](https://www.postman.com/)

You need to have a Postman collection account, which can be obtained by signing up [here](https://identity.getpostman.com/signup).

Athough Postman offers a web-based client, we highly reccomend installing the Application to avoid unnecessary errors while using the collection. The application can be found [here](https://www.postman.com/downloads/).

----------------------------------------------------------

## Overview of files

There are three files present in the "Postman collections" folder:

- The Central Registry Postman Collection
- The Central Registry Environment
- The Token Issuance service Postman collection

The first two files are necessary for trying out or inspecting the Central registry Postman collection, while the last file is sufficient for the Token Issuance service

----------------------------------------------------------

## How-To

1. The Central Registry

There are two files required for setting up the Central Registry Collection on Postman:

- The Postman collection
- The Environment file.

Here are the steps:

i. Open Postman collection on your Computer (Web client or Application)

ii. [Optional] Create a new Workspace by clicking Clicking on the Workspace tab and then selecting Create new Workspace and selecting the parameters that suit your need.

iii. Inside you custom workspace or the default Postman workspace, Go to the collection tab.

iv. Click on the import button found in the top right corner of the left pane.

v. In the "File" tab, select "Upload Files" and select the File - "CR - Endpoints.postman_collection.json".

vi. Click on Import and wait for the process to complete.

vii. Now head over to the Environment tab from the extreme left pane and repeat the process with the File: "CR Environment.postman_environment.json" to import the environment

viii. Hover over the imported environment's name and click on the check mark to enable the environment.

ix. Double click on the environment to view it's details.

x. In the table that's now visible, fill in the relevant details

xi. You're good to go!

Now you can view the various details regarding Sahamati's Central registry API as well as use this set up to test your API calls before embedding them into your system.

2. Token Issuance service

There is only one file required for setting up the Central Registry Collection on Postman:

- The Postman collection

Here are the steps:

i. Open Postman collection on your Computer (Web client or Application)

ii. [Optional] Create a new Workspace by clicking Clicking on the Workspace tab and then selecting Create new Workspace and selecting the parameters that suit your need.

iii. Inside you custom workspace or the default Postman workspace, Go to the collection tab.

iv. Click on the import button found in the top right corner of the left pane.

v. In the "File" tab, select "Upload Files" and select the File - "token-issuance-api.postman_collection.json".

vi. Click on Import and wait for the process to complete.

You're good to go!