## Steps to host Swagger API documentation with GitHub Pages

1. Download the latest stable release of the Swagger UI [here](https://github.com/swagger-api/swagger-ui/releases).

2. Extract the contents and copy the "dist" directory to the root of your repository.

3. Move the file "index.html" from the directory "dist" to the root of your repository.
    ```
    mv dist/index.html .
    ```
    
4. Copy the YAML specification file for your API to the root of your repository.

5. Edit [dist/swagger-initializer.js](dist/swagger-initializer.js) and change the `url` property to reference your local YAML file. 
    ```javascript
        window.ui = SwaggerUIBundle({
            url: "swagger.yaml",
        ...
    ```
    Then fix any references to files in the "dist" directory.
    ```html
    ...
    <link rel="stylesheet" type="text/css" href="dist/swagger-ui.css" >
    <link rel="icon" type="image/png" href="dist/favicon-32x32.png" sizes="32x32" />
    <link rel="icon" type="image/png" href="dist/favicon-16x16.png" sizes="16x16" />    
    ...
    <script src="dist/swagger-ui-bundle.js"> </script>
    <script src="dist/swagger-ui-standalone-preset.js"> </script>    
    <script src="dist/swagger-initializer.js" charset="UTF-8"> </script>
    ...
    ```
    
6. Go to the settings for your repository at `https://github.com/iana-org/rzm-api/settings` and enable GitHub Pages.

    
7. Browse to the Swagger documentation at `https://iana-org.github.io./rzm-api/`.
