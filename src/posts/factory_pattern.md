---
image: "src/images/factory.jpg"
title: Factory Pattern in Go
slug: factory_pattern_in_go
excerpt: The factory pattern is a design pattern that is commonly used in object-oriented programming to create objects without specifying the exact class of object that will be created. This pattern is particularly useful in situations where a class hierarchy exists, but the client code should be decoupled from the classes that are being instantiated. In this blog post, we will take a look at how to implement the factory pattern in Go, with a code sample to illustrate how it works.
date: 2022-08-01
author: Henk Bourgonje
---

The factory pattern is a design pattern that is commonly used in object-oriented programming to create objects without specifying the exact class of object that will be created. This pattern is particularly useful in situations where a class hierarchy exists, but the client code should be decoupled from the classes that are being instantiated. In this blog post, we will take a look at how to implement the factory pattern in Go, with a code sample to illustrate how it works.

The factory pattern is implemented by creating a factory function that takes in the necessary parameters and returns an instance of the desired class. The factory function is responsible for creating and returning the appropriate instance, based on the parameters passed to it. Here is an example of a factory function that creates instances of different types of vehicles:

```go
type Vehicle interface {
	Drive() string
}

type Car struct{}

func (c *Car) Drive() string {
	return "Vroom!"
}

type Truck struct{}

func (t *Truck) Drive() string {
	return "Rumble!"
}

func NewVehicle(t string) Vehicle {
	switch t {
	case "car":
		return &Car{}
	case "truck":
		return &Truck{}
	default:
		return nil
	}
}

func main() {
	vehicle := NewVehicle("car")
	fmt.Println(vehicle.Drive())
	// Output: "Vroom!"
}
```

In this example, we have defined an interface Vehicle which has a method Drive() . Then we have created two structs Car, Truck which implements the Vehicle interface and have their own implementation of the Drive method. The factory function NewVehicle takes a string as parameter and returns an instance of the struct based on the string value passed.

The factory pattern can be useful when you want to create objects without specifying the exact class of object that will be created, or when you want to decouple the client code from the classes that are being instantiated. By using a factory function, the client code can simply call the factory function and let it handle the details of creating the appropriate instance, without needing to know the details of the classes that are being instantiated.

In this example, the factory function NewVehicle is responsible for creating and returning the appropriate vehicle instance, based on the type passed as a parameter. The client code can simply call the factory function and let it handle the details of creating the appropriate instance, without needing to know the details of the Car and Truck structs.

In conclusion, The factory pattern is a powerful technique that can be used to create objects in a flexible and decoupled way. It allows you to create objects without specifying the exact class of object that will be created, and it can be used to decouple the client code from the classes that are being instantiated. Implementing the factory pattern in Go is relatively simple, and it can make your code more flexible and easier to maintain in the long run.
