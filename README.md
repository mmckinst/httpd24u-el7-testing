This is relevant to https://github.com/iuscommunity-pkg/httpd24u/issues/5 .

Directions mostly came from https://icing.github.io/mod_h2/howto.html

To test:

```
vagrant up
curl --http2 -v 'http://127.0.0.1:8080/' >/dev/null
```
