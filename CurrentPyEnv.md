#Current Python Enviroment on Mac

## <font color="#0099ff">Homebrew Python3 [Default]</font>

```
$which python
/usr/local/bin/python
```

```mermaid
graph TD;
AliasDir1(/usr/local/bin/<br>python<br>python3<br>python3.x)
-->
OriginalDir("/usr/local/Cellar/python@3.x/3.x.x/Frameworks/<br>Python.framework/Versions/3.x/bin/python3.x")
AliasDir2("/usr/local/Cellar/python@3.8/3.8.5/bin/<br>python3<br>python3.x") --> OriginalDir
```


## <font color="#0099ff">Homebrew Python2</font>

```mermaid
graph TD;
AliasDir1("/usr/local/Cellar/python@2/2.7.17/bin/<br>python<br>python2<br>python2.7")
-->
OriginalDir("/usr/local/Cellar/python@2/2.7.17/Frameworks/<br>Python.framework/Versions/2.7/bin/python2.7")
```

## <font color="#0099ff">Anaconda Python3</font>

```
$ which python
/Users/jkfan/opt/anaconda3/bin/python
```

```mermaid
graph TD;
Alias1(python)
-->
Original(python3.7)
Alias2(python3) --> Original
Alias3(python3.7m) --> Original
```

## <font color="#0099ff">Built-In Python2</font>

```
$ which python2:
/usr/bin/python2
```

```mermaid
graph TD;
AliasDir1(/usr/bin/<br>python<br>python2<br>python2.7)
-->
Original(/System/Library/Frameworks/Python.framework/<br>Versions/2.7/bin/python2.7)
```