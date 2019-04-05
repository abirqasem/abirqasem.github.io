### Go syntactic quirks

```
func (file *File) Write(b []byte) (n int, err error)
```

**name before type**

int main  is main int


### Go stuff the needs to be tested out

1. go fmt // what is package level
2. godoc //why is it a web server
    * Every package should have `/* */` before the package statement
3. Names have semantic effect, uppercase names are visible outside packages.
4. `src/encoding/base64` is imported as `""encoding/base64""` but used as `base64`. 
5. Write a if -else -if using empty switch
1. Composite literal
2. comma, ok medium
3. `%+v` and `%#v` 
4. toString of go is  --String (it is in my go kv idiom)
5. `v ...interface{}` then v acts like a variable of type `[] interface {}` 
 // array off interface of type 
6. 
`x := []int{1,2,3}
y := []int{4,5,6}
x = append(x, y...)
`
7. `iota`
