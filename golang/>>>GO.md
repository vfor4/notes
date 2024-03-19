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

### LOOP 
```go
// Infinite
for { }
// Condition
for i < 5 { }
// Counter-based
for i:=1; i< 3; i++ { }
// Over Collections
for key,value := range collection { }
for key := range collection { }
for _, value := range collection { }
```
### BRANCHING 😋
```go
// if
if condition { }
💡 if initializer; test { }
// switch
switch i := 5; i {
	case 5:
		PrintLn
	case 3, 4:
		statements2
	default:
		statement

}
💡 similar to if
// logical swithc
switch i := 5, true { // can remove true, short hand syntax
	case i > 3:
		Println
}
// deferred
db, _ := sql.Open("drive", "connect")
defer db.Close()

rows, _ := db.Query("select ...")
defer rows.Close()

// panic and recovery, panic like exception
func divide(dividend, divisor int) int {
	defer func () {
		if msg := recover(); msg != nil {
			fmt.Println(msg)
		}
	}()
}

// goto 
can leave a block
```

![[Pasted image 20240319203237.png]]
### FUNCTION
```go
// functions
return single value
func greet (name1 string, name2 string) = func greet (name1, name2 string)
pass by value

return multiple values
func multi (l int) (int, bool) {
	return 4,true
}
// packages
lowercase means private, uppercase means public
// comments


```



![[Pasted image 20240319213259.png]]










