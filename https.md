``` go
openssl genrsa -out key.pem 2048
openssl req -new -x509 -key key.pem -out cert.pem -days 1095
```

``` go
package main

import (

    "log"
    "net/http"
)

func SayHello(w http.ResponseWriter, req *http.Request) {
    w.Write([]byte("Hello"))
}

func main() {

    http.HandleFunc("/", SayHello)
    err := http.ListenAndServeTLS(":8080", "cert.pem", "key.pem", nil)
    if err != nil {
        log.Fatal("ListenAndServe: ", err)
    }
}
```
> 附一个免费的ssl证书制造地方

> http://zyan.cc/startssl/
