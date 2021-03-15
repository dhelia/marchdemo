# marchdemo

The below command will help you get the latest SHA of your main branch (or any other branch like master)

**Command**
```
git ls-remote <GIT REPO URL/CLONE REPO URL> | awk "/<BRANCH NAME>/ {print\$1}"
```

**Example**
```
git ls-remote https://github.com/dhelia/marchdemo.git | awk "/main/ {print \$1}"
```

The below command will help you get the name of files that changed between two SHA(s)

**Command**
```
git diff <SHA1> <SHA2> --name-only
```

**Example**
```
git diff cc94bf5619f9f3bed798ddf151e5e473a789c71b 0502179f8706237c45a64cf6c95882fcfcec689a --name-only
```

Now lets condense the two commands into a single command: 


**Command**
```
git diff --name-only $(git ls-remote <GIT REPO URL/CLONE REPO URL> | awk "/<BRANCH NAME>/ {print \$1}") <SHA2 FROM REMOTE PACKAGE NAME>
```

**Example**
```
git diff --name-only $(git ls-remote https://github.com/dhelia/marchdemo.git | awk "/main/ {print \$1}") 0502179f8706237c45a64cf6c95882fcfcec689a
```
