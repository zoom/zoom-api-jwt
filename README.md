# Make Zoom API call using JWT

> With this app, you can learn how to generate JWT and use the JWT to authenticate and make a Zoom API call. Follow the steps below to install the app and run it on your computer. 

## Getting Started

### Install

Clone the repo using git clone.
`git clone https://github.com/zoom/zoom-api-jwt.git`

> Install the dependent node modules by typing `npm-install` in your terminal.

 The app requires the following modules:

 >jsonwebtoken : Provides a way to generate JWT with jwt.sign() method. 
 >request-promise: Provides a way to Request call objects with .then() method.
 >express: Web application framework for Node.js.

### Quick Start

To generate JWT, you have to provide your API Key and API Secret credentials. You can locate these credentials in your app’s configuration by going to `Zoom Marketplace > Manage > <YourApp> > App Credentials`. If you haven’t already registered your app in the marketplace, you will have to create an app here to get your credentials. For the purpose of this sample app, you only need your credentials and you do not have to fill out any additional information while registering the app.

> In the config.js file, input your client API Key & Secret credentials.

``` 
const config = {
    production:{	
        APIKey: 'Your environment API Key',
        APISecret: 'Your environment API Secret'
    }
};
```

> Start the node app.
Type `node index.js` in your terminal from within the project directory.

> Enter your email and view the API's response.
 When you run the app, you will see a form that asks for an email address. Provide your Zoom email address and you will see your JWT and other information related to your account. 

The following code snippet generates the JWT using your Client Credentials:

``` 
const payload = {
    iss: config.APIKey,
    exp: (new Date()).getTime() + 5000
};

const token = jwt.sign(payload, config.APISecret);
```

After you submit an email address, it will post the entered information and the email will be used to make a **Retrieve User** Zoom API call and you will be redirected to localhost:3000/userinfo page that displays the API response - information related to the user. This is achieved through an HTTP POST method. You can make API calls to other ZOOM endpoints by replacing the uri shown in the snippet below with another uri of your choice. You can find more about ZOOM APIs here. 

```
const options = {
    uri: `https://api.zoom.us/v2/users/${email}`, 
    qs: {
        'status': 'active' 
    },
    auth: {
        'bearer': token
    },
    headers: {
        'User-Agent': 'Zoom-api-Jwt-Request',
        'content-type': 'application/json'
    },
    json: true // Parse the JSON string in the response
};
```

### For more Information about Zooms API and JWT

Documentation for JWT is available [here](https://marketplace.zoom.us/docs/guides/authorization/jwt). You can learn more about Zoom API [here](https://marketplace.zoom.us/docs/api-reference/introduction).

## Need help?

If you're looking for help, try [Developer Support](https://devsupport.zoom.us) or our [Developer Forum](https://devforum.zoom.us). Priority support is also available with [Premier Developer Support](https://zoom.us/docs/en-us/developer-support-plans.html) plans.



