# FreeRDP/Remmina open issues, labeled SSH

The last two columns are used to flag if a certain issues is easily solved with the specified library (from which version)

| ISSUE | Description | Labels | libssh | libssh2 |
|-------|-------------|--------|--------|---------|
| [985](https://github.com/FreeRDP/Remmina/issues/985) | Connection not kept alive using SSH in Remmina 1.2e | [bug] [SSH] | ??? | libssh2 1.2.5 |
| [984](https://github.com/FreeRDP/Remmina/issues/984) | Remmina can't connect to key based SSH server running on non-standard port [unconfirmed] [SSH] | | |
| [983](https://github.com/FreeRDP/Remmina/issues/983) | Remmina can't connect to system that has only modern KEX algorithms enabled using SSHe | [enhancement] [SSH] | | |
| [982](https://github.com/FreeRDP/Remmina/issues/982) | Mosh/other clients support | [enhancement] [SSH] | Not libssh related | Not libssh2 related |
| [975](https://github.com/FreeRDP/Remmina/issues/975) | SSH windows closes without messagee | [SSH] [unconfirmed] | | |
| [919](https://github.com/FreeRDP/Remmina/issues/919) | FIDO U2F Security Key to create SSH Tunnel for RDP | [enhancement] [security] [SSH] 1 | | |
| [909](https://github.com/FreeRDP/Remmina/issues/909) | Frequent disconnection during ssh connection| [notabug] [SSH] | | |
| [808](https://github.com/FreeRDP/Remmina/issues/808) | Keyboard shortcut for "Open Secure Shell in new terminal" and other features in Tools| [enhancement] [SSH] | | |
| [708](https://github.com/FreeRDP/Remmina/issues/708) | the checkbox, 'Save SSH Password',  greyed out. | [enhancement] [SSH] | | |
| [584](https://github.com/FreeRDP/Remmina/issues/584) | External tools broken? [enhancement] [SSH] | | |
| [235](https://github.com/FreeRDP/Remmina/issues/235) | Remmina doesn't respect ssh config files... | [SSH] | | |
| [176](https://github.com/FreeRDP/Remmina/issues/176) | SSH: missed check availability of PubkicKey Auth on remote host before asking passphrase | [SSH] | | |

# libssh2 VS libssh

libssh2 and libssh both provide an API to develop SSH based applications.

Here's an attempt to put some light on the differences between them.

## libssh2

* License: [3-clause BSD License](https://en.wikipedia.org/wiki/BSD_licenses#3-clause_license_.28.22Revised_BSD_License.22.2C_.22New_BSD_License.22.2C_or_.22Modified_BSD_License.22.29)
* Developped in: C (30218 SLOC), sh (1102 SLOC), Perl (65 SLOC), Lisp (33 SLOC), AWK (23 SLOC)
* NUmber of functions: 170
* Key Exchange Methods: diffie-hellman-group1-sha1, diffie-hellman-group14-sha1, diffie-hellman-group-exchange-sha1, diffie-hellman-group-exchange-sha256
* Hostkey Types: ssh-rsa, ssh-dss
* Ciphers: aes256-ctr, aes192-ctr, aes128-ctr, aes256-cbc (rijndael-cbc@lysator.liu.se), aes192-cbc, aes128-cbc, 3des-cbc, blowfish-cbc, cast128-cbc, arcfour, arcfour128, none
* Compression Schemes: zlib, zlib@openssh.com, none
* MAC hashes: hmac-sha2-256, hmac-sha2-512, hmac-sha1, hmac-sha1-96, hmac-md5, hmac-md5-96, hmac-ripemd160 (hmac-ripemd160@openssh.com), none
* Authentication: none, password, public-key, hostbased, keyboard-interactive
* Channels: shell, exec (incl. SCP wrapper), direct-tcpip, subsystem
* Global Requests: tcpip-forward
* Channel Requests: x11, pty, exit-signal, keepalive@openssh.com
* Subsystems: sftp(version 3), publickey(version 2)
* SFTP: statvfs@openssh.com, fstatvfs@openssh.com
* Thread-safe: just don't share handles simultaneously
* Non-blocking: it can be used both blocking and non-blocking
* Your sockets: the app hands over the socket, calls select() etc.
* OpenSSL, Libgcrypt or WinCNG (native since Windows Vista): builds with either

## libssh

* License: [GNU Lesser General Public License](https://www.gnu.org/licenses/old-licenses/lgpl-2.1.html)
* Developped in: C (46021 SLOC), C++ (1181 SLOC), sh (186 SLOC), Python (9 SLOC)
* NUmber of functions: 213
* Key Exchange Methods: curve25519-sha256@libssh.org, ecdh-sha2-nistp256, diffie-hellman-group1-sha1, diffie-hellman-group14-sha1
* Hostkey Types: ssh-ed25519, ecdsa-sha2-nistp256, ecdsa-sha2-nistp384, ecdsa-sha2-nistp521, ssh-rsa, ssh-dss, ssh-rsa, ssh-dss
* Ciphers: aes256-ctr, aes192-ctr, aes128-ctr, aes256-cbc (rijndael-cbc@lysator.liu.se), aes192-cbc, aes128-cbc, 3des-cbc, blowfish-cbc, none
* Compression Schemes: zlib, zlib@openssh.com, none
* MAC hashes: hmac-sha1, none
* Authentication: none, password, public-key, hostbased, keyboard-interactive, gssapi-with-mic
* Channels: shell, exec (incl. SCP wrapper), direct-tcpip, subsystem, auth-agent-req@openssh.com
* Global Requests: tcpip-forward, forwarded-tcpip
* Channel Requests: x11, pty, exit-status, signal, exit-signal, keepalive@openssh.com, auth-agent-req@openssh.com
* Subsystems: sftp(version 3), OpenSSH Extensions
* SFTP: statvfs@openssh.com, fstatvfs@openssh.com
* Thread-safe: Just don't share sessions
* Non-blocking: it can be used both blocking and non-blocking
* Your sockets: the app hands over the socket, or uses libssh sockets
* OpenSSL or gcrypt: builds with either
* Client and server support
* SSHv2 and SSHv1 protocol support
* Supports Linux, UNIX, BSD, Solaris, OS/2 and Windows
* Automated test cases with nightly tests
* Event model based on poll(2), or a poll(2)-emulation.

## Tables

| Library | Number of available functions              |
|---------|-------------------------------------------:|
| libssh2 | 170 |
| libssh  | 213 |

| item | libssh2 | libssh |
|------|---------|--------|
| Licence  | BSD  | LGPL |
| Server-side support  | no  | yes |
| GSSAPI authentication  | no  | yes |
| Eliptic Curve Key Exchange  | no  | yes |
| Eliptic Curve Hostkeys  | no  | yes |
| Automated test cases with nightly tests  | no (tests available)  | yes |
| Stable API  | yes  | mostly |
| C compatibility  | C89  | C99 |
| strict namespace  | yes  | yes |
| man pages for all functions  | yes  | no |
| Doxygen documentation for all functions  | no  | yes |
| Tutorial  | no  | yes |
| SSHv1 support  | no  | yes |
| Build concept  | Autotools and CMake | CMake |

