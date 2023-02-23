# Swgger Inject 
embed swagger ui resources


# usage

assume you will access your swagger ui from `/swagger/index.html`

just serve your `swagger.json` at /swagger.json

see `swagger/js/swagger-initializer.js` for details

### gin example

```go
package main

import (
    "github.com/gin-gonic/gin"
    "github.com/linxlib/swagger_inject"
)

func main() {
    r := gin.Default()
    r.GET("/swagger.json",func(c *gin.Context) {
        // write your swagger.json to response body
    })
    r.GET("/swagger/*any",func(c *gin.Context){
        c.FileFromFS(c.Request.URL.Path, http.FS(swagger_inject.FS))
    })
    r.Run(":8080")
}
```


