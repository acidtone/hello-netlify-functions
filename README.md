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

- 