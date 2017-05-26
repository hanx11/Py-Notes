============================================================
16.6. multiprocessing -- Process-based "threading" interface
============================================================

Introduction
------------

multiprocessing is a package that supports spawning processes using an API
similar to the threading module. The multiprocessing package offers both
local and remote concurrency, effectively side-stepping the Global Interpreter
Lock by using subprocesses instead of threads. Due to this, the multiprocessing
module allows the programmer to fully leverage multiple processors on a given 
machine. It runs on both Unix and Windows.

The multiprocessing module also introduces APIs which do not have analogs in the
threading module. A prime example of this is the Pool object which offers a 
convenient means of parallelizing the execution of a function across multiple
input values, distributing the input data across processes (data parallelism).
The following example demonstrates the common practice of defining such functions
in a module so that child processes can successfully import that module. This basic
example of data parallelism using Pool.

.. code:: python

    from multiprocessing import Pool

    def f(x):
        return x*x

    if __name__ == '__main__':
        p = Pool(2)
        print(p.map(f, [1, 2, 3]))

will print to standard output
  [1, 4, 9]

16.6.1.1. The Process class

In multiprocessing, processes are spawned by creating a Process object and then
calling its start() method. Process follows the API of threading.Thread. A trivial
example of a multiprocess program is

.. code:: python 

    from multiprocessing import Process

    def f(name):
        print 'hello', name

    if __name__ == '__main__':
        p = Process(target=f, args('bob', ))
        p.start()
        p.join()

To show the individual process IDs involved, here is an expanded example:

.. code:: python

    from multiprocessing import Process
    import os

    def info(title):
        print title
        print 'module name: ', __name__
        if hasattr(os, 'getppid'):
            print 'parent process: ', os.getppid()
        print 'process id: ', os.getpid()

    def f(name):
        info('function f')
        print 'hello', name

    if __name__ == '__main__':
        info('main line')
        p = Process(target=f, args=('bob',))
        p.start()
        p.join()


16.6.1.2. Exchanging objects between processes

multiprocessing supports two types of communication channel between processes:

**Queues**

The Queue class is a near clone of Queue.Queue. For example:

.. code:: python

    from multiprocessing import Process, Queue

    def f(q):
        q.put([42, None, 'hello'])

    if __name__ == '__main__':
        q = Queue()
        p = Process(target=f, args=(q,))
        p.start()
        print q.get()
        p.join()


