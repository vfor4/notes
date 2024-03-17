![[gophercises_punching.gif]]

```go

a := "hi"
cont a = 5
// Aggregate
array := [3]string{"a", "b", "c"} // if not init return default value
var slice []int // [] (nill)
var m map[string]int // map[] (nill)

//Structs is heterogeneous data type 
var s struct {
	name string
	id int
}

// custom type
type myStruct struct {
	name string
	value int
}
a myStruct; // {"", 0}
a = myStruct{name: "lego", value: 1}
s2 := s
s.name = "Blinkgo" 
Println(s, s2) // {"Blinkgo", 1} {"lego", 1}
// allow to compare

```
Allow to compare two arrays
Arrays are fixed size
Slice are called reference data type (under the hood uses arrays)
Map are called referece data type too