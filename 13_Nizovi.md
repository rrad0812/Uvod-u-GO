[Sadržaj](toc.md)

# Nizovi

Niz je kolekcija elemenata istog tipa fiksne veličine. Elementi niza se čuvaju sekvencijalno i može im se pristupiti pomoću njihovih index.

### Deklaracija niza

Niz možemo deklarisati na sledeći način:
```
var a [n]T
```
Ovde je `n` dužina i `T` može biti bilo kog tipa kao što je ceo broj, string ili korisnički definisane strukture.

Sada, hajde da deklarišemo niz celih brojeva dužine 4 i odštampamo ga.
```
func main() {
	var arr [4]int
	fmt.Println(arr)
}
```
	$ go run main.go
	[0 0 0 0]

Podrazumevano, svi elementi niza su inicijalizovani nultom vrednošću odgovarajućeg tipa niza.

### Inicijalizacija

Takođe možemo inicijalizovati niz koristeći `array literal`.
```
var a [n]T = [n]T{V1, V2, ... Vn}

func main() {
	var arr = [4]int{1, 2, 3, 4}

	fmt.Println(arr)
}
```
	$ go run main.go
	[1 2 3 4]

Možemo čak i da napravimo skraćenu deklaraciju.
```
...
arr := [4]int{1, 2, 3, 4}
```
### Pristup članovima niza

I slično kao i u drugim jezicima, elementima možemo pristupiti koristeći `index` jer su sačuvani sekvencijalno.
```
func main() {
	arr := [4]int{1, 2, 3, 4}

	fmt.Println(arr[0])
}
```
	$ go run main.go
	1

### Iteriranje niza

Dakle, postoji više načina za iteraciju kroz nizove.

Prvi je korišćenje petlje `for` sa `len` funkcijom koja nam daje dužinu niza.
```
func main() {
	arr := [4]int{1, 2, 3, 4}

	for i := 0; i < len(arr); i++ {
		fmt.Printf("Index: %d, Element: %d\n", i, arr[i])
	}
}
```
	$ go run main.go
	Index: 0, Element: 1
	Index: 1, Element: 2
	Index: 2, Element: 3
	Index: 3, Element: 4

Drugi način je korišćenje `range` ključne reči sa `for` petljom.
```
func main() {
	arr := [4]int{1, 2, 3, 4}

	for i, e := range arr {
		fmt.Printf("Index: %d, Element: %d\n", i, e)
	}
}
```
	$ go run main.go
	Index: 0, Element: 1
	Index: 1, Element: 2
	Index: 2, Element: 3
	Index: 3, Element: 4

Kao što vidimo, naš primer funkcioniše isto kao i prethodni.

Ali ključna reč `range` je prilično svestrana i može se koristiti na više načina.
```
for i, e := range arr {} 	// Normal usage of range
for _, e := range arr {} 	// Omit index with _ and use element
for i := range arr {} 		// Use index only
for range arr {} 			// Simply loop over the array
```
### Višedimenzionalni nizovi

Svi nizovi koje smo do sada kreirali su jednodimenzionalni. Takođe možemo kreirati višedimenzionalne nizove u programskom jeziku Go.

Hajde da pogledamo jedan primer:
```
func main() {
	arr := [2][4]int{
		{1, 2, 3, 4},
		{5, 6, 7, 8},
	}
	for i, e := range arr {
		fmt.Printf("Index: %d, Element: %d\n", i, e)
	}
}
```
	$ go run main.go
	Index: 0, Element: [1 2 3 4]
	Index: 1, Element: [5 6 7 8]

Takođe možemo dozvoliti kompajleru da zaključi dužinu niza koristeći ... elipsis umesto dužine.
```
func main() {
	arr := [...][4]int{
		{1, 2, 3, 4},
		{5, 6, 7, 8},
	}
	for i, e := range arr {
		fmt.Printf("Index: %d, Element: %d\n", i, e)
	}
}
```
	$ go run main.go
	Index: 0, Element: [1 2 3 4]
	Index: 1, Element: [5 6 7 8]

### Svojstva nizova

Sada hajde da pričamo o nekim svojstvima nizova.

Dužina niza je deo njegovog tipa. Dakle, niz a i b su potpuno različiti tipovi i ne možemo dodeliti jedan drugom.

To takođe znači da ne možemo promeniti veličinu niza, jer bi promena veličine niza značila promenu njegovog tipa.
```
package main

func main() {
	var a = [4]int{1, 2, 3, 4}
	var b [2]int = a // Error, cannot use a (type [4]int) as type [2]int in assignment
}
```
Nizovi u programskom jeziku Go su vrednosni tipovi, za razliku od drugih jezika poput C, C++ i Java gde su nizovi referentni tipovi.

To znači da kada dodelimo niz novoj promenljivoj ili prosledimo niz funkciji, ceo niz se kopira.

Dakle, ako napravimo bilo kakve izmene u ovom kopiranom nizu, originalni niz neće biti pogođen i ostaće nepromenjen.
```
package main
import "fmt"

func main() {
	var a = [7]string{"Mon", "Tue", "Wed", "Thu", "Fri", "Sat", "Sun"}
	var b = a // Copy of a is assigned to b
	b[0] = "Monday"
	fmt.Println(a) // Output: [Mon Tue Wed Thu Fri Sat Sun]
	fmt.Println(b) // Output: [Monday Tue Wed Thu Fri Sat Sun]
}
```

[Sadržaj](toc.md)