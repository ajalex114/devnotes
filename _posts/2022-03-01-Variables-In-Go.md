---
title:  "Variables in Go" 
categories: [dev]
description: "Variables in Go / Golang"
tags: [go]
--- 

Go or Golang is a strongly typed language. So, basically the compiler needs to know what kind of data type it is dealing with.

There are 3 ways of declaring a variable.

1. 

``` go
	var i int
```

Here `i` is the variable name and the data type is `int`.  
The default value of the variable would be `0`.

----

2. 

``` go
    var s = "Hello World"
```

Here, `s` is the variable name and it is of the data type `string`.  
Although it is not mentioned that the data type is string, the compiler implies from the value assigned to the variable that it is of type string.

---

3. 

``` go
    s := "Hello World"
```

Here again, `s` is the variable name and it is of type `string`.  
In this method you don't have to use the keyword `var`. But if you look closely, the assignment operator is a bit different.  
This method uses the operator `:=` instead of `=`.  

---

4. 

``` go
    var a, b, c int
```

You can declare multiple variables together like above, if they are of the same data type.  

You could use a similar mechanism when declaring functions as well.  
For example:
``` go
func Foo(a, b, c string) {
	fmt.Println(a, b, c)
}
```

---

5. 

``` go
	var (
		i = 0
		j = "hello world"
		k = false
	)
```

You can use this method to initialize multiple variables of different datatype, but together.

----

_References: [Effective Go](https://go.dev/doc/effective_go#variables), [Go By Example](https://gobyexample.com/variables)_