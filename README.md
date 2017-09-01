# Introduction

GOsc <Simplify your waste-bytes helper functions> is an helper package for Go, written to be user friendly with aliases and simple examples.  

If you need a new helper, please open an issue and if you have already the code, thank you!

# Installation

Install the package from your terminal with `go get github.com/danilopolani/gosc` and then import it in your project: `import "gosc"`.

# Available helpers
## Strings
- [ToBytes](#tobytes) - Convert a string into a bytes slice.
- [ByteToString](#bytetostring) - Convert a bytes slice into a string.
- [Rstring](#rstring) - Reverse a string (every character).
- [LcFirst](#lcfirst) - Convert the first character to the string to **L**ower**C**ase.
- [UcFirst](#ucfirst) - Convert the first character to the string to **U**pper**C**ase.
- [ToSnake](#tosnake) - Convert a string to *snake_case*.
- [ToCamel](#tocamel) - Convert a string to *camelCase*.
- [ToPascal](#topascal) - Convert a string to *PascalCase*.
- [ToInt](#toint) - Convert a string to an int.
- [ToUint](#touint) - Convert a string to a uint.
- [ToBase64](#tobase64) - Encode a string in base64.
- [FromBase64](#frombase64) - Decode a string from base64.
- [IsBool](#isbool) - Check if a string is a boolean.
- [IsEmail](#isemail) - Check if a string is an email address.
- [IsURL](#isulrl) - Check if a string is a valid URL.
- [IsJSON](#isjson) - Check if a string is a valid JSON document.
- [IsIP](#isip) - Check if a string is an IPv4.
- [IsHexColor](#ishexcolor) - Check if a string is a hex color.
- [IsRGBColor](#isrgbcolor) - Check if a string is a RGB color.
- [IsCreditCard](#iscreditcard) - Check if a string is a valid credit card.
- [IsOnlyDigits](#isonlydigits) - Check if a string contains only numbers.
- [IsOnlyLetters](#isonlyletters) - Check if a string contains only letters.
- [IsOnlyAlphaNumeric](#isonlyalphanumeric) - Check if a string contains only letters and numbers.
- [Uniq](#uniq) - Generate a unique token based on current time and hashed in sha256. 
- [StrRand](#strrand) - Generate a random string of the given size.
- [UUID](#uuid) - Generate a UUID v4 according to RFC 4122.

## Numbers
- [IsInt](#isint) - Check if a string is an integer.
- [IsFloat](#isfloat) - Check if a string is a float number and numbers.
- [Utoa](#utoa) - Transform a uint into a string. 
- [Rand](#rand) - Pick a random int from the given range.

## Slices
- [Delete](#delete) - Delete an item from a slice.
- [Rsort](#rsort) - Reverse the order (*desc*) of an ordered slice.
- [EqSlices](#eqslices) - Check if two slices are equal. 
- [SliceRand](#slicerand) - Retrieve a random item from the given slice. 
- [InSlice](#inslice) - Check if a value is in the given slice.

# Helpers
The detailed list of helpers with examples.  

### ToBytes
Convert a string into a bytes slice.  
**Return**: `[]byte`  

```
fmt.Println(gosc.ToBytes("Foo")) // [70 111 111]
```

### ByteToString
Convert a bytes slice into a string.  
**Return**: `string`  

```
fmt.Println(gosc.ByteToString([]byte{70, 111, 111})) // Foo
```

### Rstring
Reverse a string (every character).  
**Aliases**: `ReverseString`  
**Return**: `string`  

```
fmt.Println(gosc.Rstring("foo")) // oof
fmt.Println(gosc.ReverseString("소주")) // 주소
```

### LcFirst
Convert the first character to the string to **L**ower**C**ase.  
**Aliases**: `LowerFirst`  
**Return**: `string`  

```
fmt.Println(gosc.LcFirst("Foo")) // foo
fmt.Println(gosc.LowerFirst("소주")) // 소주
```

### UcFirst
Convert the first character to the string to **U**pper**C**ase.  
**Aliases**: `UpperFirst`  
**Return**: `string`  

```
fmt.Println(gosc.UcFirst("foo")) // Foo
fmt.Println(gosc.UpperFirst("소주")) // 소주
```

### ToSnake
Convert a string to *snake_case*.  
**Aliases**: `ToSnakeCase`  
**Return**: `string`  

```
fmt.Println(gosc.ToSnake("Foo 123")) // foo_123
fmt.Println(gosc.ToSnakeCase("camelCase")) // camel_case
```

### ToCamel
Convert a string to *camelCase*.  
**Aliases**: `ToCamelCase`  
**Return**: `string`  
**Known bugs**:  
[] Doesn't lowercase the string

```
fmt.Println(gosc.ToCamel("foo bar")) // fooBar
fmt.Println(gosc.ToCamelCase("kebab-case")) // kebabCase
```

### ToPascal
Convert a string to *PascalCase*.  
**Aliases**: `ToPascalCase`  
**Return**: `string`  
**Known bugs**:  
[] Doesn't lowercase the string

```
fmt.Println(gosc.ToPascal("foo bar")) // FooBar
fmt.Println(gosc.ToPascalCase("kebab-case")) // KebabCase
```

### ToKebab
Convert a string to *kebab-case*.  
**Aliases**: `ToKebabCase`  
**Return**: `string`  

```
fmt.Println(gosc.ToKebab("Foo bAr")) // foo-bar
fmt.Println(gosc.ToKebabCase("snake_case")) // snake-case
```

### ToInt
Convert a string to an int.  
**Return**: `int`  

```
fmt.Println(gosc.ToInt("-53")) // -53
fmt.Println(gosc.ToInt("542.8")) // 542
fmt.Println(gosc.ToInt("foo")) // 0
```

### ToUint
Convert a string to a uint.  
**Return**: `uint`  

```
fmt.Println(gosc.ToUint("2")) // 2
fmt.Println(gosc.ToUint("-53")) // 0
fmt.Println(gosc.ToUint("542.8")) // 542
fmt.Println(gosc.ToUint("foo")) // 0
```

### ToBase64
Encode a string in base64.  
**Return**: `string`  

```
fmt.Println(gosc.ToBase64("abc〩")) // YWJj44Cp
```

### FromBase64
Decode a string from base64.  
**Return**: `string`  

```
fmt.Println(gosc.FromBase64("YWJj44Cp")) // abc〩
fmt.Println(gosc.FromBase64("fake")) // ""
```

### IsBool
Check if a string is a boolean.  
**Return**: `bool`  

```
fmt.Println(gosc.IsBool("false")) // true
fmt.Println(gosc.IsBool("foo")) // false
fmt.Println(gosc.IsBool("5")) // false
fmt.Println(gosc.IsBool("1")) // true
```

### IsEmail
Check if a string is an email address.  
**Return**: `bool`  

```
fmt.Println(gosc.IsEmail("me@example.com")) // true
fmt.Println(gosc.IsEmail("foo")) // false
fmt.Println(gosc.IsEmail("")) // false
```

### IsURL
Check if a string is a valid URL.  
**Return**: `bool`  
**Known bugs**:  
[] Other protocols (such as FTP) return true
[] Just the procotol returns true

```
fmt.Println(gosc.IsURL("https://github.com")) // true
fmt.Println(gosc.IsURL("https://github")) // false
fmt.Println(gosc.IsURL("https://github.com?q=gosc")) // true
```

### IsJSON
Check if a string is a valid JSON document.  
**Return**: `bool`  

```
fmt.Println(gosc.IsJSON("{\"foo\":\"bar\"}")) // true
fmt.Println(gosc.IsJSON("")) // false
fmt.Println(gosc.IsJSON("[1]")) // true
```

### IsIP
Check if a string is an IPv4.  
**Return**: `bool`  

```
fmt.Println(gosc.IsIP("127.0.0.1")) // true
fmt.Println(gosc.IsIP("")) // false
fmt.Println(gosc.IsIP("127.0.0.1.1")) // false
fmt.Println(gosc.IsIP("2001:0db8:85a3:0000:0000:8a2e:0370:7334")) // false
fmt.Println(gosc.IsIP("D8-D3-85-EB-12-E3")) // false
```

### IsHexColor
Check if a string is a hex color.  
**Return**: `bool`  

```
fmt.Println(gosc.IsHexColor("#fff")) // true
fmt.Println(gosc.IsHexColor("fff")) // true
fmt.Println(gosc.IsHexColor("#ffff")) // false
fmt.Println(gosc.IsHexColor("#ggg")) // false
fmt.Println(gosc.IsHexColor("rgb(255, 255, 255)")) // false
```

### IsRGBColor
Check if a string is a RGB color.  
**Aliases**: `IsRGB`  
**Return**: `bool`  

```
fmt.Println(gosc.IsRGBColor("rgb(255, 255, 255)")) // true
fmt.Println(gosc.IsRGBColor("rgb(255, 255, 256)")) // false (out of range)
fmt.Println(gosc.IsRGBColor("rgb(255, 255)")) // false
fmt.Println(gosc.IsRGB("rgba(255, 255, 255, 1)")) // false
fmt.Println(gosc.IsRGB("#fff")) // false
```

### IsCreditCard
Check if a string is a valid credit card.  
**Return**: `bool`  

```
fmt.Println(gosc.IsCreditCard("4653 0343 2480 9848")) // true (Visa)
fmt.Println(gosc.IsCreditCard("4653-0343-2480-9848")) // true
fmt.Println(gosc.IsCreditCard("1111-0343-2480-9848")) // false (not valid vendor)
fmt.Println(gosc.IsCreditCard("5321 7873 3201 8954")) // true (Mastercard)
fmt.Println(gosc.IsCreditCard("3421-941266-26371")) // true (American Express)
fmt.Println(gosc.IsCreditCard("주주주주-주주주주-주주주주-주주주주")) // false
```

### IsOnlyDigits
Check if a string contains only numbers.  
**Aliases**: `IsOnlyNumbers`
**Return**: `bool`  

```
fmt.Println(gosc.IsOnlyDigits("1234")) // true
fmt.Println(gosc.IsOnlyDigits("-1")) // false
fmt.Println(gosc.IsOnlyNumbers("foo")) // false
```

### IsOnlyLetters
Check if a string contains only letters.  
**Aliases**: `IsOnlyAlpha`
**Return**: `bool`  

```
fmt.Println(gosc.IsOnlyLetters("foo")) // true
fmt.Println(gosc.IsOnlyLetters("foo3")) // false
fmt.Println(gosc.IsOnlyAlpha("주")) // false
fmt.Println(gosc.IsOnlyAlpha("")) // false
```

### IsOnlyAlphaNumeric
Check if a string contains only letters and numbers.  
**Aliases**: `IsOnlyLettersNumbers`, `IsOnlyAlphaNum`  
**Return**: `bool`  

```
fmt.Println(gosc.IsOnlyAlphaNumeric("foo")) // true
fmt.Println(gosc.IsOnlyAlphaNumeric("foo3")) // true
fmt.Println(gosc.IsOnlyAlpha("주")) // false
fmt.Println(gosc.IsOnlyAlpha("")) // false
```

### Uniq
Generate a unique token based on current time and hashed in sha256.  
**Aliases**: `Unique`  
**Return**: `string`  

```
fmt.Println(gosc.Uniq()) // My output: 839079123b9223727c31982cedc4e63f880a91a26591532f08185453d20db497
```

### StrRand
Generate a random string of the given size.  
**Aliases**: `RandStr`, `RandomString`  
**Return**: `string`  

```
fmt.Println(gosc.StrRand(12)) // My output: BbikfUNZdXCS
```

### UUID
Generate a UUID v4 according to RFC 4122.  
**Return**: `string`  

```
fmt.Println(gosc.UUID()) // My output: 8e67e7ae-d674-4470-9345-35511fed974a
```

## Numbers

### IsInt
Check if a string is an integer.    
**Return**: `bool`  

```
fmt.Println(gosc.IsInt("5")) // true
fmt.Println(gosc.IsInt("-3")) // true
fmt.Println(gosc.IsInt("76.9")) // false
fmt.Println(gosc.IsInt("foo")) // false
```

### IsFloat
Check if a string is a float number.  
**Return**: `bool`  

```
fmt.Println(gosc.IsFloat("76.9")) // true
fmt.Println(gosc.IsFloat("5")) // true
fmt.Println(gosc.IsFloat("foo")) // false
```

### Utoa
Transform a uint into a string.  
**Return**: `string`  

```
var i uint = 5
fmt.Println(gosc.Utoa(i)) // "5"
```

### Rand
Pick a random int from the given range.  
**Return**: `int`  

```
fmt.Println(Rand(1, 999)) // My output: 508
```

## Slices

### Delete
Delete an item from a slice.  
**Supported types**: `string`, `int`, `float64`

```
slice1 := []string{"foo", "bar", "lazy", "dog"}
slice2 := []int{5, -3, 64}

Delete(&slice1, 2)
Delete(&slice2, 0)

fmt.Println(slice1) // [foo bar dog]
fmt.Println(slice2) // [-3 64]
```

### Rsort
Reverse the order (*desc*) of an ordered slice.  
**Alias**: `ReverseSort`  

```
slice1 := []string{"foo", "bar", "lazy", "dog"}
slice2 := []int{5, -3, 64}

Rsort(&slice1)
ReverseSort(&slice2)

fmt.Println(slice1) // [lazy foo dog bar]
fmt.Println(slice2) // [64 5 -3]
```

### EqSlices
Check if two slices are equal (not in depth, use `reflect.DeepEqual` for that).  
**Return**: `bool`  

```
slice1 := []string{"foo", "bar"}
slice2 := []int{5, -3, 64}

fmt.Println(EqSlices(&slice1, &[]string{"foo","bar"})) // true
fmt.Println(EqSlices(&slice2, &slice1)) // false
fmt.Println(EqSlices(&slice2, &[]int{-3, 5, 64})) // false
fmt.Println(EqSlices(&slice2, &[]int{5, -3, 64})) // true
```

### SliceRand
Retrieve a random item from the given slice. If you don't want to assign it to a variable, please look the other functions at the end.    

```
slice1 := []string{"foo", "bar", "lazy", "dog"}
slice2 := []int{5, -3, 64, 777}

var randomString string
var randomInt int

SliceRand(&slice1, &randomString)
SliceRand(&slice2, &randomInt)

fmt.Println(randomString) // My output: bar
fmt.Println(randomInt) // My output: -3
```

### InSlice
Check if a value is in the given slice.  

```
slice1 := []string{"foo", "bar", "lazy", "dog"}
slice2 := []int{5, -3, 64, 777}

fmt.Println(InSlice("lazy", &slice1)) // frue
fmt.Println(InSlice(55, &slice2)) // false
```