#  AirBnB clone - RESTful API

## Resources
### Read or watch:

- REST API concept page
- [Learn REST: A RESTful Tutorial](https://intranet.alxswe.com/rltoken/rycjU2GvZAlahHa61WWDBg)
- [Designing a RESTful API with Python and Flask](https://intranet.alxswe.com/rltoken/WfKwKtaROCybta0_E849AQ)
- [HTTP access control (CORS)](https://intranet.alxswe.com/rltoken/D55IFF8lgZDLPyIX6b6C5A)
- [Flask cheatsheet](https://intranet.alxswe.com/rltoken/L01qANfgx0al8_an4mtPuw)
- [What are Flask Blueprints, exactly?](https://intranet.alxswe.com/rltoken/QxbV8TCzNl3oP9br8CV5Lw)
- [Flask](https://intranet.alxswe.com/rltoken/OLWDl7iDVpWKykekaznWpQ)
- [Modular Applications with Blueprints](https://intranet.alxswe.com/rltoken/y3Lhj6w1g59MA_HPtc578w)
- [Flask tests](https://intranet.alxswe.com/rltoken/UGo4ArPFHhx-ow2QtZWILA)
- [Flask-CORS](https://intranet.alxswe.com/rltoken/vq8ER3xb99-N2anC-zke3A)


[Codebase](https://github.com/alexaorrico/AirBnB_clone_v2.git)


Tasks

#### 0. Restart from scratch!

No no no! We are already too far in the project to restart everything.

But once again, let’s work on a new codebase.

For this project you will fork this [Codebase](https://github.com/alexaorrico/AirBnB_clone_v2.git):

Update the repository name to `AirBnB_clone_v3`
Update the README.md:
- Add yourself as an author of the project
- Add new information about your new contribution
- Make it better!
If you’re the owner of this codebase, create a new repository called AirBnB_clone_v3 and copy over all files from AirBnB_clone_v2

**Repo:**

GitHub repository: `AirBnB_clone_v3`

#### 1. Never fail!

Since the beginning we’ve been using the unittest module, but do you know why unittests are so important? Because when you add a new feature, you refactor a piece of code, etc… you want to be sure you didn’t break anything.

At Holberton, we have a lot of tests, and they all pass! Just for the Intranet itself, there are:

- 5,213 assertions (as of 08/20/2018)
- 13,061 assertions (as of 01/25/2021)

The following requirements must be met for your project:

- all current tests must pass (don’t delete them…)
- add new tests as much as you can (tests are mandatory for some tasks)

```
guillaume@ubuntu:~/AirBnB_v3$ python3 -m unittest discover tests 2>&1 | tail -1
OK
guillaume@ubuntu:~/AirBnB_v3$ HBNB_ENV=test HBNB_MYSQL_USER=hbnb_test HBNB_MYSQL_PWD=hbnb_test_pwd HBNB_MYSQL_HOST=localhost HBNB_MYSQL_DB=hbnb_test_db HBNB_TYPE_STORAGE=db python3 -m unittest discover tests 2>&1 /dev/null | tail -n 1
OK
guillaume@ubuntu:~/AirBnB_v3$
```

**Repo:**

GitHub repository: `AirBnB_clone_v3`

#### 2. Improve storage

Update DBStorage and FileStorage, adding two new methods. All changes should be done in the branch storage_get_count:

A method to retrieve one object:

- Prototype: def get(self, cls, id):
     - cls: class
    - id: string representing the object ID
- Returns the object based on the class and its ID, or None if not found

A method to count the number of objects in storage:

- Prototype: def count(self, cls=None):
    - cls: class (optional)
- Returns the number of objects in storage matching the given class. If no class is passed, returns the count of all objects in storage.
Don’t forget to add new tests for these 2 methods on each storage engine.

```
guillaume@ubuntu:~/AirBnB_v3$ cat test_get_count.py
#!/usr/bin/python3
""" Test .get() and .count() methods
"""
from models import storage
from models.state import State

print("All objects: {}".format(storage.count()))
print("State objects: {}".format(storage.count(State)))

first_state_id = list(storage.all(State).values())[0].id
print("First state: {}".format(storage.get(State, first_state_id)))

guillaume@ubuntu:~/AirBnB_v3$
guillaume@ubuntu:~/AirBnB_v3$ HBNB_MYSQL_USER=hbnb_dev HBNB_MYSQL_PWD=hbnb_dev_pwd HBNB_MYSQL_HOST=localhost HBNB_MYSQL_DB=hbnb_dev_db HBNB_TYPE_STORAGE=db ./test_get_count.py
All objects: 1013
State objects: 27
First state: [State] (f8d21261-3e79-4f5c-829a-99d7452cd73c) {'name': 'Colorado', 'updated_at': datetime.datetime(2017, 3, 25, 2, 17, 6), 'created_at': datetime.datetime(2017, 3, 25, 2, 17, 6), '_sa_instance_state': <sqlalchemy.orm.state.InstanceState object at 0x7fc0103a8e80>, 'id': 'f8d21261-3e79-4f5c-829a-99d7452cd73c'}
guillaume@ubuntu:~/AirBnB_v3$
guillaume@ubuntu:~/AirBnB_v3$ ./test_get_count.py
All objects: 19
State objects: 5
First state: [State] (af14c85b-172f-4474-8a30-d4ec21f9795e) {'updated_at': datetime.datetime(2017, 4, 13, 17, 10, 22, 378824), 'name': 'Arizona', 'id': 'af14c85b-172f-4474-8a30-d4ec21f9795e', 'created_at': datetime.datetime(2017, 4, 13, 17, 10, 22, 378763)}
guillaume@ubuntu:~/AirBnB_v3$
```

For this task, you must make a pull request on GitHub.com, and ask at least one of your peer to review and merge it.

**Repo:**

- GitHub repository: `AirBnB_clone_v3`
- File: `models/engine/db_storage.py, models/engine/file_storage.py, tests/test_models/test_engine/test_db_storage.py, tests/test_models/test_engine/test_file_storage.py`





