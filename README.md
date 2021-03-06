# freebsd-jitsi-meet-setup
A personal shell script which performs the initial configuration of a jitsi-meet server on FreeBSD

## Prerequisites
- You've installed jitsi-meet, jitsi-videobridge, jicofo, prosody and a webserver (either nginx or apache24) from ports or packages (optionally they can be installed by the script).
- You've got a valid TLS server certificate and a private key for the server. The certificate has to be verifiable by clients' web browsers.

## Usage
- Clone this repository anywhere you want.
- Run 'setup.sh' just after installing the aforementioned ports or packages.
- The script takes three mandatory arguments:
  1. SERVER_FQDN - the server's resolvable domain name.
  2. SERVER_CERT_PATH - a full pathname of the server certificate.
  3. SERVER_KEY_PATH - a full pathname of the server private key.
- If you use apache24 instead of nginx, specify -a flag.
- If you want authentication for room creation, specify -r flag.
- If the server is behind a NAT, specify -N LOCAL:PUBLIC where LOCAL is a private IP address actually assigned to the server and PUBLIC is a public IP address to which the LOCAL address is translated by the NAT.

## Examples
- Nginx, no authentiation and no NAT
  ```
  # ./setup.sh jitsi.example.com /path/to/jitsi.crt /path/to/jitsi.key
  ```

- Apache24, no authentication and no NAT
  ```
  # ./setup.sh -a jitsi.example.com /path/to/jitsi.crt /path/to/jitsi.key
  ```

- Nginx, authentiation and no NAT
  ```
  # ./setup.sh -r jitsi.example.com /path/to/jitsi.crt /path/to/jitsi.key
  ```

- Nginx, no authentiation and NAT
  ```
  # ./setup.sh -N 192.168.10.5:10.1.1.5 jitsi.example.com /path/to/jitsi.crt /path/to/jitsi.key
  ```
