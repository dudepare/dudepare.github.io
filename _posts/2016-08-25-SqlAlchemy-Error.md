---
layout: post
date: 25 August 2016
title: SqlAlchemy Error
category: programming
---

## Error

    sqlalchemy.exc.TimeoutError: QueuePool limit of size 5 overflow 10 reached, connection timed out, timeout 30


I am working on a Pyramid web app. A new team member is setting up his development environment when this error occurred. Of course I have been working on this web app for a good number of months now. I haven't encountered this error on my machine and in production. 
The first instinct is to go on to Stack Overflow and search for the exact error. I found this [article](http://stackoverflow.com/questions/3360951/sql-alchemy-connection-time-out). So I looked at the code and searched for any sessions that needed closing. I found some but I asked first on the IRC channel #sqlalchemy on freenode if those sessions needed to be closed. Apparently not. 

The day ended with the error still left unsolved.

## Fix 

The next day, I had a few ideas to try out. To install and develop the web app, my instructions was:

    $ python setup.py develop
  
Then I tried 

    $ pip install -e .

This command did its magic. The webapp remained stable and does not show the error anymore. I hope this helps others who encountered the same error.

## Complete error message

    2016-08-23 15:15:51,553 ERROR [waitress] Exception when serving /organisations/
    Traceback (most recent call last):
      File "/home/<user>/.virtualenvs/simtrack/lib/python3.5/site-packages/SQLAlchemy-0.9.10-py3.5-linux-x86_64.egg/sqlalchemy/pool.py", line 968, in _do_get
      return self._pool.get(wait, self._timeout)
      File "/home/<user>/.virtualenvs/simtrack/lib/python3.5/site-packages/SQLAlchemy-0.9.10-py3.5-linux-x86_64.egg/sqlalchemy/util/queue.py", line 156, in get
      raise Empty
    sqlalchemy.util.queue.Empty
    
    During handling of the above exception, another exception occurred:
    
    Traceback (most recent call last):
      File "/home/<user>/.virtualenvs/simtrack/lib/python3.5/site-packages/waitress-0.8.11b0-py3.5.egg/waitress/channel.py", line 338, in service
      task.service()
      File "/home/<user>/.virtualenvs/simtrack/lib/python3.5/site-packages/waitress-0.8.11b0-py3.5.egg/waitress/task.py", line 169, in service
      self.execute()
      File "/home/<user>/.virtualenvs/simtrack/lib/python3.5/site-packages/waitress-0.8.11b0-py3.5.egg/waitress/task.py", line 392, in execute
      app_iter = self.channel.server.application(env, start_response)
      File "/home/<user>/.virtualenvs/simtrack/lib/python3.5/site-packages/pyramid-1.5.8-py3.5.egg/pyramid/router.py", line 242, in __call__
      response = self.invoke_subrequest(request, use_tweens=True)
      File "/home/<user>/.virtualenvs/simtrack/lib/python3.5/site-packages/pyramid-1.5.8-py3.5.egg/pyramid/router.py", line 220, in invoke_subrequest
      request._process_response_callbacks(response)
      File "/home/<user>/.virtualenvs/simtrack/lib/python3.5/site-packages/pyramid-1.5.8-py3.5.egg/pyramid/request.py", line 84, in _process_response_callbacks
      callback(self, response)
      File "/home/<user>/workspace/simtrack/simtrack/authentication.py", line 278, in session_callback
      self.persist()
      File "/home/<user>/.virtualenvs/simtrack/lib/python3.5/site-packages/Beaker-1.8.0-py3.5.egg/beaker/session.py", line 735, in persist
      self._session().save()
      File "/home/<user>/.virtualenvs/simtrack/lib/python3.5/site-packages/Beaker-1.8.0-py3.5.egg/beaker/session.py", line 433, in save
      self.namespace.release_write_lock()
      File "/home/<user>/.virtualenvs/simtrack/lib/python3.5/site-packages/Beaker-1.8.0-py3.5.egg/beaker/container.py", line 229, in release_write_lock
      self.close(checkcount=True)
      File "/home/<user>/.virtualenvs/simtrack/lib/python3.5/site-packages/Beaker-1.8.0-py3.5.egg/beaker/container.py", line 252, in close
      self.do_close()
      File "/home/<user>/.virtualenvs/simtrack/lib/python3.5/site-packages/Beaker-1.8.0-py3.5.egg/beaker/ext/database.py", line 148, in do_close
      data=self.hash, accessed=datetime.now())
      File "/home/<user>/.virtualenvs/simtrack/lib/python3.5/site-packages/SQLAlchemy-0.9.10-py3.5-linux-x86_64.egg/sqlalchemy/sql/base.py", line 386, in execute
      return e._execute_clauseelement(self, multiparams, params)
      File "/home/<user>/.virtualenvs/simtrack/lib/python3.5/site-packages/SQLAlchemy-0.9.10-py3.5-linux-x86_64.egg/sqlalchemy/engine/base.py", line 1867, in _execute_clauseelement
      connection = self.contextual_connect(close_with_result=True)
      File "/home/<user>/.virtualenvs/simtrack/lib/python3.5/site-packages/SQLAlchemy-0.9.10-py3.5-linux-x86_64.egg/sqlalchemy/engine/base.py", line 1908, in contextual_connect
      self.pool.connect(),
      File "/home/<user>/.virtualenvs/simtrack/lib/python3.5/site-packages/SQLAlchemy-0.9.10-py3.5-linux-x86_64.egg/sqlalchemy/pool.py", line 342, in connect
      return _ConnectionFairy._checkout(self)
      File "/home/<user>/.virtualenvs/simtrack/lib/python3.5/site-packages/SQLAlchemy-0.9.10-py3.5-linux-x86_64.egg/sqlalchemy/pool.py", line 649, in _checkout
      fairy = _ConnectionRecord.checkout(pool)
      File "/home/<user>/.virtualenvs/simtrack/lib/python3.5/site-packages/SQLAlchemy-0.9.10-py3.5-linux-x86_64.egg/sqlalchemy/pool.py", line 444, in checkout
      rec = pool._do_get()
      File "/home/<user>/.virtualenvs/simtrack/lib/python3.5/site-packages/SQLAlchemy-0.9.10-py3.5-linux-x86_64.egg/sqlalchemy/pool.py", line 977, in _do_get
      (self.size(), self.overflow(), self._timeout))
    sqlalchemy.exc.TimeoutError: QueuePool limit of size 5 overflow 10 reached, connection timed out, timeout 30
