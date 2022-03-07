---
title:  "Inheritance in Go" 
categories: [dev]
description: "Inheritance in Go / Golang"
tags: [go]
--- 

Since Golang does not support classes, the concept of inheritance is achieved using `interfaces` and `structs`.  
Then again, structs cannot directly extend from interfaces or other structs.  
So, one could argue that _Golang does not have inheritance_

Inheritance can be achieved in Golang in 3 ways.  

1. Implied inheritance using interfaces with Polymorphism
2. Inheritance by Composition
3. Inheritance Embedding

## Implied inheritance using interfaces with Polymorphism

For people coming from the object oriented world (_like me_), it can be considered as an alternative of inheritance.  
This concept is actually `Polymorphism` in Golang.

The idea is that, if you have an `interface` and a `struct` that has the same structure, then you can consider it akin to a child instance of the interface.  

The concept sounds similar to a weakly typed language.  
If the `struct` looks like an `interface`, then it can be used in place of the interface.  
In short, if a struct has all the methods of the interface defined, then its reference can be used in place of the interface.

``` go
package main

import "fmt"

type sleeper interface {
	Sleep()
}

type Cat struct{}

func (c *Cat) Sleep() {
	fmt.Println("purrrrrr")
}

type Dog struct{}

func (d *Dog) Sleep() {
	fmt.Println("brrrrr")
}

func main() {
	pets := []sleeper{new(Cat), new(Dog)}

	for _, x := range pets {
		x.Sleep()
	}

	var pussyCat1 sleeper
	pussyCat1 = new(Cat)
	pussyCat1.Sleep()

	var tiger sleeper
	tiger = &Dog{}
	tiger.Sleep()

	// This will not work
	// var doggy sleeper
	// doggy = Dog{}
	// doggy.Sleep()
}

```

[Click to try out the above code](https://go.dev/play/p/YiE2iqmjszT)

## Inheritance by Composition

If you search for inheritance using Golang online, you will come across this method of inheritance by composition.   
I frankly do not consider this as inheritance at all.  
This is just composition.  

You include a type (struct or interface) as a field in struct.  
Then why include this here? _Just because I see this as a popular method mentioned online_

_How does it work?_

``` go
package main

import "fmt"

type human struct {
	Name string
}

type person struct {
	human human
	age   int
}

func (p *person) GetSpecies() string {
	return "human"
}

func (h *human) GetLivingBeing() string {
	return "human being"
}

func main() {
	alen := person{
		human: human{
			Name: "Alen",
		},
		age: 10,
	}

	fmt.Println(alen.human.Name)
	fmt.Println(alen.age)
	fmt.Println(alen.GetSpecies())
	fmt.Println(alen.human.GetLivingBeing())
}

```

[Click to try out the above code](https://go.dev/play/p/__s_AH5YIHA)

## Inheritance by Embedding

This is the closest I feel Go works, when it comes to inheritance.  
You can consider this like a syntactical sugar to implement inheritance in Go (_although it isn't really the case_)  

In this method you embed an `interface` or `struct` into another `interface` or `struct`.  

_See below:_  

``` go
package main

import "fmt"

type livingBeings interface {
	GetLivingBeing() string
}

type species interface {
	livingBeings
	GetSpecies() string
}

type human struct {
	species
	Name string
}

type person struct {
	human
	age int
}

func (p *person) GetSpecies() string {
	return "human"
}

func (h *human) GetLivingBeing() string {
	return "human being"
}

func main() {
	alen := person{
		human: human{
			Name: "Alen",
		},
		age: 10,
	}

	fmt.Println(alen.Name)
	fmt.Println(alen.age)
	fmt.Println(alen.GetSpecies())
	fmt.Println(alen.GetLivingBeing())
}

```

[Click to try out the above code](https://go.dev/play/p/hmdf20GiKdu)

## References
- [Inheritance in GoLang - GeeksForGeeks](https://www.geeksforgeeks.org/inheritance-in-golang/)
- [Embedding Interfaces in Golang - GeeksForGeeks](https://www.geeksforgeeks.org/embedding-interfaces-in-golang/)
- [Why Go’s structs are superior to class-based inheritance - Medium](https://medium.com/@simplyianm/why-gos-structs-are-superior-to-class-based-inheritance-b661ba897c67)
- [Golang Polymorphism Using Interfaces - GeekForGeeks](https://www.geeksforgeeks.org/golang-polymorphism-using-interfaces/)
- [Interfaces - Effective Go](https://go.dev/doc/effective_go#interfaces)
- [Embedding - Effective Go](https://go.dev/doc/effective_go#embedding)