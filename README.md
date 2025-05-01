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
java -jar lib/specmatic.jar virtualize
```

### Run Contract Test against the Mock Server
```shell
java -jar lib/specmatic.jar test
```