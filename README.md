<p align="center">
  <img src="https://raw.githubusercontent.com/SonicCloudOrg/sonic-server/main/logo.png">
</p>
<p align="center">🎉Proxy Plugin of Sonic cloud real machine testing platform</p>
<p align="center">
  <span>English |</span>
  <a href="https://github.com/SonicCloudOrg/sonic-go-mitmproxy/blob/main/README_CN.md">  
     简体中文
  </a>
</p>

This repo was fork from [go-mitmproxy](https://github.com/lqqyt2423/go-mitmproxy).
We will optimize and customize based on this, and we will also provide our pr to the original repo.

### Official Website
[Sonic Official Website](http://sonic-cloud.gitee.io)
## Background

#### What is sonic ?

> Nowadays, automatic testing, remote control and other technologies have gradually matured. [Appium](https://github.com/appium/appium) can be said to be the leader in the field of automation, and [STF](https://github.com/openstf/stf) is the ancestor of remote control. A long time ago, I began to have an idea about whether to provide test solutions for all clients (Android, IOS, windows, MAC and web applications) on one platform. Therefore, sonic cloud real machine testing platform was born.

#### Vision

> Sonic's vision is to help small and medium-sized enterprises solve the problem of lack of tools and testing means in client automation or remote control.
>
>If you want to participate, welcome to join! 💪
>
>If you want to support, you can give me a star. ⭐


## Features

- Intercept HTTP & HTTPS requests and responses and modify them on the fly
- SSL/TLS certificates for interception are generated on the fly
- Certificates logic compatible with [mitmproxy](https://mitmproxy.org/), saved at `~/.mitmproxy`. If you used mitmproxy before and installed certificates, then you can use this go-mitmproxy directly
- Addon mechanism, you can add your functions easily, refer to [addon/addon.go](./addon/addon.go)
- Performance advantages
  - Golang's inherent performance advantages
  - Forwarding and parsing HTTPS traffic in process memory without inter-process communication such as tcp port or unix socket
  - Use LRU cache when generating certificates of different domain names to avoid double counting
- Support `Wireshark` to analyze traffic through the environment variable `SSLKEYLOGFILE`
- Support streaming when uploading/downloading large files
- Web interface

## Usage

### Startup

```
sonic-go-mitmproxy
```

After startup, the HTTP proxy address defaults to port 9080, and the web interface defaults to port 9081.

After the first startup, the SSL/TLS certificate will be automatically generated at `~/.mitmproxy/mitmproxy-ca-cert.pem`. You can refer to this link to install: [About Certificates](https://docs.mitmproxy.org/stable/concepts-certificates/).

### Help

```
Usage of sonic-go-mitmproxy:
  -addr string
    	proxy listen addr (default ":9080")
  -dump string
    	dump filename
  -dump_level int
    	dump level: 0 - header, 1 - header + body
  -mapper_dir string
    	mapper files dirpath
  -ssl_insecure
    	not verify upstream server SSL/TLS certificates.
  -version
    	show version
  -web_addr string
    	web interface listen addr (default ":9081")
  -cert_path string
    	path of generate cert files
```

## Usage as package

Refer to [cmd/go-mitmproxy/main.go](./cmd/go-mitmproxy/main.go), you can add your own addon by call `AddAddon` method.

For more examples, please refer to [examples](./examples)

## Web interface

![](./assets/web-1.png)

![](./assets/web-2.png)

![](./assets/web-3.png)

## TODO

- [ ] Support http2
- [ ] Support parse websocket

## License

[MIT License](./LICENSE)
