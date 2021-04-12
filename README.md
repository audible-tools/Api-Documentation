
# AAX Api Documentation

The aax api allows to obtain the 'activation bytes' for any audible aax file. those Activation bytes are basically the seed for the  en-/decryption keys to retreive raw m4b files.

Also available on [ReDoc](https://aax.api.j-kit.me/ReDoc), [Postman](https://www.postman.com/coderdojo-austria/workspace/aax-lookup-api/overview) and [OpenApi json](https://aax.api.j-kit.me/swagger/v1/swagger.json)


## Best Practices

- !!**Custom headers**!!
	- Please use a custom [User-Agent](https://developer.mozilla.org/de/docs/Web/HTTP/Headers/User-Agent) and/or [Origin](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Origin) (If not coming from the web -> Project site)
	- This helps me evaluating where traffic comes from and making decisions based on that. Thanks! 
- Validate the responses. 
	- Re-Calculate the hash of the response ( [Sample HashAlgorithm](https://github.com/audible-tools/audible-tools.github.io/blob/926a3b6ea8f3bc0d71f294adc78d4bbd545c20ab/src/Utils/AaxHashAlgorithm.js) | [Sample Usage](https://github.com/audible-tools/audible-tools.github.io/blob/926a3b6ea8f3bc0d71f294adc78d4bbd545c20ab/src/ChecksumResolver.js#L150))
- Cache as much as you can
	- Even though, the server is very efficient at what it does, there is no reason to stress things


## v2

Request:

    GET https://aax.api.j-kit.me/api/v2/activation/[ACTIVATION_BYTES]

For e.g:

    GET https://aax.api.j-kit.me/api/v2/activation/9eb875b484f87510b88eb389031e06790674193e

Returns: 

```json
{
	"success": true,
	"activationBytes": "12345678"
}
```


## v1 (not recommended)
Request:

    GET https://aax.api.j-kit.me/api/v1/activation/[ACTIVATION_BYTES]

For e.g:

    GET https://aax.api.j-kit.me/api/v1/activation/9eb875b484f87510b88eb389031e06790674193e

Returns: 

	12345678
    


