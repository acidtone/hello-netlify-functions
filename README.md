# Hello Netlify Functions
Goal: Have Netlify recognize a serverless function in their admin panel.

## Plan
1. Create a repo with a `hello` function that does whatever
2. Create a netlify.toml file (that isn't broken), setting the `functions` folder.
3. Create a Netlify app and deploy from repo
4. Success condition: `hello` function shows up in Netlify admin.

## Brute force notes
- First question in my mind: what should the function do? What's the minimum? Found this code on the [Build functions with JavaScript](https://docs.netlify.com/functions/build-with-javascript/) docs page:

    ```js
    exports.handler = async function(event, context) {
      return {
        statusCode: 200,
        body: JSON.stringify({message: "Hello World"})
      };
    }
    ```

- There seems to be a some variation in the docs over how to set up functions with `netlify.toml`. I'm going by the official docs:

    ```
    [functions]
      directory = "functions"
    ```

- Does npm need to be initialized for netlify functions to work? Answer: nope!

## Walk-through
Success: The [hello-netlify-functions](https://github.com/acidtone/hello-netlify-functions) repo is the minimum you need to publish a Netlify function.
    - a [`netlify.toml`](https://github.com/acidtone/hello-netlify-functions/blob/main/netlify.toml) file is needed to configure the location of the functions directory
    - Requests to the functions are routed according to this pattern:

        ```
        https://[site-name].netlify.app/.netlify/functions/[function-name]
        ```

        Example:
        
        ```
        https://sait-wbdv-netlify-functions.netlify.app/.netlify/functions/hello
        ```

Next Steps:
- Get this example to work locally with Netlify Dev:

    ```
    https://locahost:3000/.netlify/functions/hello
    ```

- Figure out how to add wildcard redirects for the endpoint so that:

    ```
    https://sait-wbdv-netlify-functions.netlify.app/.netlify/functions/hello
    ```

    maps to 

    ```
    https://sait-wbdv-netlify-functions.netlify.app/api/hello
    ```

## Optimize
- Nothing needed.