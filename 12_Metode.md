[[Strukture]](11_Strukture.md) [[Sadržaj]](toc.md) [[Nizovi]](13_Nizovi.md)

# Metode

Hajde da pričamo o metodama, ponekad poznatim i kao metode prijemnika.

Tehnički gledano, Go nije objektno orijentisan programski jezik. Nema klase, objekte i nasleđivanje.

Međutim, Go ima tipove. I možete definisati metode na tipovima.

Metod nije ništa drugo do funkcija sa posebnim argumentom prijemnika. Da vidimo kako možemo deklarisati metode.
```
func (variable T) Name(params) (returnTypes) {}
```
Argument prijemnika ima ime i tip. Pojavljuje se između ključne reči `func` i imena metode.

Na primer, definišimo Car strukturu.
```
type Car struct {
	Name string
	Year int
}
```
Sada, hajde da definišemo metodu poput `IsLatest` koja će nam reći da li je automobil proizveden u poslednjih 5 godina.
```
func (c Car) IsLatest() bool {
	return c.Year >= 2017
}
```
Kao što vidite, možemo pristupiti instanci Car koristeći promenljivu prijemnika c. Volim da je smatram `this` ključnom reči iz objektno orijentisanog sveta.

Sada bi trebalo da budemo u mogućnosti da pozovemo ovu metodu nakon što inicijalizujemo našu strukturu, baš kao što to radimo sa klasama u drugim jezicima.
```
func main() {
	c := Car{"Tesla", 2021}
	fmt.Println("IsLatest", c.IsLatest())
}
```
### Metode sa pointer prijemnicima

Svi primeri koje smo ranije videli imali su vrednosni prijemnik.

Kod vrednosnih prijemnika, metoda radi na kopiji vrednosti koja joj je prosleđena. Stoga, sve izmene izvršene na prijemniku unutar metoda nisu vidljive pozivaocu.

Na primer, napravimo još jednu metodu pod nazivom *UpdateName* koja će ažurirati tip *Car*.
```
func (c Car) UpdateName(name string) {
	c.Name = name
}
```
Sada, hajde da ovo pokrenemo.
```
func main() {
	c := Car{"Tesla", 2021}
	c.UpdateName("Toyota")
	fmt.Println("Car:", c)
}
```
	$ go run main.go
	Car: {Tesla 2021}

Izgleda da ime nije ažurirano, pa sada prebacimo naš prijemnik na tip pointera i pokušajmo ponovo.
```
func (c *Car) UpdateName(name string) {
	c.Name = name
}
```
	$ go run main.go
	Car: {Toyota 2021}

Kao što se i očekivalo, metode sa pointer prijemnicima mogu da menjaju vrednost na koju prijemnik pokazuje. Takve modifikacije su vidljive i pozivaocu metode.

### Svojstva metoda

Hajde da vidimo i neka svojstva metoda!

Go je dovoljno pametan da pravilno interpretira naš poziv funkcije i stoga su pozivi metoda pointer prijemnika samo sintaksički šećer koji Go pruža radi praktičnosti.
```
(&c).UpdateName(...)
```
Možemo izostaviti i naziv promenljive ako je ne koristimo.
```
func (Car) UpdateName(...) {}
```
Metode nisu ograničene samo na strukture, već se mogu koristiti i sa tipovima koji nisu strukture.
```
package main
import "fmt"

type MyInt int

func (i MyInt) isGreater(value int) bool {
	return i > MyInt(value)
}

func main() {
	i := MyInt(10)
	fmt.Println(i.isGreater(5))
}
```
### Zašto metode umesto funkcija?

Dakle, pitanje je, zašto koristiti metode umesto funkcija?

Kao i uvek, nema posebnog odgovora na ovo, i ni na koji način jedno nije bolje od drugog. Umesto toga, trebalo bi ih koristiti na odgovarajući način kada se situacija pojavi.

Jedna stvar koja mi trenutno pada na pamet je da nam metode mogu pomoći da izbegnemo sukobe u imenovanju.

Pošto je metoda vezana za određeni tip, možemo imati ista imena metoda za više prijemnika.

Ali na kraju, to bi moglo da se svede na preferencije, kao što je "pozivi metoda su mnogo lakši za čitanje i razumevanje od poziva funkcija" ili obrnuto.

[[Strukture]](11_Strukture.md) [[Sadržaj]](toc.md) [[Nizovi]](13_Nizovi.md)