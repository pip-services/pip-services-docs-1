
```dart
var config = ConfigParams.fromTuples(['connection.host', 'localhost', 'connection.port', '8080']);

var configReader = MemoryConfigReader();
configReader.configure(config);

var parameters = ConfigParams.fromValue(Platform.environment);
var result = await configReader.readConfig('123', parameters);

```
