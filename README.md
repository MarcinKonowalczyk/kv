# KV - simple key/value store

Upstream of [mgax/kv](https://github.com/mgax/kv).

KV provides a dictionary-like interface on top of SQLite. Keys can be
unicode strings, numbers or None. Values are stored as JSON.

```python
>>> from kv import KV
>>> db = KV('/tmp/demo.kv')
>>> db['hello'] = 'world'
>>> db[42] = ['answer', 2, {'ultimate': 'question'}]
>>> dict(db)
{42: [u'answer', 2, {u'ultimate': u'question'}], u'hello': u'world'}
```

There is a locking facility that uses SQLite's transaction API::

```python
>>> with kv.lock():
...   l = db[42]
...   l += ['or is it?']
...   db[42] = l
```

And that's about it. The code_ is really simple.

