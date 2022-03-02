
```go
import (
	cconf "github.com/pip-services3-go/pip-services3-commons-go/config"
	aauth "github.com/pip-services3-go/pip-services3-components-go/auth"
)

config := cconf.NewConfigParamsFromTuples(
	"key1.user", "jdoe",
	"key1.pass", "pass123",
	"key2.user", "bsmith",
	"key2.pass", "mypass",
)

credentialStore := aauth.NewEmptyMemoryCredentialStore()
credentialStore.ReadCredentials(config)

```