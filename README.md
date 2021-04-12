
Generated with https://github.com/Mermade/widdershins
Better view: https://aax.api.j-kit.me/redoc/index.html

<!-- Generator: Widdershins v4.0.0 -->

<h1 id="aax-activationservice-api_3">AAX.ActivationService.Api_3 v1.0</h1>

> Scroll down for code samples, example requests and responses. Select a language for code samples from the tabs above or the mobile navigation menu.

<h1 id="aax-activationservice-api_3-activation">Activation</h1>

## Resolves

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'text/plain'
}

result = RestClient.get '/api/v1/Activation/{checksum}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'text/plain'
}

r = requests.get('/api/v1/Activation/{checksum}', headers = headers)

print(r.json())

```

```csharp
using System;
using System.Collections.Generic;
using System.Net.Http;
using System.Net.Http.Headers;
using System.Text;
using System.Threading.Tasks;
using Newtonsoft.Json;

/// <<summary>>
/// Example of Http Client
/// <</summary>>
public class HttpExample
{
    private HttpClient Client { get; set; }

    /// <<summary>>
    /// Setup http client
    /// <</summary>>
    public HttpExample()
    {
      Client = new HttpClient();
    }
    
    /// Make a dummy request
    public async Task MakeGetRequest()
    {
      string url = "/api/v1/Activation/{checksum}";
      var result = await GetAsync(url);
    }

    /// Performs a GET Request
    public async Task GetAsync(string url)
    {
        //Start the request
        HttpResponseMessage response = await Client.GetAsync(url);

        //Validate result
        response.EnsureSuccessStatusCode();

    }
    
    
    
    
    /// Deserialize object from request response
    private async Task DeserializeObject(HttpResponseMessage response)
    {
        //Read body 
        string responseBody = await response.Content.ReadAsStringAsync();

        //Deserialize Body to object
        var result = JsonConvert.DeserializeObject(responseBody);
    }
}

```

`GET /api/v1/Activation/{checksum}`

<h3 id="resolves-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|checksum|path|string|true|The checksum that should be resolved|

> Example responses

> 200 Response

```
"string"
```

<h3 id="resolves-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|string|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|None|

<aside class="success">
This operation does not require authentication
</aside>

## Resolve single activation bytes

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'text/json'
}

result = RestClient.get '/api/v2/Activation/{checksum}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'text/json'
}

r = requests.get('/api/v2/Activation/{checksum}', headers = headers)

print(r.json())

```

```csharp
using System;
using System.Collections.Generic;
using System.Net.Http;
using System.Net.Http.Headers;
using System.Text;
using System.Threading.Tasks;
using Newtonsoft.Json;

/// <<summary>>
/// Example of Http Client
/// <</summary>>
public class HttpExample
{
    private HttpClient Client { get; set; }

    /// <<summary>>
    /// Setup http client
    /// <</summary>>
    public HttpExample()
    {
      Client = new HttpClient();
    }
    
    /// Make a dummy request
    public async Task MakeGetRequest()
    {
      string url = "/api/v2/Activation/{checksum}";
      var result = await GetAsync(url);
    }

    /// Performs a GET Request
    public async Task GetAsync(string url)
    {
        //Start the request
        HttpResponseMessage response = await Client.GetAsync(url);

        //Validate result
        response.EnsureSuccessStatusCode();

    }
    
    
    
    
    /// Deserialize object from request response
    private async Task DeserializeObject(HttpResponseMessage response)
    {
        //Read body 
        string responseBody = await response.Content.ReadAsStringAsync();

        //Deserialize Body to object
        var result = JsonConvert.DeserializeObject(responseBody);
    }
}

```

`GET /api/v2/Activation/{checksum}`

<h3 id="resolve-single-activation-bytes-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|checksum|path|string|true|none|

> Example responses

> 200 Response

```json
{
  "success": true,
  "message": "Unknown Error",
  "checksum": "3eee792cbc9b8e086241becf8b95f133d0b7444da",
  "activationBytes": "12345688"
}
```

<h3 id="resolve-single-activation-bytes-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|[AaxChecksumResponseDto](#schemaaaxchecksumresponsedto)|

<aside class="success">
This operation does not require authentication
</aside>

## Resolve batched activation bytes

> Code samples

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'text/json'
}

result = RestClient.post '/api/v2/Activation',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'text/json'
}

r = requests.post('/api/v2/Activation', headers = headers)

print(r.json())

```

```csharp
using System;
using System.Collections.Generic;
using System.Net.Http;
using System.Net.Http.Headers;
using System.Text;
using System.Threading.Tasks;
using Newtonsoft.Json;

/// <<summary>>
/// Example of Http Client
/// <</summary>>
public class HttpExample
{
    private HttpClient Client { get; set; }

