# Zoom API using JWT

> This is a sample app that uses JWT to call Zoom's API. It also uses the request-promise node module to make http calls with Promises. 

## Getting Started

### Install

Clone the repo using git clone.
` git clone https://github.com/zoom/zoom-api-jwt.git`

> Install the dependent node modules.
``` npm install ```

### Quick Start



> In the config.js file, input your client API Key & Secret credentials.
``` const config = {
	production:{	
		APIKey : 'Your environment API Key',
		APISecret : 'Your environment API Secret'
	}
    };
```
> Set your environment varaibles.
` export NODE_NEV=[environment name] (e.g. export NODE_NEV=production) `

> Start the node app.
` node.index.js `

> Enter your email and view the API's response.

### For more Information about Zooms API and JWT
Documentation for JWT is available [here](https://marketplace.zoom.us/docs/guides/authorization/jwt). You can learn more about Zoom API [here](https://marketplace.zoom.us/docs/api-reference/introduction).
## Support
For any questions or issues, please visit our new Community Support Forum at https://devforum.zoom.us/
