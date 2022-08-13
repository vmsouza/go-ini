Package ini provides INI file read and write functionality in Go.

## Features

- Load from multiple data sources(file, `[]byte`, `io.Reader` and `io.ReadCloser`) with overwrites.
- Read with recursion values.
- Read with parent-child sections.
- Read with auto-increment key names.
- Read with multiple-line values.
- Read with tons of helper methods.
- Read and convert values to Go types.
- Read and **WRITE** comments of sections and keys.
- Manipulate sections, keys and comments with ease.
- Keep sections and keys in order as you parse and save.

## Installation

The minimum requirement of Go is **1.13**.

```sh
$ go get github.com/vmsouza/go-ini
```

Please add `-u` flag to update in the future.

## License

This project is under Apache v2 License. See the [LICENSE](LICENSE) file for the full license text.

## Example

package main

import (
	"fmt"
	"github.com/vmsouza/go-ini"
	"os"
)

func main() {
  cfg, err := ini.Load("~/.my.cnf")
  if err != nil {
      fmt.Printf("Fail to read file: %v", err)
      os.Exit(1)
  }
	sqlHost:=cfg.Section("client").Key("host").String()
	sqlPort:=cfg.Section("client").Key("port").String()
	sqlUser:=cfg.Section("client").Key("user").String()
	sqlPassword:=cfg.Section("client").Key("password").String()
	sqlDatabase:=cfg.Section("client").Key("database").String()
  fmt.Printf("hostname: %s\n", sqlHost)
	fmt.Printf("hostname: %s\n", sqlPort)
	fmt.Printf("hostname: %s\n", sqlUser)
	fmt.Printf("hostname: %s\n", sqlPassword)
	fmt.Printf("hostname: %s\n", sqlDatabase)
  
