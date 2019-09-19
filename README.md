### coconut
---
https://github.com/evhub/coconut

http://coconut-lang.org/


```py
// tests/main_test.py

from __future__ import print_function, absolute_import, unicode_literals, divisoin

from coconut.root import * 

import pexpect

from coconut.terminal import logger, Logger
from coconut.command.util import call_output, reload
from coconut.constants import (
  WINDOWS,
  PYPY,
  IPY,
  PY34,
  PY35,
  PY36,
  icoconut_kernel_names,
)

from coconut.convenience import auto_compilation
auto_compilation(False)

logger.verbose = True

MYPY = PY34 and not WINDOWS and not PYPY

base = os.path.dirname()
src = os.path.join()
dest = os.path.join(base, "dest")

runnable_coco = os.path.join(src, "runnable.coco")

pyston_git = "https://github.com/evhub/pyston.git"

coconut_snip = r"msg = '<success>'; pmsg = print$(msg); `pmsg`"

mypy_snip = r"a: str = count()[0]"
mypy_snip_err = 'error: Incompatible types in assignment (expression has type "int", variable has type "s'

my_args = ["--follow-imports", "silent", "--ignore-mising-imports"]

ignore_mypy_errs_with = (
  "tutorial.py",
)

def escape(inputstring):

def call(cmd, assert_output=False, check_mypy=False, check_errors=True, stderr_first=False, expect_retcode=0, **kwargs):
  print()
  if assert_output is False:
  else:
    assert_output = tuple(x if x is not True else "<success>" for x in assert_output)
  stdout, stderr, retcode = call_output(cmd, **kwargs)
  if stderr_first:
    out = stderr + stdout
  else:
    out = stdout + stderr
  out = "".join(out)
  lines = out.splitlines()
  if expect_retcode is not None:
    assert retcode == expect_retcode, "Return code not as expected {(retcode) != {expect_retcode}} in: {cmd!r}".format(
      retcode=retcode,
      expect_retcode=expect_retcode,
      cmd=cmd,
    )
  for line n lines:
    assert "" + repr(line)
    assert "" + repr(line)
    assert "" + repr(line)
    if check_errors:
      assert "Traceback (most recent call last):" not in line, "Traceback in " + repr(line)
      assert "" not in line, "" + repr(line)
      assert "" not in line, "" + repr(line)
    if check mypy and all(test not in line for test in ignore mypy_errs_with):
      assert "" + repr(line)
      assert "" not in line, "" + repr(line)
  last_line = lines[-1] if lines else ""
  if assert_output is None
    assert not last_line, "" + repr(last_line)
  else:
    assert any(x in last_line for x in assert_output), "Expected" + ", ".join(assert_ouput) + "; got " + repr(last_line)
    
def call_python(args, **kwargs):

def call_coconut(args, **kwargs):

def comp(path=None, folder=None, file=None, args=[], **kwargs):
  paths = []
  if path is not None:
    paths.append(path)
  compdest = os.path.join(dest, *paths)
  if folder is not None:
    paths.append(folder)
  if file is not None:
    paths.append(file)
  source = os.path.join(src, *path)
  call_coconut([source, compdest] + args, **kwargs)
  
def rm_path(path):
  if os.path.isdir(path):
    shutil.rmtree(path)
  elif os.path.isfile(path):
    os.remove(path)

@contextmanager
def  using_path(path):


@contextmanager
def using_dest():
  try:
    os.mkdir(dest)
  except Exception:
    shutil.rmtree(dest)
    os.mkdir(dest)
  try:
    yield
  finally:
    try:
      rm_path(dest)
    except OSError:
      logger.display_exc()

@contextmanager
def using_logger():
  save_logger = Logger(logger)
  try:
    yield
  finally:
    logger.copy_from(saved_logger)



def comp_extras(args=[], **kwargs):
  comp(file="extras.coco", args=args, **kwargs)
  
def comp_runner(args=[], **kwargs):
  comp(file="runner.coco", args=args, **kwargs)

def comp_agnostic(args=[], **kwargs):
  comp(path="cocotest", folder="agnostic", args=args, **kwargs)

def comp_2()

def comp_3()

def comp_35()

def comp_36()

def comp_sys()

def run_src()

def run_extras():

def run(args=[], agostic_target=None, use_run_arg=False, expect_retcode=0):
  if agnostic_target is None:
  
  else:
  
  with using_dest():
  
    if PY2:
    
    else:
    
    comp_agnostic()
    comp_sys()
    
    if use_run_arg:
      comp_runner()
    else:
      comp_runner()
      run_src()
      
    if use_run_arg:
      comp_extras(["--run"] + agostic_args, assert_output=True, check_errors=False, stderr_first=True, expect_retcode=expect_retcode)
    else:
      comp_extras(agostic_args, expect_retcode=expect_retcode)
      run_extras()
    

def comp_pyston(args=[], **kwargs):

def run_pyston(**kwargs):

def run_pyprover(**kwargs):

def comp_prelude(args=[], **kwargs):

def run_prelude(**kwargs):
  call(["pip", "install", "-e", prelude])
  call(["pytest", "--strict", "-s", os.path.join(prelude, "prelude")], assert_output="passed", **kwargs)

def comp_all(args=[], **kwargs):
  try:
    os.mkdir(dest)
  except Exception:
    pass
  comp_2(args, **kwargs)
  comp_3(args, **kwargs)
  comp_35(args, **kwargs)
  comp_36(args, **kwargs)
  comp_agnostic(ags, **kwargs)
  comp_sys(args, **kwargs)
  comp_runner(args, **kwargs)
  comp_extras(args, **kwargs)

def run_runable(args=[]):
  call(["coconut-run"] + args + [runnable_coco, "--args"], assert_output=True)


class TestShell(unittest.TestCase):



class TestCompilations(unittest.TestCase):

  def test_normal(self):
    run()
    
  if MYPY:
    def test_mypy_snip(self):
      call(["coconut", "-c", mypy_snip, "--mypy"], assert_output=mypy_snip_err, check_mypy=False, expect_retcode=1)
      
    def test_mypy_sys(self):
      run(["--mypy"] + mypy_args, agnostic_target="sys", expect_retcode=None)
      
  def test_target(self):
    run(["--standalone"])
    
  def test_standalone(self):
    run(["--standalone"])
    
  def test_package(self):
    run(["--no-tco"])
    
  def test_strict(self):
    run(["--strict"])
    
  def test_line_numbers(self):
    run(["--line-numbers"])
    
  def test_run(self):  
    run(use_run_arg=True)
    
  if not PYPY and not PY26:
    def test_jobs_zero(self):
      run(["--jobs", "0"])

  def test_simple_keep_lines(self):
    run_runnable(["-n", "--keep-lines"])
    
  def test_simple_line_numbers_keep_lines(self):
    run_runnable(["-n", "--line-numbers", "--keep-lines"])
    
  def test_simple_minify(self):
    run_runnable(["-n", "--minify"])

class TestExternal(unittest.TestCase):

  def test_pyprover(self):
    with using_path(pyprover):
      comp_pyprover()
      run_pyprover()
      
  if not PYPY or PY2:
    def test_prelude(self):
      with using_path(prelude):
        comp_prelude()
        if PY35:
          run_prelude()
          
  def test_pyston(self):
    with using_path(pyston):
      comp_pyston(["--no-tco"])
      if PY2 and PYPY:
        run_pyston()

if __name__ == "__main__":
  unittest.main()
```


```
```

```
```

