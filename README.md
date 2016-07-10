# Erlang

+ ++ --都是对于列表操作的
++[H]++
--[H]
不能--H这样子

### 以end结尾的有：fun、 case of、 if、try catch after
###tuple的element（N,tuple）方法 N>=1不是从0开始
### 布尔表达式（A or B, A and B)表达式A，B都会被执行，尽管可能只需要第一个值就能知道整个布尔表达式的值，短路布尔表达式不一定是两个都会执行
###receive after end receive首先从邮箱里读取所有的邮件 然后才会执行after的部分，after 0或者after 1000 都是在receive之后才有机会执行
after 0:超时为零会让超时的主体部分立刻（不是首先）执行(在分裂出进程的时候就自动执行)，但是在这之前系统会尝试对邮箱里面的消息进行匹配。可以用此特性写出清空邮箱的程序

flush_buffer()->
  receive
    _Any->
      flush_buffer()
    after 0->
      true
  end.
  
当执行完Pid=spawn(test,clock,[]). spawn方法时 Pid进程就已经处于接受消息的状态了

erl -name mynode@127.0.0.1 -setcookie abc


Built-in type	Defined as
term()	any()
binary()	<<_:_*8>>
bitstring()	<<_:_*1>>
boolean()	'false' | 'true'
byte()	0..255
char()	0..16#10ffff
nil()	[]
number()	integer() | float()
list()	[any()]
maybe_improper_list()	maybe_improper_list(any(), any())
nonempty_list()	nonempty_list(any())
string()	[char()]
nonempty_string()	[char(),...]
iodata()	iolist() | binary()
iolist()	maybe_improper_list(byte() | binary() | iolist(), binary() | [])
function()	fun()
module()	atom()
mfa()	{module(),atom(),arity()}
arity()	0..255
identifier()	pid() | port() | reference()
node()	atom()
timeout()	'infinity' | non_neg_integer()
no_return()	none()
