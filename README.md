# websocket

websocket is copy of [golang.org/x/net/websocket](golang.org/x/net/websocket)



## Feature

1. Set Host Header when websocket handshark

You can send handshark data to special address with different Host header

2. Set TLS Config

You can set InsecureSkipVerify to ignore ssl verify error

3. Fully compatible

You can replace `golang.org/x/net/websocket` package with `github.com/akkuman/websocket`


## Example

```golang
// set host and tls config

package main

import (
	"fmt"
	"log"

	"golang.org/x/net/websocket"
)

func main() {
	origin := "http://localhost/"
	url := "ws://localhost:12345/ws"
    ws := websocket.NewConfig(url, origin, WithSourceHost("baidu.com"), WithTlsConfig(&tls.Config{
			InsecureSkipVerify: true,
    }))
    
    conn, err := websocket.DialConfig(cfg)
    
    ...
}
```
