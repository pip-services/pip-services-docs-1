
```go
import (
	conf "github.com/pip-services3-gox/pip-services3-commons-gox/config"
	rlock "github.com/pip-services3-go/pip-services3-redis-go/lock"
)


lock := rlock.NewRedisLock()
lock.Configure(conf.NewConfigParamsFromTuples(
	"connection.host", "localhost",
	"connection.port", 6379,
))

```