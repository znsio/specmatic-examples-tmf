# Specmatic Examples for TMF APIs
Specmatic Example Validation and Generation for TMF API

### Validate Inline Examples
```shell
java -jar lib/specmatic.jar examples validate --examples-to-validate=inline --spec-file specs/TMF621-Trouble_Ticket-v5.0.0.oas.yaml
```

### Export Inline Examples to External Files
```shell
java -jar lib/specmatic.jar examples export --spec-file specs/TMF621-Trouble_Ticket-v5.0.0.oas.yaml
```

### Load External Examples in an interactive Example UI
```shell
java -jar lib/specmatic.jar examples interactive --spec-file specs/TMF621-Trouble_Ticket-v5.0.0.oas.yaml
```
#### Docker version
```shell
docker pull znsio/specmatic-openapi
docker run \
      -p 9001:9001 \
      -v "$PWD/.specmatic/repos/specmatic-license.txt:/usr/src/app/specmatic-license.txt" \
      -v "$PWD/specs/TMF621-Trouble_Ticket-v5.0.0.oas.yaml:/usr/src/app/TMF621-Trouble_Ticket-v5.0.0.oas.yaml" \
      -v "$PWD/specmatic.yaml:/usr/src/app/specmatic.yaml" \
      -v "$PWD/specs/TMF621-Trouble_Ticket-v5.0.0.oas_examples:/usr/src/app/TMF621-Trouble_Ticket-v5.0.0.oas_examples" \
      -v "$PWD/specs/TMF621-Trouble_Ticket-v5.0.0.oas_dictionary.yaml:/usr/src/app/TMF621-Trouble_Ticket-v5.0.0.oas_dictionary.yaml" \
      -e SPECMATIC_LICENSE_PATH=/usr/src/app/specmatic-license.txt \
      znsio/specmatic-openapi examples interactive --spec-file TMF621-Trouble_Ticket-v5.0.0.oas.yaml
```

### Generate Dictionary
```shell
java -jar lib/specmatic.jar examples dictionary --spec-file specs/TMF621-Trouble_Ticket-v5.0.0.oas.yaml
```

### Start Interactive Example Server with Dictionary
```shell
java -jar lib/specmatic.jar examples interactive --dictionary specs/TMF621-Trouble_Ticket-v5.0.0.oas_dictionary.yaml --spec-file specs/TMF621-Trouble_Ticket-v5.0.0.oas.yaml
```

### Validate Inline Examples in the updated Spec
```shell
java -jar lib/specmatic.jar examples validate --examples-to-validate=inline --spec-file specs/TMF621-Trouble_Ticket-v5.0.0.oas-updated.yaml
```

### Start Mock Server
```shell
java -jar lib/specmatic.jar virtualize --port 9003
```

### Check if the Mock Server is up using curl
```shell
curl -X GET http://localhost:9003/troubleTicket/1002
```

### Run Contract Test against the Mock Server
```shell
java -jar lib/specmatic.jar test --testBaseURL=http://localhost:9003 --filter="PATH!='/hub*' && PATH!='/listener/*'"
```

### Run Actual Trouble Ticket API Server
```shell
docker compose up
```
### Run Contract Test against the actual API server
```shell
java -DMAX_TEST_REQUEST_COMBINATIONS=1 -jar lib/specmatic.jar test --testBaseURL=http://localhost:8621/tmf-api/troubleTicket/v5 --filter="PATH!='/hub*' && PATH!='/listener/*' && STATUS!='202'"
```

### Test API Drift
```shell
java -jar lib/specmatic.jar compare specs/TMF621-Trouble_Ticket-v5.0.0.oas.yaml specs/TMF621-Trouble_Ticket-v5.0.0.oas_new.yaml
```