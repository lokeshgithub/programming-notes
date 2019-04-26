# 26-apr-2019

### 2 - sentry with golang

- https://docs.sentry.io/clients/go/ 

```golang
package main

import "github.com/getsentry/raven-go"
import "os"
import "log"
import "fmt"


func init() {
    raven.SetDSN("https://c10f4d3a8d6eXXXXXXXXXf830bc9ef:8bd45cXXXXXXXXd3154db8f6a2b@sentry.io/000000")
}


func main(){
    
    f, err := os.Open("filename.ext")
    if err != nil {
        raven.CaptureErrorAndWait(err, nil)
        log.Panic(err)
    }

    fmt.Println(f)


}
```

### 1 - server/client in bash for quick use


client:
```bash
#!/bin/sh

while true; do
  msg="$(date '+%Y-%m-%d %H:%M:%S') hello from ${HOSTNAME}"
  echo ${msg}
  echo ${msg} | nc -w 1 localhost 4242
  sleep 1
done;
```


server:
```bash
#!/bin/sh

port="4242"
echo "starting server on ${port}"

while true; do 
  nc -l -p ${port} -vv -k -q 60
done;
```