Minimal Repro for python/mypy#8481
==================================

This fails:

```
$ mypy --no-implicit-reexport pkg/a.py
Traceback (most recent call last):
  File "/home/rraval/.local/share/virtualenvs/encircle/bin/mypy", line 8, in <module>
    sys.exit(console_entry())
  File "/home/rraval/.local/share/virtualenvs/encircle/lib/python3.6/site-packages/mypy/__main__.py", line 8, in console_entry
    main(None, sys.stdout, sys.stderr)
  File "mypy/main.py", line 90, in main
  File "mypy/build.py", line 180, in build
  File "mypy/build.py", line 254, in _build
  File "mypy/build.py", line 2630, in dispatch
  File "mypy/build.py", line 2953, in process_graph
  File "mypy/build.py", line 3070, in process_stale_scc
  File "mypy/build.py", line 2232, in write_cache
  File "mypy/build.py", line 1445, in write_cache
  File "mypy/nodes.py", line 303, in serialize
  File "mypy/nodes.py", line 3098, in serialize
  File "mypy/nodes.py", line 3034, in serialize
AssertionError
```

This seems to work:

```
$ mypy pkg/a.py
Success: no issues found in 1 source file
```

Version info:

```
$ mypy --version
mypy 0.790
```
