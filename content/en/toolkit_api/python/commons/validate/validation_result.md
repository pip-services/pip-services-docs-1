---
type: docs
title: "ValidationResult"
linkTitle: "ValidationResult"
gitUrl: "https://github.com/pip-services3-python/pip-services3-commons-python"
description: >
   Result generated by a schema validation
---

### Description

The ValidationResult class provides a representation of the result generated by a schema validation.

### Constructors
Creates a new instance of a validation result and sets its values.
See [ValidationResultType](../validation_result_type)

> ValidationResult(path: str = None, type: [ValidationResultType](../validation_result_type) = None, code: str = None, message: str = None,  expected: Any = None, actual: Any = None)

- **path**: str - a dot notation path of the validated element.
- **type**: [ValidationResultType](../validation_result_type) - a type of the validation result: Information, Warning, or Error.
- **code**: str - an error code.
- **message**: str - human readable message.
- **expected**: Any - value expected by schema validation.
- **actual**: Any - aactual value found by schema validation.


### Instance methods

#### get_actual
Gets the actual value found by schema validation.

> get_actual(): Any

- **returns**: Any - the actual value.


#### get_code
Gets the error code.

> get_code(): str

- **returns**: str - the error code


#### get_expected
Gets the value expected by schema validation.

> get_expected(): Any

- **returns**: Any - the expected value.


#### get_message
Gets the human readable message.

> get_message(): str

- **returns**: str - the result message.


#### get_path
Gets dot notation path of the validated element.

> get_path(): str

- **returns**: str - the path of the validated element.


#### get_type
Gets dot notation path of the validated element.

> get_type(): [ValidationResultType](../validation_result_type)

- **returns**: [ValidationResultType](../validation_result_type) - the type of the validation result.


#### to_json
 Returns the validation result in JSON format.
> to_json(): object