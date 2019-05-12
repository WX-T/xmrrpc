# xmrrpc
Golang client for Monero (XMR) Json RPC API.

Support daemon's Json-RPC. Support digest authentication.

Tested on: Monero 'Boron Butterfly' (v0.14.0.2-release), stagenet.

## Documentation
Full API Documentation can be found at https://web.getmonero.org/resources/developer-guides/

Current API version: network height of 1,562,465.

### JSON RPC Methods:
- get_block_count
- on_get_block_hash
- get_block_template
- submit_block
- get_last_block_header
- get_block_header_by_hash
- get_block_header_by_height
- get_block_headers_range
- get_block
- get_connections
- get_info
- hard_fork_info
- set_bans
- get_bans
- flush_txpool
- get_output_histogram
- get_version
- get_coinbase_tx_sum
- get_fee_estimate
- get_alternate_chains
- relay_tx
- sync_info
- get_txpool_backlog
- get_output_distribution

## Know issues
- get_output_distribution - bad server response (invalid character '\x00' in string literal)

## Installation
```bash
$ go get github.com/stdfox/xmrrpc
```

## Importing
```go
import (
    "github.com/stdfox/xmrrpc"
)
```

## Example
```go
package main

import (
	"fmt"

	"github.com/stdfox/xmrrpc"
)

func main() {
	daemonClient := xmrrpc.NewDaemonClient("http://127.0.0.1:38081/json_rpc", "username", "password")

	res, err := daemonClient.GetLastBlockHeader()
	if err != nil {
		panic(err)
	}

	fmt.Printf("[Status: %s] Hash: %s\n", res.Status, res.BlockHeader.Hash)
}
```
```shell
$ go run main.go
[Status: OK] Hash: fb7070a2787a71a900b527fe30f0b32063cf0441511a1be32203e1d9994a7f43
```

## License
[MIT License](https://github.com/stdfox/xmrrpc/blob/master/LICENSE.md)

## Donation ❤
If this project help you, you can give me a cup of coffee :)

XMR: `49Nz5mVA9sQjKrT65TgdEneiZo1oCp3n8bCtjA3qaCoa5cuPKxqWBcZfD1f1iv6ASjCQUK55m3r4iho7ivMcNvsLDnP3sqX`

BTC: `1Kyxw87175msSRkXez7iKrzZLBaPb7rp1H`