    /// <<summary>>
    /// Setup http client
    /// <</summary>>
    public HttpExample()
    {
      Client = new HttpClient();
    }
    
    
    /// Make a dummy request
    public async Task MakePostRequest()
    {
      string url = "/api/v2/Activation";
      
      string json = @"{
  ""checksums"": [
    ""9eb875b484f87510b88eb389031e06790674193f"",
    ""3eee792cbc9b8e086241becf8b95f133d0b7444da"",
    ""731cf67dddcad97cb5ef95a07a4c4512426927c3""
  ]
}";
      AaxChecksumBatchRequestDto content = JsonConvert.DeserializeObject(json);
      await PostAsync(content, url);
      
      
    }

    /// Performs a POST Request
    public async Task PostAsync(AaxChecksumBatchRequestDto content, string url)
    {
        //Serialize Object
        StringContent jsonContent = SerializeObject(content);

        //Execute POST request
        HttpResponseMessage response = await Client.PostAsync(url, jsonContent);
    }
    
    
    
    /// Serialize an object to Json
    private StringContent SerializeObject(AaxChecksumBatchRequestDto content)
    {
        //Serialize Object
        string jsonObject = JsonConvert.SerializeObject(content);

        //Create Json UTF8 String Content
        return new StringContent(jsonObject, Encoding.UTF8, "application/json");
    }
    
    /// Deserialize object from request response
    private async Task DeserializeObject(HttpResponseMessage response)
    {
        //Read body 
        string responseBody = await response.Content.ReadAsStringAsync();

        //Deserialize Body to object
        var result = JsonConvert.DeserializeObject(responseBody);
    }
}

```

`POST /api/v2/Activation`

> Body parameter

```json
{
  "checksums": [
    "9eb875b484f87510b88eb389031e06790674193f",
    "3eee792cbc9b8e086241becf8b95f133d0b7444da",
    "731cf67dddcad97cb5ef95a07a4c4512426927c3"
  ]
}
```

<h3 id="resolve-batched-activation-bytes-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|[AaxChecksumBatchRequestDto](#schemaaaxchecksumbatchrequestdto)|false|Contains a set of checksums to be resolved|

> Example responses

> 200 Response

```json
[
  {
    "success": true,
    "message": "Unknown Error",
    "checksum": "3eee792cbc9b8e086241becf8b95f133d0b7444da",
    "activationBytes": "12345688"
  }
]
```

<h3 id="resolve-batched-activation-bytes-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|Inline|

<h3 id="resolve-batched-activation-bytes-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[[AaxChecksumResponseDto](#schemaaaxchecksumresponsedto)]|false|none|none|
|» success|boolean|false|none|Indicates wether the activationbytes could be successfully resolved|
|» message|string¦null|false|none|Error message when AAX.ActivationService.Api_3.Models.Dtos.AaxChecksumResponseDto.Success indicates failure|
|» checksum|string¦null|false|none|Copy of the requested checksum|
|» activationBytes|string¦null|false|none|The resulting activation bytes|

<aside class="success">
This operation does not require authentication
</aside>

# Schemas

<h2 id="tocS_AaxChecksumBatchRequestDto">AaxChecksumBatchRequestDto</h2>
<!-- backwards compatibility -->
<a id="schemaaaxchecksumbatchrequestdto"></a>
<a id="schema_AaxChecksumBatchRequestDto"></a>
<a id="tocSaaxchecksumbatchrequestdto"></a>
<a id="tocsaaxchecksumbatchrequestdto"></a>

```json
{
  "checksums": [
    "9eb875b484f87510b88eb389031e06790674193f",
    "3eee792cbc9b8e086241becf8b95f133d0b7444da",
    "731cf67dddcad97cb5ef95a07a4c4512426927c3"
  ]
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|checksums|[string]¦null|false|none|The checksums to be resolved|

<h2 id="tocS_AaxChecksumResponseDto">AaxChecksumResponseDto</h2>
<!-- backwards compatibility -->
<a id="schemaaaxchecksumresponsedto"></a>
<a id="schema_AaxChecksumResponseDto"></a>
<a id="tocSaaxchecksumresponsedto"></a>
<a id="tocsaaxchecksumresponsedto"></a>

```json
{
  "success": true,
  "message": "Unknown Error",
  "checksum": "3eee792cbc9b8e086241becf8b95f133d0b7444da",
  "activationBytes": "12345688"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|success|boolean|false|none|Indicates wether the activationbytes could be successfully resolved|
|message|string¦null|false|none|Error message when AAX.ActivationService.Api_3.Models.Dtos.AaxChecksumResponseDto.Success indicates failure|
|checksum|string¦null|false|none|Copy of the requested checksum|
|activationBytes|string¦null|false|none|The resulting activation bytes|

