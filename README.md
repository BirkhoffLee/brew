# homebrew-birkhoff

My Homebrew formulas

## cURL

Patched from the formula provided by the core, I added support for `--dns-server` and http/3 by [quiche](https://github.com/cloudflare/quiche).

```shell
$ brew install BirkhoffLee/birkhoff/curl
==> Tapping birkhofflee/birkhoff
Cloning into '/opt/homebrew/Library/Taps/birkhofflee/homebrew-birkhoff'...
remote: Enumerating objects: 9, done.
remote: Counting objects: 100% (9/9), done.
remote: Compressing objects: 100% (7/7), done.
remote: Total 9 (delta 1), reused 0 (delta 0), pack-reused 0
Receiving objects: 100% (9/9), done.
Resolving deltas: 100% (1/1), done.
Tapped 1 formula (13 files, 11.4KB).
==> Fetching birkhofflee/birkhoff/curl
==> Downloading https://github.com/curl/curl/commit/3103de2053ca8cacf9cdbe78764ba6814481709f.patch?full_index=1
Already downloaded: /Users/birkhoff/Library/Caches/Homebrew/downloads/387c8bbb096c86b107b91259750d701ccb55547d2864a8850d6b806ae15cc00c--3103de2053ca8cacf9cdbe78764ba6814481709f.patch
==> Downloading https://github.com/curl/curl/commit/87ed650d04dc1a6f7944a5d952f7d5b0934a19ac.patch?full_index=1
Already downloaded: /Users/birkhoff/Library/Caches/Homebrew/downloads/0164b2b6cd070f78194ea0fbacde8e8fc660b1baf1903ceb626090e8fc992790--87ed650d04dc1a6f7944a5d952f7d5b0934a19ac.patch
==> Downloading https://curl.se/download/curl-7.88.0.tar.bz2
Already downloaded: /Users/birkhoff/Library/Caches/Homebrew/downloads/222513b1fd3999c257320dc64972e0f30a02d29b04bd4eea359f130209329df0--curl-7.88.0.tar.bz2
==> Installing curl from birkhofflee/birkhoff
==> Patching
==> Applying 3103de2053ca8cacf9cdbe78764ba6814481709f.patch
patching file 'lib/http2.c'
==> Applying 87ed650d04dc1a6f7944a5d952f7d5b0934a19ac.patch
patching file 'lib/http2.c'
==> ./configure --prefix=/opt/homebrew/Cellar/curl/7.88.0_1 --with-ssl=/opt/homebrew/opt/openssl@1.1 --without-ca-bundle --without-ca-path --wit
==> make install
==> make install -C scripts
==> Caveats
curl is keg-only, which means it was not symlinked into /opt/homebrew,
because macOS already provides this software and installing another version in
parallel can cause all kinds of trouble.

If you need to have curl first in your PATH, run:
  echo 'export PATH="/opt/homebrew/opt/curl/bin:$PATH"' >> ~/.zshrc

For compilers to find curl you may need to set:
  export LDFLAGS="-L/opt/homebrew/opt/curl/lib"
  export CPPFLAGS="-I/opt/homebrew/opt/curl/include"

For pkg-config to find curl you may need to set:
  export PKG_CONFIG_PATH="/opt/homebrew/opt/curl/lib/pkgconfig"

zsh completions have been installed to:
  /opt/homebrew/opt/curl/share/zsh/site-functions
==> Summary
🍺  /opt/homebrew/Cellar/curl/7.88.0_1: 510 files, 4.2MB, built in 33 seconds
==> Running `brew cleanup curl`...
Disable this behaviour by setting HOMEBREW_NO_INSTALL_CLEANUP.
Hide these hints with HOMEBREW_NO_ENV_HINTS (see `man brew`).

$ curl --dns-server 1.1.1.1 --http3-only -vI4 https://cloudflare-quic.com/
*   Trying 104.22.9.38:443...
*  subjectAltName: host "cloudflare-quic.com" matched cert's "cloudflare-quic.com"
* Connected to cloudflare-quic.com (104.22.9.38) port 443 (#0)
* using HTTP/3
* h2h3 [:method: HEAD]
* h2h3 [:path: /]
* h2h3 [:scheme: https]
* h2h3 [:authority: cloudflare-quic.com]
* h2h3 [user-agent: curl/8.0.1]
* h2h3 [accept: */*]
* Using HTTP/3 Stream ID: 0 (easy handle 0x120009200)
> HEAD / HTTP/3
> Host: cloudflare-quic.com
> user-agent: curl/8.0.1
> accept: */*
> 
< HTTP/3 200 
HTTP/3 200 
< date: Thu, 11 May 2023 09:29:24 GMT
date: Thu, 11 May 2023 09:29:24 GMT
< content-type: text/html
content-type: text/html
< content-length: 109425
content-length: 109425
< server: cloudflare
server: cloudflare
< cf-ray: 7c5965b67e92afdb-NRT
cf-ray: 7c5965b67e92afdb-NRT
< alt-svc: h3=":443"; ma=86400, h3-29=":443"; ma=86400
alt-svc: h3=":443"; ma=86400, h3-29=":443"; ma=86400
* Connection #0 to host cloudflare-quic.com left intact
```
