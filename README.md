<h1 align="left" style="border-bottom: none;">🚀 Watson Assistant Sample Application</h1>
<h3 align="left">This Node.js app demonstrates the Watson Assistant service in a simple interface.</h3>
<p align="left"></p>

![Demo](readme_images/demo.gif)

You can view a [demo][demo_url] of this app.


## Prerequisites
Sign up for an [IBM Cloud account](https://console.bluemix.net/registration/).

## Develop your chatbot conversation

Login to IBM Cloud. 

### Step 1. Create Watson Assistant service on IBM Cloud
With IBM Watson™ Assistant service you can build a solution that understands natural-language input and uses machine learning to respond to customers in a way that simulates a conversation between humans.

Go to your IBM Cloud account and open the catalog. Look for Watson Assistant service and click on it.

<img src="/readme_images/WA1.png" width="50%" height="50%">

Choose the region and space where you want the service to be created. In new accounts it will automatically select your resource group, usually named as default. 
You don't need to change the name if you don't want to, just click on 'Create'. 
![](/readme_images/WA2.png?raw=true)

### Step 2. Import a conversation
Once the service is created click on 'Launch tool' to access it. 

<img src="/readme_images/WA3.png" width="60%" height="60%">

In the home tab you have videos and tutorials on how to get started building dialoges. Feel free to explore them. 
Let's move to the Skills tab.

<img src="/readme_images/WA5b.png" width="50%" height="50%">

The natural-language processing happens inside a skill, which is a container for all of the artifacts that define the conversation flow for an application.

You can create a new skill and start from scratch or import an existing conversation. 

Download a conversation from here: https://ibm.box.com/v/bank-conversation 

Click on the 'Create new' button and then click on the import skill tab.

<img src="/readme_images/WA6b.png" width="30%" height="30%">

When you import a skill, you can choose to import only the intents and entities, which can be useful if you want to build a new dialog using the same training data. In this case we will import everything. Click on 'Choose JSON file ' button and find the file you just downloaded. Then click on Import.

<img src="/readme_images/WA7b.png" width="50%" height="50%">

### Step 3. Understand how Watson Assitant works
IBM Watson™ Assistant is a cognitive bot that you can customize for your business needs, and deploy across multiple channels to bring help to your customers where and when they need it.

**Dialog skill**

Create a dialog skill. Use the intuitive graphical tool to define the training data and dialog for the conversation between your assistant and your customers. In this lab we imported a sample conversation. 

The training data consists of the following artifacts:

**Intents:** Goals that you anticipate your users will have when they interact with the service. Define one intent for each goal that can be identified in a user's input. For example, you might define an intent named store_hours that answers questions about store hours. For each intent, you add sample utterances that reflect the input customers might use to ask for the information they need, such as, What time do you open?
You can also use prebuilt content catalogs provided by IBM to get started with data that addresses common customer goals.

**Entities:** An entity represents a term or object that provides context for an intent. For example, an entity might be a city name that helps your dialog to distinguish which store the user wants to know store hours for.
As you add training data, a natural language classifier is automatically added to the skill, and is trained to understand the types of requests that you have indicated the service should listen for and respond to.

**Dialog:** Use the dialog tool to build a dialog flow that incorporates your intents and entities. The dialog flow is represented graphically in the tool as a tree. You can add a branch to process each of the intents that you want the service to handle. You can then add branch nodes that handle the many possible permutations of a request based on other factors, such as the entities found in the user input or information that is passed to the service from an external service.

### Step 4. Test your dialog
As you make changes to your dialog, you can test it at any time to see how it responds to input.
From the Dialog tab, click the conversation bubble icon. In the chat panel, type some text and then press Enter.
Check the response to see if the dialog correctly interpreted your input and chose the right response. 

The chat window indicates what intents and entities were recognized in the input. In the dialog editor pane, the currently active node is highlighted
Feel free to create new intents for your bot.
![](/readme_images/WA8B.png?raw=true)

### Step 5. Get Watson Assistant credentials 
Once you have tested the dialoge, it's time to collect the credentials. You will need them to connect the web application in future steps to your chatbot. 

Click on the Skills name and go back to the Skills overview. 

<img src="/readme_images/WA-1.png" width="40%" height="40%">

Click on the 3 dots in your Assistant to open a menu and then click on View API details. 

<img src="/readme_images/WA-2.png" width="40%" height="40%">

Copy the credentials and save them for later. You will need the Workspace ID (skill), username ('apikey') and password. 

<img src="/readme_images/WA-3.png" width="60%" height="60%">

## Deploy the application to IBM Cloud

Click here to deploy the user interface of your bot:

<a href="https://bluemix.net/deploy?repository=https://github.com/sandra-calvo/assistant-simple&branch=master"><img src="https://bluemix.net/deploy/button.png" alt="Deploy to IBM Cloud"></a>

## Configuring the application

The application will not run till you enter your Watson Assitant credentials. Open the Git to see the application code. 

Open the *.env* file and add the service credentials that you obtained in the previous step. The Watson SDK automatically locates the correct environment variables for either `username`, `password`, and `url` or the `apikey` and `url` credentials found in the *.env* file.

    Example *.env* file that configures the `apikey` and `url` for a Watson Assistant service instance hosted in the US East region:

    ```
    ASSISTANT_IAM_APIKEY=X4rbi8vwZmKpXfowaS3GAsA7vdy17Qh7km5D6EzKLHL2
    ASSISTANT_URL=https://gateway-wdc.watsonplatform.net/assistant/api
    ```

    - If your service instance uses `username` and `password` credentials, add the `ASSISTANT_USERNAME` and `ASSISTANT_PASSWORD` variables to the *.env* file.

    Example *.env* file that configures the `username`, `password`, and `url` for a Watson Assistant service instance hosted in the US South region:

    ```
    ASSISTANT_USERNAME=522be-7b41-ab44-dec3-g1eab2ha73c6
    ASSISTANT_PASSWORD=A4Z5BdGENrwu8
    ASSISTANT_URL=https://gateway.watsonplatform.net/assistant/api
    ```
    However, if your credentials contain an IAM API key, copy the `apikey` and `url` to the relevant fields.
    ```JSON
      {
        "apikey": "ca2905e6-7b5d-4408-9192-e4d54d83e604",
        "iam_apikey_description": "Auto generated apikey during resource-key ...",
        "iam_apikey_name": "auto-generated-apikey-62b71334-3ae3-4609-be26-846fa59ece42",
        "iam_role_crn": "crn:v1:bluemix:public:iam::::serviceRole:Manager",
        "iam_serviceid_crn": "crn:v1:bluemix:public:iam...",
        "url": "https://gateway-syd.watsonplatform.net/assistant/api"
      }
    ```
    ```
    ASSISTANT_IAM_APIKEY=ca2905e6-7b5d-4408-9192-e4d54d83e604
    ASSISTANT_IAM_URL=https://gateway-syd.watsonplatform.net/assistant/api
    ```

7. Add the `WORKSPACE_ID` to the previous properties

    ```
    WORKSPACE_ID=522be-7b41-ab44-dec3-g1eab2ha73c6
    ```
Once you commit the changes the application will start and you will be able to test your chatbot in your given URL. 
To check the URL go to: 

## Running locally

Clone the repository to your machine.

1. Install the dependencies

    ```
    npm install
    ```

2. Run the application

    ```
    npm start
    ```

3. View the application in a browser at `localhost:3000`

Make sure you modified the .env file with your own credentials. 

## Deploying to IBM Cloud as a Cloud Foundry Application

1. Login to IBM Cloud with the [IBM Cloud CLI](https://console.bluemix.net/docs/cli/index.html#overview)

    ```
    ibmcloud login
    ```

1. Target a Cloud Foundry organization and space.

    ```
    ibmcloud target --cf
    ```

1. Edit the *manifest.yml* file. Change the **name** field to something unique.  
  For example, `- name: my-app-name`.
1. Deploy the application

    ```
    ibmcloud app push
    ```

1. View the application online at the app URL.  
For example: https://my-app-name.mybluemix.net


## License

This sample code is licensed under Apache 2.0.  
Full license text is available in [LICENSE](LICENSE).

## Contributing

See [CONTRIBUTING](CONTRIBUTING.md).

## Open Source @ IBM

Find more open source projects on the
[IBM Github Page](http://ibm.github.io/).


[demo_url]: http://conversation-simple.ng.bluemix.net/
[doc_intents]: (https://console.bluemix.net/docs/services/conversation/intents-entities.html#planning-your-entities)
[docs]: https://console.bluemix.net/docs/services/conversation/index.html
[docs_landing]: (https://console.bluemix.net/docs/services/conversation/index.html)
[node_link]: (http://nodejs.org/)
[npm_link]: (https://www.npmjs.com/)
[sign_up]: bluemix.net/registration
