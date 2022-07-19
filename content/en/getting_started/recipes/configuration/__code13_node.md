
```typescript
let configReader = new JsonConfigReader("config.json");
let parameters = ConfigParams.fromTuples("KEY1_VALUE", 123, "KEY2_VALUE", "ABC");
let result = await configReader.readConfig("correlationId", parameters); // Result: key1=123;key2=ABC


```
