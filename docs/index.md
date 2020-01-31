## MkDocs PoC Demo

### Code Block의 표시

#### Fenced Code Block

~~~
#!/usr/bin
$ echo "Hello World!"
~~~

#### Backtick Code Block

```
#!/usr/bin
$ echo "Hello World!"
```

#### Indented Code Block

    #!/usr/bin
    $ echo "Hello World!"

### Code Block 라인 번호 표시

#### Line Number 특정 코드 블럭에만 사용

``` linenums="1"
#!/usr/bin
$ echo "Hello World!"
```

### List 하위에 Code Block 표시


1.  First item of the list

		#!/usr/bin
		$ echo "Hello World!"

2.  Second item of the list

		<html>
		<head>
		<script src=" "></script>
		</head>
		</html>

### Note 내부에 Code Block 표시

!!! note "code block inside note"
    > ``` linenums="1"
      $ echo "test" > text.txt
      $ exit
      ```

### Code Block의 특정 라인 highlight

``` bash hl_lines="1 3"
#!/usr/bin
$ echo "Hello World!"
$ touch example.txt
```

### Code Block title 표시 불가 (대안)

``` bash tab="Tab Title"
#!/usr/bin
$ echo "Hello World!"
$ touch example.txt
```
