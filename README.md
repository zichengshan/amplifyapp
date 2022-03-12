# README
## Create a Notes Application using AWS Amplify
1. Added authentication to your app allowing users to sign up, sign in, and manage their account
2. Scalable GraphQL API configured with an Amazon DynamoDB database allowing users to create and delete notes
3. Added file storage using Amazon S3 allowing users to upload images and view them in their app
### DEMO
![Screen Recording 2022-03-12 at 3 28 47 PM mov-high](https://user-images.githubusercontent.com/61951792/158038840-0f3ff922-e177-431b-9e07-64d45bdb934f.gif)

### PART1
**Create a React application and deploy it to the cloud using AWS Amplify web hosting service**

**AWS Amplify** provides a Git-based CI/CD workflow for building, deploying, and hosting single page web applications or static sites with serverless backends.
#### Steps:
1. Create a React application by using command ```npx create-react-app amplifyapp```
2. Initialize GitHub repository, initialize git and push the application to the new GitHub
3. Connect the GitHub repository to the AWS Amplify service!<img width="1236" alt="Screen Shot 2022-03-12 at 3 45 01 PM" src="https://user-images.githubusercontent.com/61951792/158038939-4679760e-dbbc-4dc2-9113-d79b00dd6b3c.png">

### PART2
**install and configure Amplify CLI**

**Amplify CLI** is a unified toolchain to create, manage, and remove AWS services directly from our terminal.
#### Steps:
1. Install Amplify CLI by using command ```npm install -g @aws-amplify/cli```
2. Configure Amplify CLI by using command ```amplify configure``` and follow this [tutorial video](https://www.youtube.com/watch?v=fWbM5DLh25U). Amazon IAM(Identity and Access Management) enables us to manage users permissions in AWS.
3. Initialize the app (Deploy a back end and initialize the backend environmental locally)

### PART3
**Use Amplify CLI and libraries to configure and add authentication to the app**
#### Steps:
1. Install Amplify libraries by using the command ```npm install aws-amplify @aws-amplify/ui-react```
   1. aws-amplify library contains all the client-side APIs for interacting with the various AWS services
   2. @aws-amplify/ui-react library contains framework-specific UI components.
2. Create the authentication service by using ```amplify add auth```
3. Deploy the authentication service by using ```amplify push --y```
4. Configure the React project with Amplify resources, add imports in index.js
5. Add the authentication flow in App.js by using withAuthenticator component. This component will scaffold an entire user authentication flow allowing users to sign up, sign in and reset their password, and confirm sign in for multifactor authentication(MFA)
6. Set up CI/CD if the front end and backend.

### PART4
**Use Amplify CLI and libraries to configure and add a GraphQL API to app**
**GraphQL** API leverages AWS AppSync (a managed GraphQL service) which is backed by **Amazon DynamoDB** (a NoSQL database)
#### Steps:
1. Create a GraphQL API and database ```amplify add api```
2. Open the schema.graphql and add the following schema: 
    ```aidl
    type Note @model {
      id: ID!
      name: String!
      description: String
    }
    ```
3. Deploy API ```amplify push --y```. This will do three things: 
   1. Create the AppSync API
   2. Create a DynamoDB table
   3. Create the local GraphQL operations in a folder located at src/graphql that can be used to query the api
4. Write frond-end code to interact with the API. Saved in src/App.js

### PART5
**Add storage and the ability to associate an image with the notes in the app**
Use Amplify CLI and libraries to create a storage service leveraging **Amazon S3**.
#### Steps:
1. Create the storage service ```amplify add storage```
2. Update the GraphQL schema, add one line: ```image: String``` in schema.graphql
3. Deploy storage service and API updates ```amplify push --y```
4. Update React app in App.js file
   1. Add storage class ```import { API, Storage} from 'aws-amplify'```
   2. Create a new onChange function
   3. Update the fetchNotes function to fetch an image
   4. Update the createNote function to add the image to the local image array
   5. Add additional input to the form in the return block
   6. Render an image if it exists

--------------
# Getting Started with Create React App

This project was bootstrapped with [Create React App](https://github.com/facebook/create-react-app).

## Available Scripts

In the project directory, you can run:

### `npm start`

Runs the app in the development mode.\
Open [http://localhost:3000](http://localhost:3000) to view it in your browser.

The page will reload when you make changes.\
You may also see any lint errors in the console.

### `npm test`

Launches the test runner in the interactive watch mode.\
See the section about [running tests](https://facebook.github.io/create-react-app/docs/running-tests) for more information.

### `npm run build`

Builds the app for production to the `build` folder.\
It correctly bundles React in production mode and optimizes the build for the best performance.

The build is minified and the filenames include the hashes.\
Your app is ready to be deployed!

See the section about [deployment](https://facebook.github.io/create-react-app/docs/deployment) for more information.

### `npm run eject`

**Note: this is a one-way operation. Once you `eject`, you can't go back!**

If you aren't satisfied with the build tool and configuration choices, you can `eject` at any time. This command will remove the single build dependency from your project.

Instead, it will copy all the configuration files and the transitive dependencies (webpack, Babel, ESLint, etc) right into your project so you have full control over them. All of the commands except `eject` will still work, but they will point to the copied scripts so you can tweak them. At this point you're on your own.

You don't have to ever use `eject`. The curated feature set is suitable for small and middle deployments, and you shouldn't feel obligated to use this feature. However we understand that this tool wouldn't be useful if you couldn't customize it when you are ready for it.

## Learn More

You can learn more in the [Create React App documentation](https://facebook.github.io/create-react-app/docs/getting-started).

To learn React, check out the [React documentation](https://reactjs.org/).

### Code Splitting

This section has moved here: [https://facebook.github.io/create-react-app/docs/code-splitting](https://facebook.github.io/create-react-app/docs/code-splitting)

### Analyzing the Bundle Size

This section has moved here: [https://facebook.github.io/create-react-app/docs/analyzing-the-bundle-size](https://facebook.github.io/create-react-app/docs/analyzing-the-bundle-size)

### Making a Progressive Web App

This section has moved here: [https://facebook.github.io/create-react-app/docs/making-a-progressive-web-app](https://facebook.github.io/create-react-app/docs/making-a-progressive-web-app)

### Advanced Configuration

This section has moved here: [https://facebook.github.io/create-react-app/docs/advanced-configuration](https://facebook.github.io/create-react-app/docs/advanced-configuration)

### Deployment

This section has moved here: [https://facebook.github.io/create-react-app/docs/deployment](https://facebook.github.io/create-react-app/docs/deployment)

### `npm run build` fails to minify

This section has moved here: [https://facebook.github.io/create-react-app/docs/troubleshooting#npm-run-build-fails-to-minify](https://facebook.github.io/create-react-app/docs/troubleshooting#npm-run-build-fails-to-minify)
