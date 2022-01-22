
```python
from pip_services3_commons.commands import ICommandable
from pip_services3_commons.config import IConfigurable
from pip_services3_commons.refer import IReferences, IReferenceable


class HelloFriendController(IConfigurable, ICommandable, IReferenceable):
    __defaultName = None
    __command_set: 'FriendsCommandSet' = None

    __persistence: 'HelloFriendPersistence' = None

    def __init__(self):
        self.__defaultName = "Pip User"

    def configure(self, config):
        self.__defaultName = config.get_as_string_with_default("default_name", self.__defaultName)

    def set_references(self, references: IReferences):
        self.__persistence = references.get_one_required(Descriptor("hello-friend", "persistence", "*", "*", "1.0"))

    def greeting(self):
        filter = FilterParams.from_tuples('type', 'friend')
        selected_friend = self.__persistence.get_one_random(None, filter)
        name2 = selected_friend.name

        return f"Hello, {name2} !"
```