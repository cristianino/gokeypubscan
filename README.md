# GoKeyPubScan

Este es un generador de direcciones de Bitcoin en Golang, su implementación es sencilla

## Instalación

```bash
go get -u github.com/cristianino/gokeypubscan
```

## Uso consultando API

```go
package main

import (
	"fmt"

	"github.com/cristianino/gokeypubscan"
)

func main() {
	var keys gokeypubscan.Keys
	keys.GeneratePrivKey()
	keys.GeneratePublicKey()
	keys.GenerateAddress()
	keys.GetBalance()

	// Print the private key, public key, and Bitcoin address to the console.
	fmt.Println("Private key:", keys.GetKeyPrivate())
	fmt.Println("Public key:", keys.GetKeyPublic())
	fmt.Println("Bitcoin address:", keys.GetAddress())
	fmt.Printf("El saldo de la wallet BTC es: %f BTC\n", keys.Balance)
}
```

## Uso consultando Nodo local

```go
package main

import (
	"fmt"

	"github.com/cristianino/gokeypubscan"
)

func main() {
	var keys gokeypubscan.Keys
	keys.GeneratePrivKey()
	keys.GeneratePublicKey()
	keys.GenerateAddress()
	keys.isLocalNode(NodeData{
		url:     "127.0.0.1",
		port:    ":8332",
		userRcp: "tu_usuario_rpc",
		passRcp: "tu_contraseña_rpc",
		useSSL:  false,
	})
	keys.GetBalance()

	// Print the private key, public key, and Bitcoin address to the console.
	fmt.Println("Private key:", keys.GetKeyPrivate())
	fmt.Println("Public key:", keys.GetKeyPublic())
	fmt.Println("Bitcoin address:", keys.GetAddress())
	fmt.Printf("El saldo de la wallet BTC es: %f BTC\n", keys.Balance)
}
```