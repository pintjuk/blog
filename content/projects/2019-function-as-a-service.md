+++
author = "Daniil Pintjuk"
categories = ["golang", "cloud"]
date = "2019-01-01"
description = "So this docker thing seems to be getting some traction, and so does function as a service (FaaS). It would be nice if we could have our own FaaS infrastructure in place instead of paying Amazon for it. There are some alternatives out there e.g. OpenFaaS. But we have a bad case of “Not Invented Here” syndrome, so we built one ourselves."
featured = "scetch.png"
featuredalt = "scetch of system"
featuredpath = "2019-06/faas/"
linktitle = "FaaS - "
title = "Function as a Service"
type = "post"

+++
This is a small GoLang infrastructure app that enables to easy deploy a simple server acting like
single functions. The goal was to easily deploy and scale the app horizontally. To achive this we leveraged the scaling, service discovery that come for free in a docker compose and swarm environment.

The core component is the FaaS Gateway that uses docker to dynamicaly descover function and rederect requests to them. The image above illustrates the idaa.

## Installing

### Requirements

1. Docker
2. Docker-compose
3. Govendor

Install go.

Install docker and docker compose.

Install govendor:

``` bash
go get -u github.com/kardianos/govendor
```

Clone this repo:

``` bash
git clone https://github.com/kardianos/govendor.git
```

## Running FAAS

``` bash
cd faas
docker-compuose up
```

## Creating a your function

A function is a docker container runing a micro service implemented as a single simple golang function.

Creating a function is easy using the faas/function library.

``` golang
import (
	"github.com/pintjuk/faas/function"
)

func main() {
	function.RunFunc([]string{"a", "b"},
		func(a float64, b float64) float64 {
			return a + b
		},
		":8080")
}
```

Just pas any regular golang function to RunFunc, and the library will spin up a web server running this function.

to make it work with the FAAS gateway you need to run it in a docker container with with labels

``` 

faas.name={name of your function}
```

and

``` 
faas.port={the port you used for its web server}
```

With this lables the FAAS gateway will detect your function container automatically and start forwarding function calls to it.
