When run with cpython, `test_1.py` fails.

```sh-session
$ python3.7 test_1.py
Traceback (most recent call last):
  File "test_1.py", line 8, in <module>
    test_1()
  File "test_1.py", line 5, in test_1
    assert isinstance(Calendar, type)
NameError: name 'Calendar' is not defined
$ python3.7 test_2.py
```

When run with pytest, `test_2.py` fails.

```sh-session
$ pytest
==================================== test session starts =====================================
platform linux -- Python 3.7.0, pytest-3.7.4, py-1.6.0, pluggy-0.7.1
rootdir: /home/ec2-user/relimp, inifile:
collected 2 items

test_1.py .                                                                            [ 50%]
test_2.py F                                                                            [100%]

========================================== FAILURES ==========================================
___________________________________________ test_2 ___________________________________________

    def test_2():
>       assert isinstance(Foo, type)
E       NameError: name 'Foo' is not defined

test_2.py:5: NameError
============================= 1 failed, 1 passed in 0.02 seconds =============================
```

If you want consistent results with direct invocation with cpython, use `python -m pytest` instead.

```sh-session
$ python3.7 -m pytest
==================================== test session starts =====================================
platform linux -- Python 3.7.0, pytest-3.7.4, py-1.6.0, pluggy-0.7.1
rootdir: /home/ec2-user/relimp, inifile:
collected 2 items

test_1.py F                                                                            [ 50%]
test_2.py .                                                                            [100%]

========================================== FAILURES ==========================================
___________________________________________ test_1 ___________________________________________

    def test_1():
>       assert isinstance(Calendar, type)
E       NameError: name 'Calendar' is not defined

test_1.py:5: NameError
============================= 1 failed, 1 passed in 0.03 seconds =============================
```
