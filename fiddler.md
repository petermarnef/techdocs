# Fiddler

## Capture requests to localhost from Firefox

- `about:config`
- Set preference `network.proxy.allow_hijacking_localhost` to `true`

## Capture request from a .NET app

Add this code to the config file:

``` xml
<system.net>
  <defaultProxy
        enabled = "true"
        useDefaultCredentials = "true">
    <proxy autoDetect="False" bypassonlocal="False" proxyaddress="http://127.0.0.1:8888" usesystemdefault="False" />
  </defaultProxy>
</system.net>
```

And change the url you are calling from `localhost` to `localhost.fiddler`.
