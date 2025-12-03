# Getting stated / Use
Simple REST API to insert messages into an IOTA Tangle

## How to build, install, or deploy it
Simply run a docker build command to create the container:
```docker build -t iota_api .```
And execute it:
```docker run -p 5555:5555 iota_api```
Additionally, a Kubernetes depoyment has been created in case you want to use K8s or similar:
 ```kubectl apply -f deployment.yaml```

## Testing
With the Custom API installed you can upload a block into the Tangle with the following command:
```
curl -i -k --location 'http://*API_IP*:30634/upload?node=iota-hornet' \
--header 'Content-Type: application/json' \
--data '{
  "tag": "self.reorquestration",
  "message": {
    "THIS CAN BE": "WHATEVER YOU WANT",
    "AS LONG AS THE": "DATA IS A JSON"
  }
}'
```

Additionally, an endpoint has been opened in KrakenD to upload from outside the cluster, you can do it with the following POST:
```
curl -i -k --location 'http://cf-mvp-domain.aeros-project.eu/iota_api?node=iota-hornet' \
--header 'Content-Type: application/json' \
--header 'Authorization: ••••••' \
--data '{
  "tag": "self.reorquestration",
  "message": {
    "THIS CAN BE": "WHATEVER YOU WANT",
    "AS LONG AS THE": "DATA IS A JSON"
  }
}'
```

You can send the message to any hornet node, just replace the "iota-hornet" in the URL with either any other hornet node (e.g. hornet-4) or just input the IP of the hornet node in question.

The contents need to be in JSON format with the two fields "tag" and "message". The contents of "message" can be whatever you want them to be.

## Credits
This repo is handled by:
Boret98

## Contributing
Pull requests are always appreciated.

## License
```
This is free and unencumbered software released into the public domain.

Anyone is free to copy, modify, publish, use, compile, sell, or
distribute this software, either in source code form or as a compiled
binary, for any purpose, commercial or non-commercial, and by any
means.
In jurisdictions that recognize copyright laws, the author or authors
of this software dedicate any and all copyright interest in the
software to the public domain. We make this dedication for the benefit
of the public at large and to the detriment of our heirs and
successors. We intend this dedication to be an overt act of
relinquishment in perpetuity of all present and future rights to this
software under copyright law.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.
IN NO EVENT SHALL THE AUTHORS BE LIABLE FOR ANY CLAIM, DAMAGES OR
OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE,
ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR
OTHER DEALINGS IN THE SOFTWARE.

For more information, please refer to <http://unlicense.org/>
```
