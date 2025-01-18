# PromQL Lexer and Parser

The goal of this project is to build a PromQL parser.

## Example

To parse a simple instant vector selector expression:

``` lua
local promql = require("promql_parser")

local promql_str = "http_requests_total{environment=~\"staging\", method!=\"GET\"} offset 5m"

local parts, err = promql.parse(promql_str)
```
Output
```
{
  matchers = { {
      name = "environment",
      type = "=~",
      value = "staging"
    }, {
      name = "method",
      type = "!=",
      value = "GET"
    } },
  name = "http_requests_total",
  offset = 300000.0,
  type = "vectorSelector"
}
```

### Language Binding
This is a lua language binding to the original promql-parser repo.
- [promql-parser](https://github.com/GreptimeTeam/promql-parser) Original Rust Crate.

## Installation

``` bash
luarocks install lua-promql-parser
```
