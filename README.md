# captive-browser

A more secure, dedicated captive portal browser that automatically bypasses custom DNS servers.

`captive-browser` detects the DHCP DNS server and runs a SOCKS5 proxy that resolves hostnames through it. Then it starts a browser instance in incognito/private mode with a separate data directory and waits for it to exit.

[Read more on the original author's blog.](https://blog.filippo.io/captive-browser)

## Installation

``` bash
go install github.com/cyb3rko/captive-browser@latest
```

You have to install a config file in `~/.config/captive-browser.toml`. You can probably use one of the stock ones below. You might have to modify the network interface.

### Arch / systemd-networkd

Example with Firefox, find more browser configs at https://github.com/cyb3rko/captive-browser.

``` bash
go install github.com/cyb3rko/captive-browser/cmd/systemd-networkd-dns
curl -fsSL https://raw.githubusercontent.com/cyb3rko/captive-browser/refs/heads/main/captive-browser-arch-firefox.toml ~/.config/captive-browser.toml
```

### Arch / dhcpcd

Example with Chromium, find more browser configs at https://github.com/cyb3rko/captive-browser.

``` bash
curl -fsSL https://raw.githubusercontent.com/cyb3rko/captive-browser/refs/heads/main/captive-browser-dhcpcd-chromium.toml ~/.config/captive-browser.toml
```

### Ubuntu

Example with Chrome, find more browser configs at https://github.com/cyb3rko/captive-browser.

``` bash
curl -fsSL https://raw.githubusercontent.com/cyb3rko/captive-browser/refs/heads/main/captive-browser-ubuntu-chrome.toml ~/.config/captive-browser.toml
```

## Usage

Simply run `captive-browser`, log into the captive portal, and then *quit*q the browser instance.

If the binary is not found, remember to add the go binary `go/bin` folder to the PATH, which you can find with `go env GOPATH` (for example `~/go/bin`).
