# Blazer - Concurrent file downloader

<p align="left">
  <a href="https://goreportcard.com/report/github.com/arvryna/blazer">
    <img src="https://goreportcard.com/badge/github.com/arvryna/blazer" />
  </a>
   <a href="http://makeapullrequest.com">
    <img src="https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=flat-square" />
  </a>
</p>

- Control thread count
- Resume from interruption
- File integrity check - SHA256

## Usage
``` blazer -url=example.com/1.pdf -t=10  ```

## Flags 
```
blazer -h
Usage of blazer:
  -checksum string
    	checksum SHA256(currently supported) to verify file
  -out string
    	output path to store the downloaded file
  -t int
    	Thread count - Number of concurrent downloads (default 10)
  -url string
    	Valid URL to download
  -v	prints current version of blazer

```

## Benchmarks
| Name       |Size    | Blazer                  | cURL          | Wget         |
| -----------|--------| -----------             | ----          | -----        |
| Debian ISO | 300 MB | 1min 10 sec (25 threads)| 2min 40 sec   | 3 min 10 sec |
| Windows-10 | 5.4 GB | 20min 52sec (25 threads)| 46min 52 sec  | 40 min 25 sec|

## How file resumption work ?
If download is either interrupted manually or network error (Timeout, RCP - happens if "-t" is a large number than server can handle) then those segments may fail and you may have to restart the download with same URL and thread count for retry to work because, temp folder name is a hash of URL and thread count. 

## Demo
[![asciicast](https://asciinema.org/a/DInboSaUY2Ik9JIOcY4vZHRY9.svg)](https://asciinema.org/a/DInboSaUY2Ik9JIOcY4vZHRY9)

## Install

- Download 64bit binary from releases: https://github.com/arvryna/blazer/releases

or

- Build from source: 

```
git clone git@github.com:arvryna/blazer.git
make package
```
