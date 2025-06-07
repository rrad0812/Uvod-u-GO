
# Uvod u Go!

Zdravo, dobrodošli na kurs i hvala što želite da učite Go. Nadam se da će vam ovaj kurs pružiti sjajno iskustvo učenja.

### Šta je Go?
Go (takođe poznat kao Golang) je programski jezik razvijen u kompaniji Gugl 2007. godine, a otvorenog koda objavljen 2009. godine.

Go se fokusira se na jednostavnost, pouzdanost i efikasnost. Dizajniran je da kombinuje efikasnost, brzinu i bezbednost statički tipiziranog i kompajliranog jezika sa lakoćom programiranja dinamičkog jezika kako bi programiranje ponovo bilo zabavno.

Na neki način, želi da kombinuje najbolje delove Pajtona i C++-a kako bi mogao da izgradi pouzdane sisteme koji mogu da iskoriste prednosti višejezgarnih procesora.

### Zašto učiti Go?

Pre nego što počnemo sa ovim kursom, hajde da razgovaramo o tome zašto bi trebalo da naučimo Go.

##### Lako se uči
Go je prilično lak za učenje i ima podržavajuću i aktivnu zajednicu.

A pošto je višenamenski jezik, možete ga koristiti za stvari poput 
- razvoja bekenda, 
- računarstva u oblaku i, u skorije vreme, 
- nauke o podacima.

##### Brz i pouzdan
Što ga čini veoma pogodnim za distribuirane sisteme. Projekti kao što su **Kubernetes** i **Docker** su napisani u Go-u.

##### Jednostavan, ali moćan
Sam jezik je koncizan. Go ima samo **25** ključnih reči što ga čini lakim za čitanje, pisanje i održavanje. 

Ali nemojte da vas jednostavnost zavara, Go ima nekoliko moćnih funkcija koje ćemo kasnije naučiti na kursu.

##### Mogućnosti za karijeru
Go brzo raste i usvajaju ga kompanije svih veličina. A sa tim dolaze i nove dobro plaćene mogućnosti za posao.

Nadam se da Vas je ovo zainteresovalo za Go. Hajde da počnemo sa ovim kursom.

### Instalacija i podešavanje
U ovom tutorijalu, instaliraćemo Go i podesiti naš uređivač koda.

##### Preuzimanje
Možemo instalirati Go iz odeljka za preuzimanja.

##### Instalacija
Ova uputstva su sa zvanične web stranice.

1. **MacOS**
Otvorite datoteku paketa koju ste preuzeli i pratite uputstva da biste instalirali Go. Paket instalira Go distribuciju na `/usr/local/go`. Paket bi trebalo da smesti `/usr/local/go/bin` direktorijum u vašu PATH promenljivu okruženja. Možda ćete morati da ponovo pokrenete sve otvorene terminalne sesije da bi promena stupila na snagu.

2. **Linux** 
Uklonite sve prethodne instalacije Goa brisanjem `/usr/local/go` direktorijuma (ako postoji), a zatim raspakujte arhivu koju ste upravo preuzeli u `/usr/local`, kreirajući novo Go stablo `/usr/local/go`:

        $ rm -rf /usr/local/go && tar -C /usr/local -xzf go1.18.1.linux-amd64.tar.gz

    **Napomena**: Možda ćete morati da pokrenete komandu kao *root* ili preko *sudo*-a.

    Ne raspakujte arhivu u postojeće `/usr/local/go` stablo. Poznato je da ovo dovodi do neispravnih Go instalacija.

    Dodajte `/usr/local/go/bin` u promenljivu okruženja PATH. To možete učiniti dodavanjem sledeće linije u vašu `$HOME/.profile` or `/etc/profile` (za
    instalaciju na nivou celog sistema):

        export PATH=$PATH:/usr/local/go/bin

    **Napomena**: Promene napravljene u datoteci profila možda neće biti primenjene do sledećeg puta kada se prijavite na računar. Da biste odmah primenili promene, jednostavno pokrenite komande školjke direktno ili ih izvršite iz profila pomoću komande kao što je

        $ source $HOME/.profile.

3. **Windows**
Otvorite MSI datoteku koju ste preuzeli i pratite uputstva za instaliranje Go-a.

    Podrazumevano, instalater će instalirati program "Idi u Program Files" ili "Program Files" (x86). Lokaciju možete promeniti po potrebi. 
    
    Nakon instalacije, moraćete da zatvorite i ponovo otvorite sve otvorene komandne linije kako bi se promene u okruženju koje je napravio instalater odrazile u komandnoj liniji.

Proverite da li ste instalirali Go tako što ćete otvoriti komandnu liniju i otkucati sledeću komandu:

    $ go version

Potvrdite da komanda ispisuje instaliranu verziju programa Go.

##### Uređivač koda
U ovom kursu ću koristiti **VS Code**, a možete ga preuzeti odavde.

Slobodno koristite bilo koji drugi uređivač koda koji vam odgovara.

##### Go VS Code extension
Obavezno instalirajte i Go ekstenziju koja olakšava rad sa Go-om u VS Code-u.

To je to što se tiče instalacije i podešavanja Go-a, hajde da započnemo kurs i napišemo naš prvi "Hello, World!" program.

### Hello world
Možemo početi inicijalizacijom modula. Za to možemo koristiti `go mod` komandu.

    $ go mod init example

Ali čekajte... šta je modul? Ne brinite, o tome ćemo uskoro razgovarati! Ali za sada, pretpostavimo da je modul u osnovi kolekcija Go paketa.

Krećemo se dalje, hajde sada da kreiramo main.go datoteku i napišemo program koji jednostavno ispisuje "Hello world".

```
package main
import "fmt"

func main() {
    fmt.Println("Hello World!")
}
```

Ako se pitate, paket `fmt` je deo je standardne Go biblioteke, koja je skup osnovnih paketa koje pruža jezik.

### Struktura Go programa
Sada, hajde da brzo analiziramo šta smo ovde uradili, odnosno strukturu Go
programa.

Prvo, definisali smo paket `main`.
```
package main
```
Zatim, imamo uvoz.
```
import "fmt"
```
Na kraju, ali ne i najmanje važno, je naša `main` funkcija koja deluje kao ulazna tačka za našu aplikaciju, baš kao i u drugim jezicima poput C, Java ili C#.
```
func main() {
	...
}
```
Zapamtite, cilj je ovde da vodite mentalnu belešku, a kasnije tokom kursa ćemo detaljno učiti o funkcijama, i drugim stvarima!

Konačno, da bismo pokrenuli naš kod, možemo jednostavno koristiti `go run` komandu.

    $ go run main.go
    Hello World!

# Promenljive
Počnimo sa deklarisanjem promenljive.

1. **Deklaracija bez inicijalizacije**:
    ```
    var foo string
    ```
2. **Deklaracija sa inicijalizacijom**:
    ```
    var foo string = "Go is awesome"
    ```
3. **Višestruke deklaracije**:
    ```
    var foo, bar string = "Hello", "World"
    // ili
    var (
        foo string = "Hello"
        bar string  = "World"
    )
    ```
4. **Deklaracija sa zaključenim tipom**
Tip je izostavljen, ali će biti zaključen:
    ```
    var foo = "What's my type?"
    ```
5. **Skraćena deklaracija**
Skraćena deklaracija, ovde izostavljamo var ključnu reč, a tip je uvek implicitan. Ovako ćemo videti promenljive koje se deklarišu većinu vremena. Takođe koristimo walrus operator dodele `:=` za deklaraciju plus dodelu.
    ```
    foo := "Shorthand!"
    ```
    **Napomena**: Skraćena deklaracija rade sami unutar tela funkcije.

### Konstante
Takođe možemo deklarisati konstante pomoću `const` ključne reči. Koje, kao što ime sugeriše, konstante predstavljaju fiksne vrednosti koje se ne mogu ponovo dodeliti.
```
const constant = "This is a constant"
```
Takođe je važno napomenuti da se samo konstante mogu dodeliti drugim konstantama.
```
const a = 10
const b = a // ✅ Works

var a = 10
const b = a // ❌ a (variable of type int) is not constant (InvalidConstInit)
```
# Tipovi podataka
Sada hajde da pogledamo neke osnovne tipove podataka dostupne u Gou.

### String
U jeziku Go, string je niz bajtova. Deklarišu se ili pomoću dvostrukih navodnika ili povratnih navodnika koji omogućuju da se string proteže preko više redova.
```
var name string = "My name is Go"

var bio string = `I am statically typed.
    I was designed at Google.`
```
### Bool
Sledeći tip je bool koji se koristi za čuvanje bulovih vrednosti. Može imati dve moguće vrednosti - `true` ili `false`.
```
var value bool = false
var isItTrue bool = true
```
##### bool operatori
Možemo koristiti sledeće operatore na bulovim tipovima

| Tip 	  |  Sintaksa
----------|--------------
Logično   |   && \|\| ! 
Jednakost |	  == !=

### Numerički tipovi
Sada, hajde da pričamo o numeričkim tipovima.

##### Označeni i neoznačeni celi brojevi
Go ima nekoliko ugrađenih tipova celih brojeva različitih veličina za čuvanje označenih i neoznačenih celih brojeva.

Veličina generičkih tipova int i uint zavisi od platforme. To znači da je širina 32 bita na 32-bitnom sistemu i 64 bita na 64-bitnom sistemu.

**Syntax označenih celih brojeva** 
```
var i int     = 404                 // Platform dependent
var i8 int8   = 127                 // -128 to 127
var i16 int16 = 32767               // -2^15 to 2^15 - 1
var i32 int32 = -2147483647         // -2^31 to 2^31 - 1
var i64 int64 = 9223372036854775807 // -2^63 to 2^63 - 1
```
Slično označenim celim brojevima, imamo i neoznačene cele brojeve.

**Syntax neoznačenih celih brojeva** 
```
var ui uint     = 404                 // Platform dependent
var ui8 uint8   = 255                 // 0 to 255
var ui16 uint16 = 65535               // 0 to 2^16
var ui32 uint32 = 2147483647          // 0 to 2^32
var ui64 uint64 = 9223372036854775807 // 0 to 2^64
var uiptr uintptr                     // Integer representation of a memory address
```

Ako ste primetili, postoji i `uintptrtyp` neoznačenog celobrojnog pointera, koji je celobrojna reprezentacija memorijske adrese. Ne preporučuje se njegova upotreba, tako da ne moramo da brinemo o tome.

##### Pa koji bi tip celog broja trebalo da koristimo?

Preporučuje se da kad god nam je potrebna celobrojna vrednost, koristimo samo `int` osim ako nemamo konkretan razlog za korišćenje nekog od tipova celog broja ili neoznačenog celog broja.

### Bajt i runa
Golang ima dva dodatna celobrojna tipa koja se zovu `byte` i `rune` koji su alijasi za tipove podataka `uint8` i `int32`, respektivno.
```
type byte = uint8	// alias
type rune = int32   // alias
```
`rune` predstavlja *Unicode kodnu tačku*.
```
var b byte = 'a'
var r rune = '🍕'
```
### Pokretni zarez
Zatim, imamo tipove sa pokretnim zarezom koji se koriste za čuvanje brojeva sa decimalnom komponentom.

Go ima dva tipa pokretnog zareza `float32` i `float64`. Oba tipa prate standard IEEE-754.

Podrazumevani tip za vrednosti sa pokretnim zarezom je `float64`.
```
var f32 float32 = 1.7812 // IEEE-754 32-bit
var f64 float64 = 3.1415 // IEEE-754 64-bit
```
##### Numerički operatori
Go pruža nekoliko operatora za izvršavanje operacija nad numeričkim tipovima.

| Tip 					| Sintaksa
------------------------|----------------------------------
Aritmetika 				| + - * / %
Poređenje 				| == != < > <= >=
Bitski 					| & \| ^ << >>
Povećanje/smanjenje 	| ++ --
Dodela	 				| = += -= *= /= %= <<= >>= &= |= ^=

### Kompleksni brojevi
U Gou postoje dva kompleksna tipa, `complex128`, gde su i realni i imaginarni delovi `float64` i `complex64`, gde su realni i imaginarni delovi `float32`.

Kompleksne brojeve možemo definisati ili koristeći ugrađenu funkciju `complex` ili kao literale.
```
var c1 complex128 = complex(10, 1)
var c2 complex64 = 12 + 4i
```
### Nulte vrednosti
Sada hajde da razgovaramo o nultim vrednostima. Dakle, u programskom jeziku Go, svakoj promenljivoj deklarisanoj bez eksplicitne početne vrednosti dodeljuje se njena nulta vrednost. 
Na primer, deklarišimo neke promenljive:
```
var i int
var f float64
var b bool
var s string

fmt.Printf("%v %v %v %q\n", i, f, b, s)
```

    $ go run main.go
    0 0 false ""

Dakle, kao što vidimo, vrednosti `int` i `float` se dodeljuju kao `0`, `bool` kao `false` i `string` kao prazan string `""`. Ovo se sasvim razlikuje od načina na koji to rade drugi jezici, većina jezika inicijalizuje nedodeljene promenljive kao null ili undefined.

Ovo je odlično, ali šta su ti simboli procenta u našoj `Printf` funkciji? Kao što ste već pretpostavili, oni se koriste za formatiranje izlaza i o njima ćemo saznati više kasnije.

### Konverzija tipa
Sada kada smo videli kako tipovi podataka funkcionišu, hajde da vidimo kako se vrši konverzija tipova.
```
i := 42
f := float64(i)
u := uint(f)

fmt.Printf("%T %T", f, u)
```

    $ go run main.go
    float64 uint

I kao što vidimo, ispisuje se tip kao float64 i uint.

Imajte na umu da se ovo razlikuje od parsiranja.

### Alias tipa
Alias tipa je uveden od verzije Go 1.9. On omogućava programerima da obezbede alternativno ime za postojeći tip i da ga koriste naizmenično sa osnovnim tipom.
```
package main
import "fmt"

type MyAlias = string

func main() {
	var str MyAlias = "I am an alias"
	fmt.Printf("%T - %s", str, str) // Output: string - I am an alias
}
```
### Definisani tipovi
Na kraju, definisani tipovi, za razliku od aliasa tipova ne koriste znak
jednakosti.
```
package main
import "fmt"

type MyDefined string

func main() {
	var str MyDefined = "I am defined"
	fmt.Printf("%T - %s", str, str) // Output: main.MyDefined - I am defined
}
```
Ali čekajte... koja je razlika?

Dakle, definisani tipovi rade više od pukog davanja imena tipu. Prvo definišu novi imenovani tip od osnovnog tipa. Međutim, ovaj definisani tip se razlikuje od bilo kog drugog tipa, uključujući i njegov osnovni tip.

Stoga se ne može koristiti naizmenično sa osnovnim tipom kao alias tipa. U početku je malo zbunjujuće, nadam se da će ovaj primer razjasniti stvari.
```
package main
import "fmt"

type MyAlias = string
type MyDefined string

func main() {
	var alias MyAlias
	var def MyDefined

	// ✅ Works
	var copy1 string = alias

	// ❌ Cannot use def (variable of type MyDefined) as string value in variable
	var copy2 string = def

	fmt.Println(copy1, copy2)
}
```
Kao što vidimo, ne možemo koristiti definisani tip naizmenično sa osnovnim tipom, za razliku od aliasa tipa.

### Formatiranje stringova
`fmt` paket sadrži mnogo funkcija. Da bismo uštedeli vreme, razmotrićemo najčešće korišćene funkcije. Počnimo sa `fmt.Print` našom glavnom funkcijom.
```
...
fmt.Print("What", "is", "your", "name?")
fmt.Print("My", "name", "is", "golang")
...
```
    $ go run main.go
    Whatisyourname?Mynameisgolang

Kao što vidimo, `fmt.Print` ne formatira izlaz, jednostavno uzima string i ispisuje ga.

Zatim, imamo `fmt.Println` što je isto kao i `fmt.Print`, ali dodaje novi red na kraju i takođe ubacuje razmak između argumenata.
```
...
fmt.Println("What", "is", "your", "name?")
fmt.Println("My", "name", "is", "golang")
...
```
    $ go run main.go
    What is your name?
    My name is golang

To je mnogo bolje!

Zatim, `fmt.Printf` poznat nam je i kao  "Formatizater štampe", koji nam omogućava formatiranje brojeva, stringova, bulovih vrednosti i još mnogo toga.

Pogledajmo jedan primer.
```
...
name := "golang"
fmt.Println("What is your name?")
fmt.Printf("My name is %s", name)
...
```
    $ go run main.go
    What is your name?
    My name is golang

Kao što vidimo, to `%s` je zamenjeno našom *name* promenljivom.

Ali pitanje je šta jes `%s` i šta znači?

Dakle, `%s` je jedan od *glagola anotacije* i oni govore funkciji kako da formatira argumente. Pomoću njih možemo kontrolisati stvari poput širine, tipova i preciznosti, a ima ih mnogo.

Sada, hajde da brzo pogledamo još nekoliko primera. Ovde ćemo pokušati daizračunamo procenat i ispišemo ga u konzolu.
```
...
percent := (7.0 / 9) * 100
fmt.Printf("%f", percent)
...
```
    $ go run main.go
    77.777778

Recimo da želimo preciznost od 2 mesta, to možemo uraditi i korišćenjem 
`%.2f`.

Takođe, da bismo dodali znak procenta, moraćemo da ga izbegnemo.
```
...
percent := (7.0 / 9) * 100
fmt.Printf("%.2f%%", percent)
...
```
    $ go run main.go
    77.78 %

Ovo nas dovodi do `fmt.Sprint`, `fmt.Sprintln` i `fmt.Sprintf`. One su u osnovi iste kao i funkcije za štampanje, jedina razlika je što vraćaju string umesto da ga ispisuju.

Hajde da pogledamo jedan primer.
```
...
s := fmt.Sprintf("hex:%x bin:%b", 10 ,10)
fmt.Println(s)
...
```
    $ go run main.go
    hex:a bin:1010

Dakle, kao što vidimo, `fmt.Sprintf` formatira naš ceo broj kao heksadecimalan ili binarni i vraća ga kao string.

Na kraju, imamo višelinijske string literale, koji se mogu koristiti na ovaj
način.
```
...
msg := `
Hello from
multiline
`
fmt.Println(msg)
...
```
Odlično! Ali ovo je samo vrh ledenog brega... zato obavezno pogledajte dokumentaciju za `fmt` paket.

Za one koji dolaze sa C/C++ pozadinom, ovo bi trebalo da deluje prirodno, ali ako dolazite, recimo, sa Pythona ili Javascripta, ovo bi u početku moglo biti malo čudno. Ali je veoma moćno i videćete da se ova funkcionalnost koristiprilično intenzivno.

# Kontrola toka

Hajde da pričamo o kontroli protoka, počevši od if/else.

### if/else
Ovo funkcioniše manje-više isto kao što očekujete, ali izraz ne mora biti
okružen zagradama ().
```
func main() {
	x := 10

	if x > 5 {
		fmt.Println("x is gt 5")
	} else if x > 10 {
		fmt.Println("x is gt 10")
	} else {
		fmt.Println("else case")
	}
}
```
    $ go run main.go
    x is gt 5

##### Kompaktno if

Takođe možemo sažeti naše if naredbe.
```
func main() {
	if x := 10; x > 5 {
		fmt.Println("x is gt 5")
	}
}
```
**Napomena**: Ovaj obrazac je prilično čest.

### Switch
Zatim, imamo switch izjavu, što je često kraći način za pisanje uslovne logike.

U programskom jeziku Go, komanda `switch` pokreće samo prvi slučaj čija je vrednost jednaka uslovnom izrazu, a ne sve slučajeve koji slede. Stoga, za razliku od drugih jezika, `break` izjava se automatski dodaje na kraj svakog
slučaja.

To znači da switch procenjuje slučajeve od vrha do dna, zaustavljajući se kada je slučaj uspešan. Pogledajmo primer:
```
func main() {
	day := "monday"

	switch day {
	case "monday":
		fmt.Println("time to work!")
	case "friday":
		fmt.Println("let's party")
	default:
		fmt.Println("browse memes")
	}
}
```
    $ go run main.go
    time to work!

Switch takođe podržava skraćene deklaracije poput ove:
```
	switch day := "monday"; day {
	case "monday":
		fmt.Println("time to work!")
	case "friday":
		fmt.Println("let's party")
	default:
		fmt.Println("browse memes")
	}
```
Takođe možemo koristiti `fallthrough` ključnu reč da prenesemo kontrolu na sledeći slučaj čak i ako se trenutni slučaj možda nije podudarao.

	switch day := "monday"; day {
	case "monday":
		fmt.Println("time to work!")
		fallthrough
	case "friday":
		fmt.Println("let's party")
	default:
		fmt.Println("browse memes")
	}

I ako ovo pokrenemo, videćemo da nakon prvog podudaranja slučaja, naredba `switch` nastavlja na sledeći slučaj zbog `fallthrough` ključne reči.

    $ go run main.go
    time to work!
    let's party

Takođe `switch` možemo koristiti bez ikakvog uslova, što je isto kao i `switch true`.
```
x := 10
switch {
	case x > 5:
		fmt.Println("x is greater")
	default:
		fmt.Println("x is not greater")
}
```
### Petlje
Sada, usmerimo pažnju na petlje. Dakle, u Gou imamo samo jednu vrstu petlje, a to je `for` petlja.

Baš kao i `if` naredba, `for` petlja, ne zahteva nikakve zagrade () za razliku od drugih jezika.

##### Definicija for petlje

Počnimo sa osnovnim `for` ciklusom.
```
func main() {
	for i := 0; i < 10; i++ {
		fmt.Println(i)
	}
}
```
Osnovna for petlja ima tri komponente odvojene tačka-zarezom:

- `init` izjava       : koja se izvršava pre prve iteracije.
- `conitions` izraz   : koji se izračunava pre svake iteracije.
- `post` izjava       : koja se izvršava na kraju svake iteracije.

##### Break i continue
Kao što se i očekivalo, Go takođe podržava i `break` i `continue` naredbe za kontrolu petlje. Hajde da pokušamo sa brzim primerom:
```
func main() {
	for i := 0; i < 10; i++ {
		if i < 2 {
			continue
		}
		fmt.Println(i)

		if i > 5 {
			break
		}
	}
	fmt.Println("We broke out!")
}
```
Dakle, `continue` naredba se koristi kada želimo da preskočimo preostali deo petlje, a `break` naredba se koristi kada želimo da izađemo iz petlje.

Takođe, `init` i `post` naredbe for petlje su opcione, tako da možemo da nateramo našu `for` petlju da se ponaša kao `while` petlja.
```
func main() {
	i := 0
	for ;i < 10; {
		i += 1
	}
}
```
**Napomena**: možemo ukloniti i dodatne tačke-zareze da bismo je učinili malo čistijim.

##### Beskonačna petlja
Konačno, ako izostavimo uslov petlje, ona se ponavlja zauvek, tako da sebeskonačna petlja može kompaktno izraziti ovako:
```
func main() {
	for {
		// do stuff here
	}
}
```

# Funkcije

U ovom tutorijalu ćemo razgovarati o tome kako radimo sa funkcijama u programskom jeziku Go. Dakle, počnimo sa jednostavnom deklaracijom funkcije.

### Deklaracija funkcije
```
func myFunction() {}
```
I možemo je pozvati ili izvršiti na sledeći način.
```
...
myFunction()
...
```
Hajde da joj prosledimo neke parametre.
```
func main() {
	myFunction("Hello")
}

func myFunction(p1 string) {
	fmt.Println(p1)
}
```
    $ go run main.go

Kao što vidimo, ispisuje našu poruku. Takođe možemo da napravimo skraćenu deklaraciju ako uzastopni parametri imaju isti tip. Na primer:
```
func myNextFunction(p1, p2 string) {}
```
### Vraćanje vrednosti
Sada hajde da vratimo vrednost iz funkcije.
```
func main() {
	s := myFunction("Hello")
	fmt.Println(s)
}

func myFunction(p1 string) string {
	msg := fmt.Sprintf("%s function", p1)
	return msg
}
```
### Višestruki povratak
Zašto vraćati jednu vrednost istovremeno, kada možemo više? Go takođe podržava višestruko vraćanje!
```
func main() {
	s, i := myFunction("Hello")
	fmt.Println(s, i)
}

func myFunction(p1 string) (string, int) {
	msg := fmt.Sprintf("%s function", p1)
	return msg, 10
}
```
### Imenovani povratak
Još jedna sjajna funkcija je `named return`, gde se povratna vrednost može imenovati i tretirati kao sopstvene promenljive funkcije.
```
func myFunction(p1 string) (s string, i int) {
	s = fmt.Sprintf("%s function", p1)
	i = 10
	return
}
```
Obratite pažnju kako smo dodali `return` iskaz bez ikakvih argumenata, ovo je takođe poznato kao `naked return`.

Reći ću da, iako je ova funkcija zanimljiva, molim vas da je koristite pažljivo jer bi to moglo smanjiti čitljivost većih funkcija.

### Funkcije kao vrednosti
Zatim, hajde da pričamo o funkcijama kao vrednostima, u Go-u su funkcije građani prve prve klase i možemo ih koristiti kao vrednosti. Dakle, hajde da sredimo našu funkciju i isprobamo je!
```
func myFunction() {
	fn := func() {
		fmt.Println("inside fn")
	}
	fn()
}
```
Takođe možemo pojednostaviti ovo tako što ćemo napraviti ananonimnu funkciju.
```
func myFunction() {
	func() {
		fmt.Println("inside fn")
	}()
}
```
Obratite pažnju kako to izvršavamo koristeći zagradu na kraju.

### Zatvaranja
Zašto bismo se tu zaustavili? Hajde da vratimo funkciju i tako kreiramo nešto što se zove zatvaranje. Jednostavna definicija može biti da je zatvaranje funkcija koja referencira promenljive izvan svog tela.
 
Zatvaranja su leksički ograničena, što znači da funkcije mogu pristupiti vrednostima u opsegu prilikom definisanja funkcije.
```
func myFunction() func(int) int {
	sum := 0
	return func(v int) int {
		sum += v
		return sum
	}
}
...
add := myFunction()
add(5)
fmt.Println(add(10))
...
```
Kao što vidimo, dobijamo rezultat 15 jer sumje promenljiva povezana sa funkcijom. Ovo je veoma moćan koncept i definitivno ga morate znati.

### Varijadičke funkcije

Sada pogledajmo varijadne funkcije, koje mogu prihvatiti nula ili više argumenata koristeći elipsis `...` operator.

Primer ovde bi bila funkcija koja može da primi gomilu vrednosti.
```
func main() {
	sum := add(1, 2, 3, 5)
	fmt.Println(sum)
}

func add(values ...int) int {
	sum := 0

	for _, v := range values {
		sum += v
	}

	return sum
}
```
Baš kul, zar ne? Takođe, ne brinite o `range` ključnoj reči, o tome ćemo kasnije razgovarati u kursu.

**Zanimljivost**: `fmt.Println` je varijadička funkcija, zato smo joj mogli proslediti više vrednosti.

### Init
U Gou, `init` je posebna funkcija životnog ciklusa aplikacije koja se izvršava pre `main` funkcije.

Slično kao `main`, `init` funkcija ne prima nikakve argumente niti vraća bilo kakvu vrednost. Pogledajmo kako to funkcioniše na primeru.
```
package main
import "fmt"

func init() {
	fmt.Println("Before main!")
}

func main() {
	fmt.Println("Running main")
}
```
Kao što se i očekivalo, `init` funkcija je izvršena pre main funkcije.

    $ go run main.go
    Before main!
    Running main

Za razliku od `main`, može postojati više od jedne `init` funkcije u jednoj ili više datoteka.

Za više `init` funkcije u jednoj datoteci, njihova obrada se vrši redosledom njihove deklaracije, dok se `init` funkcije deklarisane u više datoteka obrađuju prema leksikografskom redosledu imena datoteke.
```
package main
import "fmt"

func init() {
	fmt.Println("Before main!")
}

func init() {
	fmt.Println("Hello again?")
}

func main() {
	fmt.Println("Running main")
}
```
I ako ovo pokrenemo, videćemo da su `init` funkcije izvršene redosledom kojim su deklarisane.

    $ go run main.go
    Before main!
    Hello again?
    Running main

Funkcija `init` je opcionalna i posebno se koristi za bilo koje globalno podešavanje koje može biti neophodno za naš program, kao što je: 
- uspostavljanje veze sa bazom podataka, 
- preuzimanje konfiguracionih datoteka, 
- podešavanje promenljivih okruženja itd.

### Defer
Na kraju, hajde da razgovaramo o `defer` ključnoj reči koja nam omogućava da odložimo izvršavanje funkcije dok se okolna funkcija ne vrati.
```
func main() {
	defer fmt.Println("I am finished")
	fmt.Println("Doing some work...")
}
```
Možemo koristiti više odloženih funkcija, ovo nas dovodi do onoga što je poznato kao `defer stek`. Pogledajmo primer:
```
func main() {
	defer fmt.Println("I am finished")
	defer fmt.Println("Are you?")

	fmt.Println("Doing some work...")
}
```
    $ go run main.go
    Doing some work...
    Are you?
    I am finished

Kao što vidimo, `defer` naredbe se slažu i izvršavaju po principu `LIFO steka`.

Dakle, `defer` je neverovatno koristan i često se koristi za čišćenje ili rukovanje greškama.

Funkcije se takođe mogu koristiti sa generičkim tipovima, ali ćemo o njima razgovarati kasnije u kursu.

# Moduli

`modul` je kolekcija Go paketa smeštenih u stablu datoteka sa `go.mod` datotekom u korenu, pod uslovom da je direktorijum unutar `$GOPATH/src`.

Go moduli su predstavljeni u Go 1.11, donose nativnu podršku za verzije i module. Ranije nam je bila potrebna GO111MODULE=on zastavica da bismo uključili funkcionalnost modula kada je bila eksperimentalna. Ali sada, nakon Go 1.13, režim modula je podrazumevani za sav razvoj.

Ali čekajte, šta je `GOPATH`?

`GOPATH` je promenljiva koja definiše koren našeg radnog prostora i sadrži sledeće direktorijume:

- `src` : sadrži izvorni kod Go-a organizovan u hijerarhiju.
- `pkg` : sadrži kompajlirani kod paketa.
- `bin` : sadrži kompajlirane binarne datoteke i izvršne datoteke.

Kao i ranije, kreirajmo novi modul koristeći `go mod init` komandu koja kreira
novi modul i inicijalizuje `go.mod` datoteku koja ga opisuje.

    $ go mod init example

Važno je napomenuti da Go modul može odgovarati i Github repozitorijumu ako planirate da objavite modul.

Sada, hajde da istražimo `go.mod` koja je datoteka koja definiše putanju modula, a takođe i putanju uvoza koja se koristi za korenski direktorijum i njegove zahteve zavisnosti.
```
module <name>
go <version>
require (
	...
)
```
Ako želimo da dodamo novu zavisnost, koristićemo `go install` komandu:

    $ go install github.com/rs/zerolog

Kao što vidimo, kreirana je i `go.sum` datoteka. Ova datoteka sadrži očekivane heševe sadržaja novih modula.

Možemo navesti sve zavisnosti koristeći `go list` komandu:

    $ go list -m all

Ako se zavisnost ne koristi, možemo je jednostavno ukloniti pomoću `go mod tidy` komande:

    $ go mod tidy

Završavajući našu diskusiju o modulima, hajde da razgovaramo i o prodaji.

Prodaja je čin pravljenja sopstvene kopije paketa trećih strana koje vaš projekat koristi. Te kopije se tradicionalno smeštaju unutar svakog projekta, a zatim čuvaju u repozitorijumu projekata.

To se može uraditi putem `go mod vendor` komande.

Dakle, hajde da ponovo instaliramo uklonjeni modul koristeći `go mod tidy`.
```
package main
import "github.com/rs/zerolog/log"

func main() {
	log.Info().Msg("Hello")
}
```
    $ go mod tidy
    go: finding module for package github.com/rs/zerolog/log
    go: found github.com/rs/zerolog/log in github.com/rs/zerolog v1.26.1

    $ go mod vendor

Nakon što se `go mod vendor` komanda izvrši, biće kreiran *vendor* direktorijum.

├─ go.mod <br>
├─ go.sum <br>
├─ go.work <br>
├─ main.go <br>
└─ vendor <br>
...├─ github.com <br>
....|....└─ rs <br>
....|........└─ zerolog <br>
....|........└─ .. <br>
...└─ modules.txt <br>

# Paketi

### Šta su paketi?
Paket nije ništa drugo do direktorijum koji sadrži jednu ili više Go izvornih datoteka ili drugih Go paketa.

To znači da svaka Go datoteka sa izvornim kodom mora pripadati paketu, a deklaracija paketa se vrši na vrhu svake datoteke sa izvornim kodom na sledeći način:
```
package <package_name>
```
Do sada smo sve uradili unutar package `main`. Po konvenciji, izvršni programi 
(pod tim mislim na one sa main paketom) se nazivaju komande, drugi se jednostavno 
nazivaju paketi.

Paket `main` bi takođe trebalo da sadrži `main()` funkciju koja je posebna funkcija koja deluje kao ulazna tačka izvršnog programa.

Pogledajmo primer kreiranjem sopstvenog paketa `custom` i dodavanjem nekih izvornih datoteka u njega kao što su code.go.
```
package custom
```
Pre nego što nastavimo dalje, trebalo bi da razgovaramo o uvozu i izvozu. Baš kao i drugi jezici, i go ima koncept uvoza i izvoza, ali je veoma elegantan.

U osnovi, bilo koja vrednost (kao što je promenljiva ili funkcija) može se izvesti i biti vidljiva iz drugih paketa ako je definisana velikim slovima.

Hajde da pokušamo sa primerom u našem custompaketu.
```
package custom

var value int = 10 // Will not be exported
var Value int = 20 // Will be exported
```
Kao što vidimo, mali identifikatori neće biti izvezeni i biće privatni za paket
u kojem su definisani. U našem slučaju, `custom` paket.

To je odlično, ali kako da ga uvezemo ili mu pristupimo? Pa, isto kao što smo
do sada radili nesvesno. Hajde da odemo do naše main.go datoteke i uvezemo naš
custompaket.

Ovde se na to možemo pozivati koristeći module smo ranije inicijalizovali u
našoj `go.mod` datoteci.
```
---go.mod---
module example
go 1.18

---main.go--
package main
import "example/custom"

func main() {
	custom.Value
}
```
Obratite pažnju kako je ime paketa kombinovano sa putanjom uvoza.

Možemo uvesti više paketa i na ovaj način.
```
package main
import (
	"fmt"
	"example/custom"
)

func main() {
	fmt.Println(custom.Value)
}
```
Takođe možemo da koristimo aliase za naše uvoze kako bismo izbegli kolizije u nazivu paketa.
```
package main

import (
	"fmt"
	abcd "example/custom"
)

func main() {
	fmt.Println(abcd.Value)
}
```
### Spoljne zavisnosti
U programu Go, nismo ograničeni samo na rad sa lokalnim paketima, već možemo instalirati i eksterne pakete koristeći go install komandu kao što smo ranije videli.

Dakle, hajde da preuzmemo jednostavan paket za evidentiranje github.com/rs/zerolog/log.

    $ go install github.com/rs/zerolog
```
package main
import (
	"github.com/rs/zerolog/log"
	abcd "example/custom"
)

func main() {
	log.Print(abcd.Value)
}
```
Takođe, obavezno proverite `go doc` paketa koje instalirate, koji se obično nalazi u `readme` datoteci projekta. `go doc` analizira izvorni kod i generiše dokumentaciju u HTML formatu. Referenca na njega se obično nalazi u `readme` datotekama.

Na kraju, dodaću da Go nema posebnu konvenciju "strukture foldera", uvek pokušajte da organizujete svoje pakete na jednostavan i intuitivan način.

# Radni prostori

Višemodulni radni prostoria su predstavljeni u Go 1.18.

Radni prostori nam omogućavaju da radimo sa više modula istovremeno bez potrebe za uređivanjem `go.mod` datoteka za svaki modul. Svaki modul unutar radnog prostora se tretira kao korenski modul prilikom rešavanja zavisnosti.

Da bismo ovo bolje razumeli, počnimo sa kreiranjem `hello` modula.

    $ mkdir workspaces && cd workspaces
    $ mkdir hello && cd hello
    $ go mod init hello

U svrhu demonstracije, dodaću jednostavan `main.go` i instalirati primer paketa.
```
package main
import (
	"fmt"
	"golang.org/x/example/stringutil"
)

func main() {
	result := stringutil.Reverse("Hello Workspace")
	fmt.Println(result)
}
```
    $ go get golang.org/x/example
    go: downloading golang.org/x/example v0.0.0-20220412213650-2e68773dfca0
    go: added golang.org/x/example v0.0.0-20220412213650-2e68773dfca0

I ako ovo pokrenemo, trebalo bi da vidimo naš izlaz u obrnutom redosledu.

    $ go run main.go
    ecapskroW olleH

Ovo je odlično, ali šta ako želimo da izmenimo `stringutil` modul od kog zavisi naš kod?

Do sada smo to morali da radimo koristeći `replace` direktivu u `go.mod` datoteci, ali sada hajde da vidimo kako možemo da koristimo radne prostore ovde.

Dakle, hajde da kreiramo naš radni prostor u workspaces direktorijumu.

    $ go work init

Ovo će kreirati `go.work` datoteku.

    $ cat go.work
    go 1.18

Takođe ćemo dodati naš `hello` modul u radni prostor.

    $ go work use ./hello

Ovo bi trebalo da ažurira `go.work` datoteku sa referencom na naš `hello` modul.
```
go 1.18
use ./hello
```
Sada, hajde da preuzmemo i izmenimo `stringutil` paket i ažuriramo implementaciju `Reverse` funkcije.

    $ git clone https://go.googlesource.com/example
    Cloning into 'example'...
    remote: Total 204 (delta 39), reused 204 (delta 39)
    Receiving objects: 100% (204/204), 467.53 KiB | 363.00 KiB/s, done.
    Resolving deltas: 100% (39/39), done.
```
example/stringutil/reverse.go

func Reverse(s string) string {
	return fmt.Sprintf("I can do whatever!! %s", s)
}
```
Konačno, dodajmo example paket našem radnom prostoru.
```
$ go work use ./example
$ cat go.work
go 1.18
use (
	./example
	./hello
)
```
Odlično, sada ako pokrenemo naš hello modul primetićemo da je `Reverse` funkcija izmenjena.

    $ go run hello
    I can do whatever!! Hello Workspace

Ovo je veoma potcenjena funkcija iz Go 1.18, ali je prilično korisna u određenim okolnostima.

# Korisne komande

Tokom naše diskusije o modulima, razgovarali smo o nekim go komandama vezanim za go module, a sada ćemo razgovarati o nekim drugim važnim komandama.

Počevši od `go fmt`, koja formatira izvorni kod i to sprovodi tako da se možemo fokusirati na to kako bi naš kod trebalo da funkcioniše, a ne na to kako bi naš kod trebalo da izgleda.

    $ go fmt

Ovo može delovati malo čudno u početku, posebno ako dolazite iz sveta Javascripta ili Pythona kao ja, ali iskreno, prilično je lepo ne brinuti o pravilima lintovanja.

Zatim, imamo `go vet` izveštaje o verovatnim greškama u našim paketima.

Dakle, ako napravim grešku u sintaksi, a zatim pokrenem go vet, trebalo bi da me obavesti o greškama.

    $ go vet

Zatim, imamo `go env` koja jednostavno ispisuje sve informacije o go okruženju, o nekim od ovih promenljivih za vreme izgradnje ćemo saznati kasnije.

Na kraju, imamo `go doc` koji prikazuje dokumentaciju za paket ili simbol, evo primera fmt paketa.

    $ go doc -src fmt Printf

Hajde da koristimo go help komandu da vidimo koje su druge komande dostupne.

    $ go help

Kao što vidimo, imamo:

- `go fix` - pronalazi Go programe koji koriste stare API-je i prepisuje ih da koriste novije.
- `go generate` - obično se koristi za generisanje koda.
- `go install` - kompajlira i instalira pakete i zavisnosti.
- `go clean` - koristi se za čišćenje datoteka koje generišu kompajleri.

Neke druge veoma važne komande su `go build` i `go test`, ali ćemo o njima detaljnije saznati kasnije u kursu.

### Build

Izrada statičkih binarnih datoteka jedna je od najboljih karakteristika Go jezika koja nam omogućava efikasno isporučivanje našeg koda.

To možemo vrlo lako uraditi pomoću `go build` komande.
```
package main
import "fmt"

func main() {
	fmt.Println("I am a binary!")
}
```
    $ go build

Ovo bi trebalo da proizvede binarnu datoteku sa imenom našeg modula. Na primer, ovde imamo *example*.

Takođe možemo samo odrediti naziv prevedenog binarnog izlaza.

    $ go build -o app

Sada, da bismo ovo pokrenuli, jednostavno treba da ga izvršimo.

    $ ./app
    I am a binary!

Da, to je jednostavno tako!

### Promenljive okruženja značajne za compile-time

Sada, hajde da razgovaramo o nekim važnim varijablama vremena izgradnje, počevši od:

    $GOOS i $GOARCH

Ove promenljive okruženja nam pomažu da napravimo go programe za različite operativne sisteme i  arhitekture procesora.

Možemo navesti sve podržane arhitekture pomoću `go tool` komande.

    $ go tool dist list
    android/amd64
    ios/amd64
    js/wasm
    linux/amd64
    windows/arm64
    .
    .
    .

Evo primera za pravljenje izvršne datoteke za Windows iz macOS-a!

    $ GOOS=windows 
    $ GOARCH=amd64 
    $ go build -o app.exe

    
**Promenljiva $CGO_ENABLED**

Ova promenljiva nam omogućava da konfigurišemo CGO, što je način u Go-u za pozivanje C koda.

Ovo nam pomaže da napravimo statički povezan binarni fajl koji radi bez ikakvih spoljnih zavisnosti.

Ovo je prilično korisno, recimo, kada želimo da pokrenemo naše go binarne datoteke u docker kontejneru sa minimalnim spoljnim zavisnostima.

Evo primera kako se koristi:

    $ CGO_ENABLED=0 
    $ go build -o app

# Pointeri

Jednostavno definisano, `pointer` je promenljiva koja se koristi za čuvanje memorijske adrese druge promenljive.

Može se deklarisati ovako:
```
var x *T
```
Gde je T tip kao što su `int`, `string`, `float32`, i tako dalje.

Hajde da pokušamo jednostavan primer i vidimo pointere u akciji.
```
package main
import "fmt"

func main() {
	var p *int
	fmt.Println(p)
}
```
    $ go run main.go
    nil

Hmm, ovo štampa nil, ali šta je nil? Dakle, nil je unapred deklarisani identifikator u Go-u koji predstavlja nultu vrednost za pointere, interfejse, kanale, mape i isečke.

Ovo je baš kao ono što smo naučili u odeljku o promenljivim i tipovima podataka, gde smo videli da neinicijalizovani `int` ima nultu vrednost `0`, a `bool` ima `false` i tako dalje.

### Referenciranje (uzimanje adrese)

U redu, sada hajde da dodelimo vrednost pointeru.
```
package main
import "fmt"

func main() {
	a := 10
	var p *int = &a
	fmt.Println("address:", p)
}
```
Koristimo `&` operator da bismo preuzeli memorijsku adresu promenljive. Ovo se naziva *referenciranje promenljive*.

    $ go run main.go
    0xc0000b8000

Referenca je vrednost memorijske adrese promenljive *a*.

### Dereferenciranje (uzimanje vrednosti)

Takođe možemo koristiti `*` operator da bismo preuzeli vrednost sačuvanu u promenljivoj na koju pointer pokazuje. Ovo se naziva i *dereferenciranje promenljive*.

Na primer, možemo pristupiti vrednosti promenljive a preko pointera *p* koristeći * operator.
```
package main
import "fmt"

func main() {
	a := 10
	var p *int = &a
	fmt.Println("address:", p)
	fmt.Println("value:", *p)
}
```
    $ go run main.go
    address: 0xc000018030
    value: 10

Ne samo da joj možemo pristupiti već i promeniti je pomoću pointera.
```
package main
import "fmt"

func main() {
	a := 10
	var p *int = &a
	fmt.Println("before", a)
	fmt.Println("address:", p)

	*p = 20
	fmt.Println("after:", a)
}
```
    $ go run main.go
    before 10
    address: 0xc000192000
    after: 20

Mislim da je ovo prilično uredno!

### Pointeri kao argumenti funkcije

Pointeri se takođe mogu koristiti kao argumenti za funkciju kada treba da prosledimo neke podatke referencom.

Evo jednog primera:
```
myFunction(&a)
...

func myFunction(ptr *int) {}
```

##### Funkcija new

Drugi način inicijalizacije pointera je korišćenje `new` funkcije koja uzima tip kao argument, alocira dovoljno memorije da smesti vrednost tog tipa i vraća pointer na nju.

Evo jednog primera:
```
package main

import "fmt"

func main() {
	p := new(int)
	*p = 100

	fmt.Println("value", *p)
	fmt.Println("address", p)
}
```
    $ go run main.go
    value 100
    address 0xc000018030

### Pointer na pointer

Evo jedne zanimljive ideje... možemo li da napravimo pointer ka pointeru? Odgovor je da! Da, možemo.
```
package main

import "fmt"

func main() {
	p := new(int)
	*p = 100

	p1 := &p

	fmt.Println("P value", *p, " address", p)
	fmt.Println("P1 value", *p1, " address", p)

	fmt.Println("Dereferenced value", **p1)
}
```
    $ go run main.go
    P value 100  address 0xc0000be000
    P1 value 0xc0000be000  address 0xc0000be000
    Dereferenced value 100

Obratite pažnju kako vrednost p1odgovara adresi od p.

Takođe, važno je znati da pointeri u Go-u ne podržavaju pointerku aritmetiku kao u C-u ili C++-u.
```
p1 := p * 2 // Compiler Error: invalid operation
```
Međutim, možemo uporediti dva pointera istog tipa radi jednakosti koristeći == operator.
```
p := &a
p1 := &a
fmt.Println(p == p1)
```
Ali zašto?

To nas dovodi do pitanja od milion dolara, zašto su nam potrebni saveti?

Pa, nema definitivnog odgovora na to, a pointeri su samo još jedna korisna funkcija koja nam pomaže da efikasno mutiramo naše podatke bez kopiranja velike količine podataka.

Na kraju, dodaću da ako dolazite iz jezika koji nema pojam pointera, ne paničite i pokušajte da formirate mentalni model kako pointeri funkcionišu.

# Strukture

Dakle, struct je korisnički definisan tip koji sadrži kolekciju imenovanih polja. U osnovi, koristi se za grupisanje povezanih podataka zajedno u jednu jedinicu.

Ako dolazite iz objektno orijentisanog okruženja, zamislite strukture kao lagane klase koje podržavaju **kompoziciju**, ali ne i **nasleđivanje**.

### Definisanje

Možemo definisati struct ovako:
```
type Person struct {}
```
Koristimo `type` ključnu reč da bismo uveli novi tip, nakon čega sledi ime, a zatim struct ključna reč da bismo naznačili da definišemo strukturu.

Sada, hajde da joj dodamo neka polja:
```
type Person struct {
	FirstName string
	LastName  string
	Age       int
}
```
A ako polja imaju isti tip, možemo ih i sakupiti.
```
type Person struct {
	FirstName, LastName string
	Age                 int
}
```
### Deklarisanje i inicijalizacija

Sada kada imamo strukturu, možemo je deklarisati isto kao i druge tipove podataka.
```
func main() {
	var p1 Person
	fmt.Println("Person 1:", p1)
}
```
	$ go run main.go
	Person 1: {  0}

Kao što vidimo, sva polja strukture su inicijalizovana svojim nultim vrednostima. Dakle, FirstName i LastNamesu postavljeni na "" prazan string, a Age je postavljeno na 0.

Takođe strukturu možemo inicijalizovati kao `struct literal`.
```
func main() {
	var p1 Person
	fmt.Println("Person 1:", p1)
	var p2 = Person{FirstName: "Karan", LastName: "Pratap Singh", Age: 22}
	fmt.Println("Person 2:", p2)
}
```
Radi čitljivosti, možemo razdvojiti novim redom, ali će to takođe zahtevati završni zarez.
```
	var p2 = Person{
		FirstName: "Karan",
		LastName:  "Pratap Singh",
		Age:       22,
	}
```
    $ go run main.go
    Person 1: {  0}
    Person 2: {Karan Pratap Singh 22}

Takođe možemo inicijalizovati samo podskup polja.
```
func main() {
	var p1 Person
	fmt.Println("Person 1:", p1)
	
	var p2 = Person{
		FirstName: "Karan",
		LastName:  "Pratap Singh",
		Age:       22,
	}
	fmt.Println("Person 2:", p2)

	var p3 = Person{
		FirstName: "Tony",
		LastName:  "Stark"`
    }
    fmt.Println("Person 3:", p3)
}
```
    $ go run main.go
    Person 1: {  0}
    Person 2: {Karan Pratap Singh 22}
    Person 3: {Tony Stark 0}

Kao što vidimo, polje za godine osobe 3 je podrazumevano podešeno na nultu vrednost. 

### Inicijalizacija strukture poljima bez imena

Go strukture takođe podržavaju inicijalizaciju bez imena polja.
```
func main() {
	var p1 Person
	fmt.Println("Person 1:", p1)

	var p2 = Person{
		FirstName: "Karan",
		LastName:  "Pratap Singh",
		Age:       22,
	}
	fmt.Println("Person 2:", p2)

	var p3 = Person{
		FirstName: "Tony",
		LastName:  "Stark",
	}
	fmt.Println("Person 3:", p3)

	var p4 = Person{"Bruce", "Wayne"}
	fmt.Println("Person 4:", p4)
}
```
Ali evo u čemu je caka, moraćemo da obezbedimo sve vrednosti tokom inicijalizacije ili će ona ne uspeti.

	$ go run main.go
	# command-line-arguments
	./main.go:30:27: too few values in Person{...}
```
	var p4 = Person{"Bruce", "Wayne", 40}
	fmt.Println("Person 4:", p4)
```
Takođe možemo deklarisati anonimnu strukturu.
```
func main() {
	var p1 Person
	fmt.Println("Person 1:", p1)

	var p2 = Person{
		FirstName: "Karan",
		LastName:  "Pratap Singh",
		Age:       22,
	}
	fmt.Println("Person 2:", p2)

	var p3 = Person{
		FirstName: "Tony",
		LastName:  "Stark",
	}
	fmt.Println("Person 3:", p3)

	var p4 = Person{"Bruce", "Wayne", 40}
	fmt.Println("Person 4:", p4)

	var a = struct {
		Name string
	}{"Golang"}
	fmt.Println("Anonymous:", a)
}
```
### Pristupanje poljima struktura

Hajde da malo sredimo naš primer i vidimo kako možemo pristupiti pojedinačnim poljima.
```
func main() {
	var p = Person{
		FirstName: "Karan",
		LastName:  "Pratap Singh",
		Age:       22,
	}
	fmt.Println("FirstName", p.FirstName)
}
```
Takođe možemo kreirati pointer na strukture.
```
func main() {
	var p = Person{
		FirstName: "Karan",
		LastName:  "Pratap Singh",
		Age:       22,
	}
	ptr := &p
	fmt.Println((*ptr).FirstName)
	fmt.Println(ptr.FirstName)
}
```
Obe izjave su jednake jer **u Go-u ne moramo eksplicitno dereferencirati pointer.** Takođe možemo koristiti ugrađenu `new` funkciju.
```
func main() {
	p := new(Person)
	p.FirstName = "Karan"
	p.LastName = "Pratap Singh"
	p.Age = 22
	fmt.Println("Person", p)
}
```
	$ go run main.go
	Person &{Karan Pratap Singh 22}

Uzgred, dve strukture su jednake ako su sva njihova odgovarajuća polja takođe jednaka.
```
func main() {
	var p1 = Person{"a", "b", 20}
	var p2 = Person{"a", "b", 20}
	fmt.Println(p1 == p2)
}
```
	$ go run main.go
	true

### Izvezena polja

Sada hajde da saznamo šta su izvezena, a šta neizvezena polja u strukturi. Isto kao i pravila za promenljive i funkcije, ako je polje strukture deklarisano malim slovima, ono neće biti izvezeno i biće vidljivo samo paketu u kojem je definisano.
```
type Person struct {
	FirstName, LastName  string
	Age                  int
	zipCode              string
}
```
Dakle, zipCode polje neće biti izvezeno. Takođe, isto važi i za Person strukturu, ako je preimenujemo u person, ona se takođe neće izvesti.
```
type person struct {
	FirstName, LastName  string
	Age                  int
	zipCode              string
}
```
### Ugrađivanje i kompozicija

Kao što smo ranije pomenuli, Go ne podržava nasleđivanje, ali možemo uraditi nešto slično sa ugrađivanjem.
```
type Person struct {
	FirstName, LastName  string
	Age                  int
}

type SuperHero struct {
	Person
	Alias string
}
```
Dakle, naša nova struktura će imati sva svojstva originalne strukture. I trebalo bi da se ponaša isto kao i naša normalna struktura.
```
func main() {
	s := SuperHero{}
	s.FirstName = "Bruce"
	s.LastName = "Wayne"
	s.Age = 40
	s.Alias = "batman"
	fmt.Println(s)
}
```
	$ go run main.go
	{{Bruce Wayne 40} batman}

Međutim, ovo se obično ne preporučuje i u većini slučajeva, kompozicija je poželjnija. Dakle, umesto ugrađivanja, jednostavno ćemo ga definisati kao normalno polje.
```
type Person struct {
	FirstName, LastName  string
	Age                  int
}

type SuperHero struct {
	Person Person
	Alias  string
}
```
Dakle, možemo prepisati naš primer i sa kompozicijom.
```
func main() {
	p := Person{"Bruce", "Wayne", 40}
	s := SuperHero{p, "batman"}

	fmt.Println(s)
}
```
	$ go run main.go
	{{Bruce Wayne 40} batman}

Opet, ovde nema tačnog ili pogrešnog, ali ipak, ugrađivanje ponekad bude korisno.

### Strukturne oznake

Strukturna oznaka je samo oznaka koja nam omogućava da polju dodamo metapodatke koje se mogu koristiti za prilagođeno ponašanje pomoću `reflect` paketa.

Hajde da naučimo kako možemo definisati strukturne oznake.
```
type Animal struct {
	Name    string `key:"value1"`
	Age     int    `key:"value2"`
}
```
Oznake ćete često pronaći u paketima za kodiranje, kao što su XML, JSON, YAML, ORM i upravljanje konfiguracijom.

Evo primera oznaka za JSON enkoder.
```
type Animal struct {
	Name    string `json:"name"`
	Age     int    `json:"age"`
}
```
### Svojstva struktura

Na kraju, hajde da razgovaramo o svojstvima struktura.

Strukture su vrednosni tipovi. Kada dodelimo jednu struct promenljivu drugoj, kreira se i dodeljuje se novoj struct kopija te promenljive.

Slično, kada prosledimo struct drugoj funkciji, funkcija dobija svoju struct kopiju.
```
package main
import "fmt"

type Point struct {
	X, Y float64
}

func main() {
	p1 := Point{1, 2}
	p2 := p1 // Copy of p1 is assigned to p2
	p2.X = 2
	fmt.Println(p1) // Output: {1 2}
	fmt.Println(p2) // Output: {2 2}
}
```
Prazna struktura zauzima nula bajtova memorije.
```
package main
import (
	"fmt"
	"unsafe"
)

func main() {
	var s struct{}
	fmt.Println(unsafe.Sizeof(s)) // Output: 0
}
```
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
# Isečci

Znam šta misliš, nizovi su korisni, ali pomalo nefleksibilni zbog ograničenja koje izaziva njihova fiksna veličina.

Ovo nas dovodi do isečka, pa šta je onda isečak"?

`Isečak` je segment niza. Isečci se nadovezuju na nizove i pružaju veću snagu,fleksibilnost i praktičnost.

Isečak se sastoji od tri stvari:

- `Pointer-referenca` na osnovni niz.
- `Dužina` segmenta niza koji isečak sadrži.
- `Kapacitet`, maksimalna veličina do koje segment može da raste.

Baš kao i kod `len` funkcije, možemo odrediti kapacitet segmenta koristeći ugrađenu `cap` funkciju. Evo primera:
```
package main

import "fmt"

func main() {
	a := [5]int{20, 15, 5, 30, 25}
	s := a[1:4]

	// Output: Array: [20 15 5 30 25], Length: 5, Capacity: 5
	fmt.Printf("Array: %v, Length: %d, Capacity: %d\n", a, len(a), cap(a))

	// Output: Slice [15 5 30], Length: 3, Capacity: 4
	fmt.Printf("Slice: %v, Length: %d, Capacity: %d", s, len(s), cap(s))
}
```
Ne brinite, detaljno ćemo razgovarati o svemu što je ovde prikazano.

### Deklaracija isečka

Da vidimo kako možemo deklarisati isečak.
```
var s []T
```
Kao što vidimo, ne moramo da navodimo nikakvu dužinu. Hajde da deklarišemo isečak stringova i vidimo kako to funkcioniše.
```
func main() {
	var s []string
	fmt.Println(s)
	fmt.Println(s == nil)
}
```
	$ go run main.go
	[]
	true

Dakle, za razliku od nizova, nulta vrednost isečka je `nil`.

### Inicijalizacija

Postoji više načina za inicijalizaciju našeg isečka. Jedan od načina je korišćenje ugrađene `make` funkcije.

	make([]T, len, cap) []T

```
func main() {
	var s = make([]string, 0, 0)

	fmt.Println(s)
}
```
	$ go run main.go
	[]

Slično nizovima, možemo koristiti `literal slice` da inicijalizujemo naš isečak.
```
func main() {
	var s = []string{"Go", "TypeScript"}

	fmt.Println(s)
}
```
	$ go run main.go
	[Go TypeScript]

Drugi način je kreiranje isečka iz niza. Pošto je isečak segment niza, možemo kreirati isečak od indeksa `low` do indeksa `high` na sledeći način:

	a[low:high]
```
func main() {
	var a = [4]string{
		"C++",
		"Go",
		"Java",
		"TypeScript",
	}

	s1 := a[0:2] // Select from 0 to 2
	s2 := a[:3]  // Select first 3
	s3 := a[2:]  // Select last 2

	fmt.Println("Array:", a)
	fmt.Println("Slice 1:", s1)
	fmt.Println("Slice 2:", s2)
	fmt.Println("Slice 3:", s3)
}
```
	$ go run main.go
	Array: [C++ Go Java TypeScript]
	Slice 1: [C++ Go]
	Slice 2: [C++ Go Java]
	Slice 3: [Java TypeScript]

Nedostatak `low` indeksa podrazumeva 0, a nedostatak `high` indeksa podrazumeva dužinu osnovnog niza (`len(a)`).

Ono što treba napomenuti je da možemo kreirati isečak i iz drugih isečaka, a ne samo iz nizova.
```
var a = []string{
	"C++",
	"Go",
	"Java",
	"TypeScript",
}
```
### Iteracija

Možemo iterirati kroz isečak na isti način kao što iterirate kroz niz, koristeći petlju `for` sa `len` funkcijom ili `range` ključnom reči.

### Funkcije 

Pa, sada, hajde da pričamo o ugrađenim funkcijama za isecanje koje su dostupne u Go-u.

##### Copy

Funkcija `copy()` kopira elemente iz jednog isečka u drugi. Prihvata 2 isečka, odredište i izvor. Takođe vraća broj kopiranih elemenata.

	func copy(dst, src []T) int

Da vidimo kako možemo da ga koristimo.
```
func main() {
	s1 := []string{"a", "b", "c", "d"}
	s2 := make([]string, len(s1))

	e := copy(s2, s1)

	fmt.Println("Src:", s1)
	fmt.Println("Dst:", s2)
	fmt.Println("Elements:", e)
}
```
	$ go run main.go
	Src: [a b c d]
	Dst: [a b c d]
	Elements: 4

Kao što se i očekivalo, naša 4 elementa iz izvornog isečka su kopirana u odredišni sečak.

##### Append

Sada, pogledajmo kako možemo dodati podatke isečku koristeći ugrađenu append funkciju koja dodaje nove elemente na kraj datog isečka.

Prihvata isečak i promenljiv broj argumenata. Zatim vraća novi isečak koji sadrži sve elemente.

	append(slice []T, elems ...T) []T

Hajde da to pokušamo na primeru dodavanjem elemenata našem isečku.
```
func main() {
	s1 := []string{"a", "b", "c", "d"}
	s2 := append(s1, "e", "f")

	fmt.Println("s1:", s1)
	fmt.Println("s2:", s2)
}
```
	$ go run main.go
	s1: [a b c d]
	s2: [a b c d e f]

Kao što vidimo, novi elementi su dodani i vraćen je novi isečak.

Ali ako dati isečak nema dovoljan kapacitet za nove elemente, onda se dodeljuje novi osnovni niz sa većim kapacitetom.

Svi elementi iz osnovnog niza postojećeg isečka se kopiraju u ovaj novi niz, a zatim se dodaju novi elementi.

### Svojstva isečaka

Na kraju, hajde da razgovaramo o nekim svojstvima isečaka.

Isečci su referentni tipovi, za razliku od nizova.

To znači da će modifikovanje elemenata isečka modifikovati odgovarajuće elemente u referenciranom nizu.
```
package main

import "fmt"

func main() {
	a := [7]string{"Mon", "Tue", "Wed", "Thu", "Fri", "Sat", "Sun"}
	s := a[0:2]
	s[0] = "Sun"

	fmt.Println(a) // Output: [Sun Tue Wed Thu Fri Sat Sun]
	fmt.Println(s) // Output: [Sun Tue]
}
```
Isečci se mogu koristiti i sa varijadičkim tipovima.
```
package main

import "fmt"

func main() {
	values := []int{1, 2, 3}
	sum := add(values...)
	fmt.Println(sum)
}

func add(values ...int) int {
	sum := 0
	for _, v := range values {
		sum += v
	}

	return sum
}
```
# Mape

Mapa je neuređena kolekcija parova `key-value`. Ona preslikava ključeve u vrednosti. Ključevi su jedinstveni unutar mape, dok vrednosti možda nisu.

Koristi se za brzo pretraživanje, pronalaženje i brisanje podataka na osnovu ključeva. To je jedna od najčešće korišćenih struktura podataka.

### Deklaracija

Počnimo sa deklaracijom.

Mapa se deklariše korišćenjem sledeće sintakse:

	var m map[K]V

Gde je K tip ključa, a V je tip vrednosti.

Na primer, evo kako možemo deklarisati mapu string ključeva i int vrednosti.
```
func main() {
	var m map[string]int

	fmt.Println(m)
}
```
	$ go run main.go
	nil

Kao što vidimo, nulta vrednost mape je `nil`.

Mapa `nil` nema ključeve. Štaviše, svaki pokušaj dodavanja ključeva mapi `nil` rezultiraće greškom tokom izvršavanja.

PS. Ovako deklarisana mapa ne služi ničemu, jer nema svoj alocirani prostor, zbog toga se njoj ne može dodati ni jedan par `key:value`. Jedino se može ići sa `new` funkcijom, dobiti alokacija i potom to dodeliti ovako deklarisanoj mapi.

### Inicijalizacija

Postoji više načina za inicijalizaciju mape.

##### Funkcija make

Možemo koristiti ugrađenu `make` funkciju koja dodeljuje memoriju za referencirane tipove podataka i inicijalizuje njihove osnovne strukture podataka.
```
func main() {
	var m = make(map[string]int)

	fmt.Println(m)
}
```
	$ go run main.go
	map[]

##### Map literal

Drugi način je korišćenje literala mape.
```
func main() {
	var m = map[string]int{
		"a": 0,
		"b": 1,
	}

	fmt.Println(m)
}
```
Imajte na umu da je završni zarez obavezan.

	$ go run main.go
	map[a:0 b:1]

Kao i uvek, možemo koristiti i naše prilagođene tipove.
```
type User struct {
	Name string
}

func main() {
	var m = map[string]User{
		"a": User{"Peter"},
		"b": User{"Seth"},
	}

	fmt.Println(m)
}
```
Možemo čak i ukloniti tip vrednosti i Go će to shvatiti!
```
var m = map[string]User{
	"a": {"Peter"},
	"b": {"Seth"},
}
```
	$ go run main.go
	map[a:{Peter} b:{Seth}]

### Dodavanje vrednosti na mapu

Sada, hajde da vidimo kako možemo dodati vrednost našoj mapi.
```
func main() {
	var m = map[string]User{
		"a": {"Peter"},
		"b": {"Seth"},
	}

	m["c"] = User{"Steve"}

	fmt.Println(m)
}
```
	$ go run main.go
	map[a:{Peter} b:{Seth} c:{Steve}]

### Preuzmimanje vrednosti sa mape

Takođe možemo da preuzmemo naše vrednosti sa mape pomoću ključa.
```
...
c := m["c"]
fmt.Println("Key c:", c)
```
	$ go run main.go
	key c: {Steve}
Šta ako koristimo ključ koji nije prisutan na mapi?
```
...
d := m["d"]
fmt.Println("Key d:", d)
```
Da, pogodili ste! Dobićemo nultu vrednost tipa vrednosti mape.

	$ go run main.go
	Key c: {Steve}
	Key d: {}

### Provera prisutnosti ključa 

Kada preuzmete vrednost dodeljenu datom ključu, vraća se i dodatna bulova vrednost. Bulova promenljiva će biti `true` ako ključ postoji, a `false` u suprotnom.

Hajde da ovo pokušamo na jednom primeru:
```
...
c, ok := m["c"]
fmt.Println("Key c:", c, ok)

d, ok := m["d"]
fmt.Println("Key d:", d, ok)
```
	$ go run main.go
	Key c: {Steve} Present: true
	Key d: {} Present: false

### Ažuriranje mape

Takođe možemo ažurirati vrednost ključa jednostavnim ponovnim dodeljivanjem ključa.
```
...
m["a"] = "Roger"
```
	$ go run main.go
	map[a:{Roger} b:{Seth} c:{Steve}]

### Brisanje iz mape

Ili, možemo obrisati ključ koristeći ugrađenu `delete` funkciju.

Evo kako izgleda sintaksa:

	delete(m, "a")

Prvi argument je mapa, a drugi je ključ koji želimo da obrišemo.

Funkcija `delete()` ne vraća nikakvu vrednost. Takođe, ne radi ništa ako ključ ne postoji u mapi.

	$ go run main.go
	map[a:{Roger} c:{Steve}]

### Iteracija mape

Slično nizovima ili isečcima, možemo iterirati kroz mape pomoću `range` ključne reči.
```
package main

import "fmt"

func main() {
	var m = map[string]User{
		"a": {"Peter"},
		"b": {"Seth"},
	}

	m["c"] = User{"Steve"}

	for key, value := range m {
		fmt.Println("Key: %s, Value: %v", key, value)
	}
}
```
	$ go run main.go
	Key: c, Value: {Steve}
	Key: a, Value: {Peter}
	Key: b, Value: {Seth}

Imajte na umu da je mapa neuređena kolekcija i stoga nije garantovano da će redosled iteracije mape biti isti svaki put kada je iteriramo.

### Svojstava mapa

Na kraju, hajde da pričamo o svojstvima mape.

Mape su referentni tipovi, što znači da kada dodelimo mapu novoj promenljivoj, obe se odnose na istu osnovnu strukturu podataka.

Stoga će promene koje izvrši jedna promenljiva biti vidljive drugoj.
```
package main

import "fmt"

type User struct {
	Name string
}

func main() {
	var m1 = map[string]User{
		"a": {"Peter"},
		"b": {"Seth"},
	}

	m2 := m1
	m2["c"] = User{"Steve"}

	fmt.Println(m1) 
	fmt.Println(m2) 
}
```
	map[a:{Peter} b:{Seth} c:{Steve}]
	map[a:{Peter} b:{Seth} c:{Steve}]

# Interfejsi

Dakle, interfejs u ​​Gou je apstraktni tip koji je definisan pomoću skupa potpisa metoda. Interfejs definiše ponašanje za slične tipove objekata.

Ovde je ponašanje ključni pojam o kome ćemo uskoro razgovarati.

Jedan od najboljih primera interfejsa iz stvarnog sveta je utičnica. Zamislite da treba da povežemo različite uređaje na utičnicu (u zidu).

### Bez interfejsa

Hajde da pokušamo da ovo implementiramo. Evo tipova uređaja koje ćemo koristiti.
```
type mobile struct {
	brand string
}
type laptop struct {
	cpu string
}
type toaster struct {
	amount int
}
type kettle struct {
	quantity string
}
type socket struct{}
```
Sada, hajde da definišemo *Draw* metodu na tipu, recimo `mobile`. Ovde ćemo jednostavno ispisati svojstva tipa.
```
func (m mobile) Draw(power int) {
	fmt.Printf("%T -> brand: %s, power: %d", m, m.brand, power)
}
```
Odlično, sada ćemo definisati *Plug* metodu na `socket` tipu koja prihvata naš `mobile` tip kao argument.
```
func (socket) Plug(device mobile, power int) {
	device.Draw(power)
}
```
Hajde da pokušamo da "povežemo" ili "priključimo" tip `mobile` našem `socket` tipu u *main* funkciji.
```
package main

import "fmt"

func main() {
	m := mobile{"Apple"}

	s := socket{}
	s.Plug(m, 10)
}
```
I ako ovo pokrenemo, videćemo sledeće.

	$ go run main.go
	main.mobile -> brand: Apple, power: 10

Ovo je zanimljivo, ali recimo da sada želimo da povežemo naš `laptop` tip.
```
package main
import "fmt"

func main() {
	m := mobile{"Apple"}
	l := laptop{"Intel i9"}
	s := socket{}
	s.Plug(m, 10)
	s.Plug(l, 50) // Error: cannot use l as mobile value in argument
}
```
Kao što vidimo, ovo će izbaciti grešku.

Šta bi trebalo sada da uradimo? Definišemo drugi metod? Kao na primer PlugLaptop? Naravno, ali onda svaki put kada dodamo novi tip uređaja, moraćemo da dodamo i novu metodu tipu `socket`, a to nije idealno.

Tu `interface` dolazi do izražaja. U suštini, želimo da definišemo ugovor koji se u budućnosti mora sprovesti.

Možemo jednostavno definisati interfejs kao što je `PowerDrawer` i koristiti ga u našoj *Plug* funkciji da bismo dozvolili bilo koji uređaj koji zadovoljava kriterijume, a to je da tip mora imati Drawmetod koji odgovara potpisu koji interfejs zahteva.

I u svakom slučaju, `socket` ne mora ništa da zna o našem uređaju i može jednostavno da pozove *Draw* metodu.

### Sa interfejsom

Sada hajde da pokušamo da implementiramo naš `PowerDrawer` interfejs. Evo kako će izgledati.

Konvencija je da se u imenu koristi sufiks `"-er"` . I kao što smo ranije pomenuli, interfejs treba samo da opisuje očekivano ponašanje. Što je u našem slučaju *Draw* metoda.

##### Implementacija interfejsa
```
type PowerDrawer interface {
	Draw(power int)
}
```
Sada, moramo ažurirati našu *Plug* metodu da prihvati uređaj koji implementira `PowerDrawer` interfejs kao argument.
```
func (socket) Plug(device PowerDrawer, power int) {
	device.Draw(power)
}
```
A da bismo zadovoljili interfejs, možemo jednostavno dodati Draw metode svim tipovima uređaja.
```
type mobile struct {
	brand string
}
func (m mobile) Draw(power int) {
	fmt.Printf("%T -> brand: %s, power: %d\n", m, m.brand, power)
}
type laptop struct {
	cpu string
}
func (l laptop) Draw(power int) {
	fmt.Printf("%T -> cpu: %s, power: %d\n", l, l.cpu, power)
}
type toaster struct {
	amount int
}
func (t toaster) Draw(power int) {
	fmt.Printf("%T -> amount: %d, power: %d\n", t, t.amount, power)
}
type kettle struct {
	quantity string
}
func (k kettle) Draw(power int) {
	fmt.Printf("%T -> quantity: %s, power: %d\n", k, k.quantity, power)
}
```
Sada možemo povezati sve naše uređaje sa utičnicom pomoću našeg interfejsa!
```
func main() {
	m := mobile{"Apple"}
	l := laptop{"Intel i9"}
	t := toaster{4}
	k := kettle{"50%"}
	s := socket{}
	s.Plug(m, 10)
	s.Plug(l, 50)
	s.Plug(t, 30)
	s.Plug(k, 25)
}
```
I funkcioniše baš onako kako smo očekivali.

	$ go run main.go
	main.mobile -> brand: Apple, power: 10
	main.laptop -> cpu: Intel i9, power: 50
	main.toaster -> amount: 4, power: 30
	main.kettle -> quantity: Half Empty, power: 25

Ali zašto se ovo smatra tako moćnim konceptom?

Pa, interfejs nam može pomoći da razdvojimo naše tipove. Na primer, pošto imamo interfejs, ne moramo da ažuriramo našu `socket` implementaciju. Možemo jednostavno definisati novi tip uređaja pomoću *Draw* metode.

Za razliku od drugih jezika, Go interfejsi su implicitno implementirani, tako da nam nije potrebno nešto poput `implements` ključne reči. To znači da tip automatski zadovoljava interfejs kada ima "sve metode" interfejsa.

### Prazan interfejs

Prazan interfejs može da poprimi vrednost bilo kog tipa.

Evo kako to deklarišemo.

	var x interface{}

Ali zašto nam je to potrebno?

Prazni interfejsi se mogu koristiti za rukovanje vrednostima nepoznatih tipova.

Neki primeri su:

- Čitanje heterogenih podataka iz API-ja.
- Promenljive nepoznatog tipa, kao u `fmt.Println` funkciji.

Da bismo koristili vrednost tipa interface{}, možemo koristiti tvrdnju tipa ili prekidač tipa da bismo odredili tip vrednosti.

### Tvrdnja tipa

Tvrdnja tipa pruža pristup osnovnoj konkretnoj vrednosti vrednosti interfejsa.

Na primer:
```
func main() {
	var i interface{} = "hello"
	
	s := i.(string)		// <<=== tvrdnja tipa
	fmt.Println(s)
}
```
Ova izjava tvrdi da vrednost interfejsa sadrži konkretan tip i dodeljuje osnovnu vrednost tipa promenljivoj.

Takođe možemo testirati da li vrednost interfejsa sadrži određeni tip.

Tvrdnja tipa može vratiti dve vrednosti:

- Prva je osnovna vrednost.
- Druga je bulova vrednost koja izveštava da li je tvrdnja uspešna.
```
s, ok := i.(string) 	// << ==== tvrdnja tiša u onliku zarez, ok 
fmt.Println(s, ok)
```
Ovo nam može pomoći da testiramo da li vrednost interfejsa sadrži određeni tip ili ne. Na neki način, ovo je slično načinu na koji čitamo vrednosti sa mape.

A ako je `ok` jednako `false` i vrednost će biti nula vrednost tipa, i neće doći do panike.
```
f, ok := i.(float64)
fmt.Println(f, ok)
```
Ali ako interfejs ne sadrži tip, izjava će izazvati paniku.
```
f = i.(float64)
fmt.Println(f) // Panic!
```
	$ go run main.go
	hello
	hello true
	0 false
	panic: interface conversion: interface {} is string, not float64

### Prekidač tipa

switch se može koristiti kao iskaz za određivanje tipa promenljive tipa interface{}.
```
var t interface{}
t = "hello"

switch t := t.(type) {
case string:
	fmt.Printf("string: %s\n", t)
case bool:
	fmt.Printf("boolean: %v\n", t)
case int:
	fmt.Printf("integer: %d\n", t)
default:
	fmt.Printf("unexpected: %T\n", t)
}
```
I ako ovo pokrenemo, možemo proveriti da imamo string tip.

	$ go run main.go
	string: hello

### Svojstva interfejsa

##### Nulta vrednost

Nulta vrednost interfejsa je `nil`.
```
package main
import "fmt"

type MyInterface interface {
	Method()
}
func main() {
	var i MyInterface

	fmt.Println(i) // Output: <nil>
}
```

##### Ugrađivanje

Možemo ugrađivati interfejse poput struktura. Na primer:
```
type interface1 interface {
    Method1()
}
type interface2 interface {
    Method2()
}
type interface3 interface {
    interface1
    interface2
}
```
##### Poređenje interfejsa

Vrednosti interfejsa su uporedive.
```
package main
import "fmt"

type MyInterface interface {
	Method()
}
type MyType struct{}
func (MyType) Method() {}

func main() {
	t := MyType{}
	var i MyInterface = MyType{}
	fmt.Println(t == i)
}
```
##### Vrednosti interfejsa

U suštini, vrednost interfejsa se može smatrati torkom koja se sastoji od vrednosti i konkretnog tipa.
```
package main
import "fmt"

type MyInterface interface {
	Method()
}
type MyType struct {
	property int
}

func (MyType) Method() {}

func main() {
	var i MyInterface
	i = MyType{10}
	fmt.Printf("(%v, %T)\n", i, i) 	// Output: ({10}, main.MyType)
}
```
Time smo pokrili interfejse u Go-u.

To je zaista moćna funkcija, ali zapamtite, "Što je interfejs veći, to je apstrakcija slabija" - Rob Pajk.

# Greške

Primetite kako sam rekao greške, a ne izuzetci, jer u Go-u nema obrade izuzetaka. Umesto toga, možemo jednostavno vratiti ugrađeni `error` tip koji je tip interfejsa.
```
type error interface {
    Error() string
}
```
Uskoro ćemo se vratiti na ovo. Prvo, pokušajmo da razumemo osnove. 

Dakle, deklarišimo jednostavnu *Divide* funkciju koja, kao što ime sugeriše, deli ceo broj *a* sa *b*.
```
func Divide(a, b int) int {
	return a/b
}
```
Sada želimo da vratimo grešku, recimo, da sprečimo deljenje nulom. To nas dovodi do konstrukcije greške.

### Konstrukcija grešaka

Postoji više načina da se to uradi, ali ćemo pogledati dva najčešća.

##### errors paket

Prvi je korišćenjem `New` funkcije koju pruža `errors` paket.
```
package main
import "errors"

func main() {}

func Divide(a, b int) (int, error) {
	if b == 0 {
		return 0, errors.New("cannot divide by zero")
	}
	return a/b, nil
}
```
Obratite pažnju kako vraćamo `error` sa rezultatom. A ako nema greške, jednostavno vraćamo ` nil` jer je to `nulta vrednost` greške, jer je na kraju krajeva, to interfejs.

Ali kako da to rešimo? Dakle, za to ćemo pozvati `Divide` funkciju u našoj `main` funkciji.
```
package main
import (
	"errors"
	"fmt"
)

func main() {
	result, err := Divide(4, 0)
	if err != nil {
		fmt.Println(err)
		// Do something with the error
		return
	}
	// Use the result
	fmt.Println(result)
}

func Divide(a, b int) (int, error) {...}
```
	$ go run main.go
	cannot divide by zero

Kao što vidite, jednostavno proveravamo da li je greška `nil` i u skladu sa tim gradimo našu logiku. Ovo se smatra prilično idiomatskim u Go jeziku i videćete da se često koristi.

##### fmt.Errorf funkcija

Drugi način da konstruišemo naše greške je korišćenje `fmt.Errorf` funkcije.

Ova funkcija je slična `fmt.Sprintf` i omogućava nam da formatiramo grešku. Ali umesto vraćanja stringa, vraća grešku.

Često se koristi da doda kontekst ili detalj našim greškama.
```
func Divide(a, b int) (int, error) {
	if b == 0 {
		return 0, fmt.Errorf("cannot divide %d by zero", a)
	}
	return a/b, nil
}
```
I trebalo bi da funkcioniše slično.

	$ go run main.go
	cannot divide 4 by zero

##### Očekivane greške

Još jedna važna tehnika u Gou je definisanje očekivanih grešaka kako bi se one mogle eksplicitno proveriti u drugim delovima koda. One se ponekad nazivaju `sentinel` greškama.
```
package main
import (
	"errors"
	"fmt"
)

var ErrDivideByZero = errors.New("cannot divide by zero")

func main() {...}

func Divide(a, b int) (int, error) {
	if b == 0 {
		return 0, ErrDivideByZero
	}
	return a/b, nil
}
```
U jeziku Go, smatra se konvencionalnim da se ispred promenljive stavlja prefiks `Err`. Na primer, `ErrNotFound`.

Ali koja je poenta?  Dakle, ovo postaje korisno kada treba da izvršimo drugu granu koda ako se naiđe na određenu vrstu greške.

Na primer, sada možemo eksplicitno proveriti koja se greška dogodila korišćenjem `errors.Is` funkcije.
```
package main
import (
	"errors"
	"fmt"
)

func main() {
	result, err := Divide(4, 0)
	if err != nil {
		switch {
		case errors.Is(err, ErrDivideByZero):
			fmt.Println(err)
			// Do something with the error
		default:
			fmt.Println("no idea!")
		}
		return
	}
	fmt.Println(result)	// Use the result
}

func Divide(a, b int) (int, error) {...}
```
	$ go run main.go
	cannot divide by zero

##### Prilagođene greške

Ova strategija pokriva većinu slučajeva upotrebe za obradu grešaka. Ali ponekad su nam potrebne dodatne funkcionalnosti kao što su dinamičke vrednosti unutar naših grešaka.

Ranije smo videli da je error samo interfejs. Dakle, u osnovi, bilo šta može biti `error` sve dok implementira `Error()` metodu koja vraća poruku o grešci kao string.

Dakle, hajde da definišemo našu prilagođenu `DivisionError` strukturu koja će sadržati kod greške i poruku.
```
package main
import (
	"errors"
	"fmt"
)
type DivisionError struct {
	Code int
	Msg  string
}
func (d DivisionError) Error() string {
	return fmt.Sprintf("code %d: %s", d.Code, d.Msg)
}
func main() {...}

func Divide(a, b int) (int, error) {
	if b == 0 {
		return 0, DivisionError{
			Code: 2000,
			Msg:  "cannot divide by zero",
		}
	}
	return a/b, nil
}
```
Ovde ćemo koristiti `errors.As` umesto `errors.Is` funkcije da bismo konvertovali grešku u ispravan tip.
```
func main() {
	result, err := Divide(4, 0)
	if err != nil {
		var divErr DivisionError
		switch {
		case errors.As(err, &divErr):
			fmt.Println(divErr)
			// Do something with the error
		default:
			fmt.Println("no idea!")
		}
		return
	}
	fmt.Println(result)	// Use the result
}
func Divide(a, b int) (int, error) {...}
```
	$ go run main.go
	code 2000: cannot divide by zero

Ali koja je razlika između funkcija `errors.Is` i `errors.As`?

Razlika je u tome što ova `As` funkcija proverava da li greška ima određeni tip, za razliku od `Is` funkcije koja ispituje da li je u pitanju određeni objekat greške.

Takođe možemo koristiti tvrdnju tipa, ali to nije poželjno.
```
func main() {
	result, err := Divide(4, 0)
	if e, ok := err.(DivisionError); ok {
		fmt.Println(e.Code, e.Msg) // Output: 2000 cannot divide by zero
		return
	}
	fmt.Println(result)
}
```
Na kraju, reći ću da je obrada grešaka u Gou prilično drugačija u poređenju sa tradicionalnim `try/catch` idiomom u drugim jezicima. Ali je veoma moćna jer podstiče programera da zapravo obradi grešku na eksplicitan način, što takođe poboljšava čitljivost.

# Panic i recover

Dakle, ranije smo saznali da je idiomatski način rešavanja abnormalnih uslova u Go programu korišćenje grešaka. Iako su greške dovoljne za većinu slučajeva, postoje neke situacije u kojima program ne može da nastavi sa radom.

U tim slučajevima možemo koristiti ugrađenu `panic` funkciju.

### Panic funkcija

	func panic(interface{})

`Panic` je ugrađena funkcija koja zaustavlja normalno izvršavanje trenutne goroutine. Kada funkcija pozove panic, normalno izvršavanje funkcije se odmah zaustavlja i kontrola se vraća pozivaocu. Ovo se ponavlja dok se program ne završi sa porukom panike i tragom steka.

**Napomena**: O *goroutine* ćemo razgovarati skasnije u kursu.

Dakle, da vidimo kako možemo da koristimo panic funkciju.
```
package main

func main() {
	WillPanic()
}
func WillPanic() {
	panic("Woah")
}
```
I ako ovo pokrenemo, možemo videti `panic` u akciji.

	$ go run main.go
	panic: Woah

goroutine 1 [running]:
```
main.WillPanic(...)
    .../main.go:8
main.main()
    .../main.go:4 +0x38
exit status 2
```
Kao što se i očekivalo, naš program je ispisao poruku panike, nakon čega je usledio trag steka, a zatim je prekinut.

Dakle, pitanje je šta učiniti kada se dogodi neočekivana panika?

### Recover funkcija

Moguće je povratiti kontrolu nad programom koji izaziva paniku koristeći ugrađenu `recover` funkciju, zajedno sa `defer` ključnom reči.

	func recover() interface{}

Hajde da pokušamo primer kreiranjem `handlePanic` funkcije. A zatim je možemo pozvati koristeći defer.
```
package main
import "fmt"

func main() {
	WillPanic()
}
func handlePanic() {
	data := recover()
	fmt.Println("Recovered:", data)
}
func WillPanic() {
	defer handlePanic()
	panic("Woah")
}
```
	$ go run main.go
	Recovered: Woah

Kao što vidimo, naša panika je oporavljena i sada naš program može da nastavi sa izvršavanjem.

Na kraju, pomenuću da se `panic` i `recover` mogu smatrati sličnim `try/catch` idiomu u drugim jezicima. Ali jedan važan faktor je da treba da izbegavamo paniku i da se oporavljamo i koristimo greške kad god je to moguće.

Ako je tako, onda nas to dovodi do pitanja, kada bi trebalo da koristimo panic?

### Slučajevi upotrebe panic funkcije

Postoje dva validna slučaja upotrebe za panic:

##### Nepopravljiva greška

Što može biti situacija u kojoj program jednostavno ne može da nastavi svoje izvršavanje.

Na primer, čitanje konfiguracione datoteke što je važno za pokretanje programa, jer nema šta drugo da se uradi ako samo čitanje datoteke ne uspe.

##### Greška programera

Ovo je najčešća situacija. Na primer, dereferenciranje pointera kada je vrednost `nil` izazvalo bi paniku.

# Testiranje

U ovom tutorijalu ćemo govoriti o testiranju u Go-u. Dakle, hajde da počnemo sa jednostavnim primerom. Napravili smo `math` paket koji sadrži `Add` funkciju koja, kao što i samo ime sugeriše, sabira dva cela broja.
```
package math
func Add(a, b int) int {
	return a + b
}
```
Koristi se u našem `main` paketu ovako:
```
package main
import (
	"example/math"
	"fmt"
)
func main() {
	result := math.Add(2, 2)
	fmt.Println(result)
}
```
I, ako ovo pokrenemo, trebalo bi da vidimo rezultat.

	$ go run main.go
	4

Sada želimo da testiramo našu `Add` funkciju. Dakle, u programskom jeziku Go deklarišemo test datoteke sa `_test` sufiksom u nazivu datoteke. Dakle, za naš `add.go`, kreiraćemo test kao `add_test.go`. Struktura našeg projekta bi trebalo da izgleda ovako:

├── go.mod<br>
├── main.go<br>
└── math<br>
....├── add.go<br>
....└── add_test.go

Počećemo korišćenjem `math_test` paketa i njegovim uvozom `testing` iz standardne biblioteke. Testiranje je ugrađeno u Go, za razliku od mnogih drugih jezika.

Ali čekajte... zašto moramo da koristimo `math_test` kao naš paket, zar ne možemo jednostavno da koristimo isti `math` paket?

Pa da, možemo napisati naš test u istom paketu ako želimo, ali lično mislim da nam rad u odvojenom paketu pomaže da pišemo testove na odvojeniji način.

Sada možemo da kreiramo našu `TestAdd`funkciju. Ona će uzimati argument tipa `testing.T` koji će nam pružiti korisne metode.
```
package math_test
import "testing"

func TestAdd(t *testing.T) {}
```
Pre nego što dodamo bilo kakvu logiku za testiranje, pokušaćemo da je pokrenemo. Ali ovog puta, ne možemo koristiti `go run` komandu, umesto toga ćemo koristiti `go test` komandu.

	$ go test ./math
	ok      example/math 0.429s

Ovde ćemo imati ime našeg paketa koje je `math`, ali možemo koristiti i relativnu putanju ./.. za testiranje svih paketa.

	$ go test ./..
	?       example [no test files]
	ok      example/math 0.348s

A ako Go ne pronađe nijedan test u paketu, obavestiće nas.

Odlično, hajde da napišemo test kod. Da bismo to uradili, proverićemo naš rezultat sa očekivanom vrednošću i ako se ne poklapaju, možemo koristiti `t.Fail` metodu da ne prođemo test.
```
package math_test
import "testing"

func TestAdd(t *testing.T) {
	got := math.Add(1, 1)
	expected := 2
	if got != expected {
		t.Fail()
	}
}
```
Odlično! Izgleda da je naš test prošao.

	$ go test math
	ok      example/math    0.412s

Da vidimo i šta se dešava ako ne prođemo test, za to možemo jednostavno promeniti očekivani rezultat.
```
package math_test
import "testing"

func TestAdd(t *testing.T) {
	got := math.Add(1, 1)
	expected := 3
	if got != expected {
		t.Fail()
	}
}
```
	$ go test ./math
	ok      example/math    (cached)

Ako ovo vidite, ne brinite. Radi optimizacije, naši testovi su keširani. Možemo koristiti `go clean` komandu da obrišemo keš memoriju, a zatim ponovo pokrenemo test.

	$ go clean -testcache
	$ go test ./math
	--- FAIL: TestAdd (0.00s)
	FAIL
	FAIL    example/math    0.354s
	FAIL

Dakle, ovako će izgledati neuspeh na testu.

### Testovi vođeni tabelama

Ovo nas dovodi do testova vođenih tabelama. Ali šta su oni tačno?

Dakle, ranije smo imali argumente funkcija i očekivane promenljive koje smo upoređivali da bismo utvrdili da li su naši testovi prošli ili ne. Ali šta ako sve to definišemo u jednom isečku i ponovimo ga? Ovo će učiniti naše testove malo fleksibilnijim i pomoći nam da lakše pokrenemo više slučajeva.

Ne brinite, naučićemo ovo na primeru. Zato ćemo početi definisanjem naše `addTestCase` strukture.
```
package math_test
import (
	"example/math"
	"testing"
)
type addTestCase struct {
	a, b, expected int
}
var testCases = []addTestCase{
	{1, 1, 3},
	{25, 25, 50},
	{2, 1, 3},
	{1, 10, 11},
}
func TestAdd(t *testing.T) {
	for _, tc := range testCases {
		got := math.Add(tc.a, tc.b)
		if got != tc.expected {
			t.Errorf("Expected %d but got %d", tc.expected, got)
		}
	}
}
```
Obratite pažnju kako smo deklarisali `addTestCase` malim slovom. Tačno, ne želimo da ga eksportujemo jer nije korisno van naše logike testiranja. Hajde da pokrenemo naš test.

	$ go run main.go
	--- FAIL: TestAdd (0.00s)
	    add_test.go:25: Expected 3 but got 2
	FAIL
	FAIL    example/math    0.334s
	FAIL

Izgleda da su nam testovi otkazali, hajde da ih popravimo ažuriranjem naših test slučajeva.
```
var testCases = []addTestCase{
	{1, 1, 2},
	{25, 25, 50},
	{2, 1, 3},
	{1, 10, 11},
}
```
Odlično, radi!

	$ go run main.go
	ok      example/math    0.589s

### Pokrivenost koda

Na kraju, hajde da pričamo o pokrivenosti koda. Prilikom pisanja testova, često je važno znati koliki deo vašeg stvarnog koda testovi pokrivaju. Ovo se generalno naziva pokrivenošću koda.

Da bismo izračunali i izvezli pokrivenost za naš test, možemo jednostavno koristiti `-coverprofile` argument sa `go test` komandom.

	$ go test ./math -coverprofile=coverage.out
	ok      example/math    0.385s  coverage: 100.0% of statements

Izgleda da imamo odličnu pokrivenost. Hajde da proverimo i izveštaj koristeći `go tool cover` komandu koja nam daje detaljan izveštaj.

	$ go tool cover -html=coverage.out

Kao što vidimo, ovo je mnogo čitljiviji format. A najbolje od svega je što je ugrađen direktno u standardne alate.

### Testiranje nejasnoća

Na kraju, pogledajmo `fuzzing testiranje` koje je predstavljeno u Go verziji 1.18.

Fazing je vrsta automatizovanog testiranja koja kontinuirano manipuliše ulazima u program kako bi pronašla greške.

Go fuzzing koristi smernice za pokrivanje kako bi inteligentno prošao kroz kod koji se fazira kako bi pronašao i prijavio greške korisniku.

Pošto može doći do graničnih slučajeva koje ljudi često propuste, `fuzzing` testiranje može biti posebno vredno za pronalaženje grešaka i bezbednosnih propusta.

Hajde da pokušamo sa primerom:
```
func FuzzTestAdd(f *testing.F) {
	f.Fuzz(func(t *testing.T, a, b int) {
		math.Add(a , b)
	})
}
```
Ako ovo pokrenemo, videćemo da će se automatski kreirati test slučajevi. Pošto je `Add` funkcija prilično jednostavna, testovi će proći.

	$ go test -fuzz FuzzTestAdd example/math
	fuzz: elapsed: 0s, gathering baseline coverage: 0/192 completed
	fuzz: elapsed: 0s, gathering baseline coverage: 192/192 completed, now fuzzing with 8 workers
	fuzz: elapsed: 3s, execs: 325017 (108336/sec), new interesting: 11 (total: 202)
	fuzz: elapsed: 6s, execs: 680218 (118402/sec), new interesting: 12 (total: 203)
	fuzz: elapsed: 9s, execs: 1039901 (119895/sec), new interesting: 19 (total: 210)
	fuzz: elapsed: 12s, execs: 1386684 (115594/sec), new interesting: 21 (total: 212)
	PASS
	ok      foo 12.692s

Ali ako ažuriramo našu `Add` funkciju slučajnim graničnim slučajem tako da će program paničiti ako je b + 10 veće od a.
```
func Add(a, b int) int {
	if a > b + 10 {
		panic("B must be greater than A")
	}
	return a + b
}
```
A ako ponovo pokrenemo test, ovaj granični slučaj će biti uhvaćen `fuzz` testiranjem.

	$ go test -fuzz FuzzTestAdd example/math
	warning: starting with empty corpus
	fuzz: elapsed: 0s, execs: 0 (0/sec), new interesting: 0 (total: 0)
	fuzz: elapsed: 0s, execs: 1 (25/sec), new interesting: 0 (total: 0)
	--- FAIL: FuzzTestAdd (0.04s)
	    --- FAIL: FuzzTestAdd (0.00s)
	        testing.go:1349: panic: B must be greater than A

Mislim da je ovo zaista sjajna karakteristika Go 1.18. Više o `fuzz` testiranju možete saznati sa zvaničnog Go bloga.

### Generici

U ovom odeljku ćemo saznati o generičkim funkcijama, dugo očekivanoj funkciji koja je objavljena sa verzijom 1.18 jezika Go.

Generici znače parametrizovane tipove. Jednostavno rečeno, generici omogućavaju programerima da pišu kod gde se tip može navesti kasnije jer tip nije odmah relevantan.

Hajde da pogledamo jedan primer da bismo ovo bolje razumeli.

Za naš primer, imamo jednostavne funkcije sumiranja za različite tipove kao što su `int`, `float64` i `string`. Pošto `overload` metoda nije dozvoljeno u Go-u, obično moramo da kreiramo nove funkcije.
```
package main
import "fmt"

func sumInt(a, b int) int {
	return a + b
}
func sumFloat(a, b float64) float64 {
	return a + b
}
func sumString(a, b string) string {
	return a + b
}
func main() {
	fmt.Println(sumInt(1, 2))
	fmt.Println(sumFloat(4.0, 2.0))
	fmt.Println(sumString("a", "b"))
}
```
Kao što vidimo, osim tipova, ove funkcije su prilično slične.

Da vidimo kako možemo definisati generičku funkciju.
```
func fnName[T constraint]() {
	...
}
```
Ovde je `T` naš parametar tipa i `constraint` biće interfejs koji dozvoljava bilo kom tipu da implementira taj interfejs. Ovo je zbunjujuće. Dakle, hajde da počnemo da gradimo našu generičku `sum` funkciju.

Ovde ćemo koristiti `T` kao parametar tipa sa praznim interfejsom `interface{}` kao ograničenjem.
```
func sum[T interface{}](a, b T) T {
	fmt.Println(a, b)
}
```
Takođe, počevši od Go 1.18 možemo koristiti `any`, što je manje-više ekvivalentno praznom interfejsu.
```
func sum[T any](a, b T) T {
	fmt.Println(a, b)
}
```
Sa parametrima tipa dolazi do potrebe za prosleđivanjem argumenata tipa, što može učiniti naš kod opširnim.
```
sum[int](1, 2) // explicit type argument
sum[float64](4.0, 2.0)
sum[string]("a", "b")
```
Srećom, Go 1.18 dolazi sa zaključivanjem tipova što nam pomaže da pišemo kod koji poziva generičke funkcije bez eksplicitnih tipova.
```
sum(1, 2)
sum(4.0, 2.0)
sum("a", "b")
```
Hajde da ovo pokrenemo i vidimo da li radi.

	$ go run main.go
	1 2
	4 2
	a b

Sada, hajde da ažuriramo sum funkciju da bismo dodali naše promenljive.
```
func sum[T any](a, b T) T {
	return a + b
}

fmt.Println(sum(1, 2))
fmt.Println(sum(4.0, 2.0))
fmt.Println(sum("a", "b"))
```
Ali sada ako ovo pokrenemo, dobićemo grešku da operator `+` nije definisan u ograničenju.

	$ go run main.go
	./main.go:6:9: invalid operation: operator + not defined on a (variable of type T constrained by any)

Iako ograničenje tipa `any` generalno funkcioniše, ono ne podržava operatore.

Dakle, hajde da definišemo sopstveno prilagođeno ograničenje koristeći interfejs. Naš interfejs treba da definiše skup tipova koji sadrži `int`, `float` i `string`.

слагање

Evo kako izgleda naš `SumConstraint` interfejs.
```
type SumConstraint interface {
	int | float64 | string
}
func sum[T SumConstraint](a, b T) T {
	return a + b
}
func main() {
	fmt.Println(sum(1, 2))
	fmt.Println(sum(4.0, 2.0))
	fmt.Println(sum("a", "b"))
}
```
I ovo bi trebalo da funkcioniše kako se očekuje.

	$ go run main.go
	3
	6
	ab

Takođe možemo koristiti `constraints` paket koji definiše skup korisnih ograničenja koja se koriste sa parametrima tipa.
```
type Signed interface {
	~int | ~int8 | ~int16 | ~int32 | ~int64
}
type Unsigned interface {
	~uint | ~uint8 | ~uint16 | ~uint32 | ~uint64 | ~uintptr
}
type Integer interface {
	Signed | Unsigned
}
type Float interface {
	~float32 | ~float64
}
type Complex interface {
	~complex64 | ~complex128
}
type Ordered interface {
	Integer | Float | ~string
}
```
Za to ćemo morati da instaliramo `constraints` paket.

	$ go get golang.org/x/exp/constraints
	go: added golang.org/x/exp v0.0.0-20220414153411-bcd21879b8fd
```
import (
	"fmt"
	"golang.org/x/exp/constraints"
)
func sum[T constraints.Ordered](a, b T) T {
	return a + b
}
func main() {
	fmt.Println(sum(1, 2))
	fmt.Println(sum(4.0, 2.0))
	fmt.Println(sum("a", "b"))
}
```
Ovde koristimo `Ordered` ograničenje.
```
type Ordered interface {
	Integer | Float | ~string
}
```
`~` je novi token dodat u Go, a izraz `~string` označava skup svih tipova čiji je osnovni tip string.

I dalje radi kako se očekuje.

	$ go run main.go
	3
	6
	ab

Generici su neverovatna karakteristika jer omogućavaju pisanje apstraktnih funkcija koje mogu drastično smanjiti dupliranje koda u određenim slučajevima.

### Kada koristiti generike

Dakle, kada koristiti generike? Možemo uzeti sledeće slučajeve upotrebe kao primer:

- Funkcije koje rade na nizovima, isečcima, mapama i kanalima.
- Strukture podataka opšte namene kao što su stek ili povezana lista.
- Da bi se smanjilo dupliranje koda.

Na kraju, dodaću da iako su generički izrazi odličan dodatak jeziku, treba ih koristiti štedljivo.

I, savetuje se da počnete sa jednostavnim i da pišete generički kod tek kada smo napisali veoma sličan kod najmanje 2 ili 3 puta.

# Konkurencija

U ovoj lekciji ćemo naučiti o konkurentnosti, što je jedna od najmoćnijih karakteristika Go jezika.

Dakle, hajde da počnemo sa pitanjem Šta je "konkurentnost" ?
Šta je konkurentnost

Konkurentnost, po definiciji, je sposobnost razlaganja računarskog programa ili algoritma na pojedinačne delove, koji se mogu izvršavati nezavisno.

Konačni ishod konkurentnog programa je isti kao i kod programa koji je izvršan sekvencijalno.

Koristeći konkurentnost, možemo postići iste rezultate za manje vremena, čime se povećavaju ukupne performanse i efikasnost naših programa.
Konkurencija naspram paralelizma

конкурентност-на-паралелизам

Mnogi ljudi mešaju konkurentnost sa paralelizmom jer oba donekle podrazumevaju istovremeno izvršavanje koda, ali to su dva potpuno različita koncepta.

Konkurencija je zadatak istovremenog pokretanja i upravljanja višestrukim izračunavanjima, dok je paralelizam zadatak istovremenog pokretanja višestrukih izračunavanja.

Jednostavan citat Roba Pajka prilično sumira sve.

"Konkurentnost je rad sa mnogo stvari odjednom. Paralelizam je rad sa mnogo stvari odjednom."

Ali konkurentnost u Gou je više od same sintakse. Da bismo iskoristili moć Goa, prvo moramo da razumemo kako Go pristupa konkurentnom izvršavanju koda. Go se oslanja na model konkurentnosti koji se zove CSP (Communicating Sequential Processes - komunikacija sekvencijalnih procesa).
Komunikacija sekvencijalnih procesa (CSP)

Komunikacija sekvencijalnih procesa (CSP) je model koji je predstavio Toni Hoar 1978. godine, a koji opisuje interakcije između konkurentnih procesa. Napravio je proboj u računarstvu, posebno u oblasti konkurentnosti.

Jezici poput Go i Erlang su bili veoma inspirisani konceptom komunikacije sekvencijalnih procesa (CSP).

Konkurencija je teška, ali CSP nam omogućava da damo bolju strukturu našem konkurentnom kodu i pruža model za razmišljanje o konkurentnosti na način koji to čini malo lakšim. Ovde su procesi nezavisni i komuniciraju deljenjem kanala između njih.

csp

Kasnije u kursu ćemo naučiti kako Golang to implementira koristeći gorutine i kanale.
Osnovni koncepti

Sada, hajde da se upoznamo sa nekim osnovnim konceptima konkurentnosti.
Trka podataka

Trka podataka nastaje kada procesi moraju istovremeno da pristupe istom resursu.

Na primer, jedan proces čita dok drugi istovremeno piše u potpuno isti resurs.
Uslovi trke

Do trke dolazi kada vreme ili redosled događaja utiče na ispravnost dela koda.
Zastoji

Zastoj se javlja kada su svi procesi blokirani dok čekaju jedan drugog i program ne može dalje da se izvršava.

Kofmanovi uslovi

Postoje četiri uslova, poznata kao Kofmanovi uslovi, i svi oni moraju biti zadovoljeni da bi došlo do zastoja.

Uzajamno isključenje

Kontinuirani proces drži barem jedan resurs u bilo kom trenutku, što ga čini nedeljivim.

Na dijagramu ispod, postoji jedna instanca Resursa 1 i nju drži samo Proces 1.

међусобно искључивање

Čekaj i sačekaj

Kontinuirani proces drži resurs i čeka na dodatni resurs.

Na dijagramu datom ispod, Proces 2 drži Resurs 2 i Resurs 3 i zahteva Resurs 1 koji drži Proces 1.

чекати

Bez prevencije

Resurs koji drži konkurentni proces ne može biti oduzet od strane sistema. Može ga osloboditi samo proces koji ga drži.

Na dijagramu ispod, Proces 2 ne može da preuzme Resurs 1 iz Procesa 1. On će biti oslobođen samo kada ga Proces 1 dobrovoljno prepusti nakon što je njegovo izvršavanje završeno.

без превенције

Kružno čekanje

Proces čeka resurs koji drži drugi proces, koji čeka resurs koji drži treći proces, i tako dalje, sve dok poslednji proces ne čeka resurs koji drži prvi proces. Dakle, formira se kružni lanac.

Na dijagramu ispod, Procesu 1 je dodeljen Resurs2 i on zahteva Resurs 1. Slično tome, Procesu 2 je dodeljen Resurs 1 i on zahteva Resurs 2. Ovo formira kružnu petlju čekanja.

кружно чекање

Žive brave

Lajvlok procesi su procesi koji aktivno izvršavaju istovremene operacije, ali ove operacije ne čine ništa da pomeraju stanje programa napred.
Gladovanje

Do gladovanja dolazi kada je proces lišen neophodnih resursa i nije u stanju da završi svoju funkciju.

Gladovanje može se desiti zbog zastoja ili neefikasnih algoritama za zakazivanje procesa. Da bismo rešili problem gladovanja, moramo da primenimo bolje algoritme za raspodelu resursa koji osiguravaju da svaki proces dobije svoj pravedan deo resursa.
Gorutine

U ovoj lekciji ćemo učiti o Gorutinama.

Ali pre nego što započnemo našu diskusiju, želeo bih da podelim jednu važnu poslovicu o Gou.

"Ne komuniciraj deljenjem sećanja, delite sećanje komunikacijom." - Rob Pajk
Šta je gorutina?

Gorutina je lagana nit izvršavanja kojom upravlja Go runtime i u suštini nam omogućava da pišemo asinhroni kod na sinhroni način.

Važno je znati da to nisu stvarne OS niti i da se sama glavna funkcija izvršava kao gorutina.

Jedna nit može da pokreće hiljade gorutina koristeći Go raspoređivač vremena izvršavanja koji koristi kooperativno zakazivanje. To podrazumeva da ako je trenutna gorutina blokirana ili je završena, raspoređivač će premestiti ostale gorutine u drugu nit operativnog sistema. Stoga postižemo efikasnost u zakazivanju gde nijedna rutina nije blokirana zauvek.

Možemo pretvoriti bilo koju funkciju u gorutinu jednostavnim korišćenjem goključne reči.
```
go fn(x, y, z)
```
Pre nego što napišemo bilo koji kod, važno je ukratko razmotriti model fork-join-a.
Model račvastog spajanja

Go koristi ideju modela fork-join konkurentnosti koji stoji iza gorutina. Model fork-join u suštini podrazumeva da se podređeni proces odvaja od svog roditeljskog procesa da bi se pokrenuo istovremeno sa roditeljskim procesom. Nakon završetka izvršavanja, podređeni proces se ponovo spaja sa roditeljskim procesom. Tačka gde se ponovo spaja naziva se tačka spajanja .

форк-јоин

Sada, hajde da napišemo malo koda i kreiramo sopstvenu gorutinu.
```
package main
import "fmt"

func speak(arg string) {
	fmt.Println(arg)
}
func main() {
	go speak("Hello World")
}
```
Ovde speakpoziv funkcije ima prefiks goključne reči . Ovo će joj omogućiti da se pokreće kao zasebna gorutina. I to je to, upravo smo kreirali našu prvu gorutinu. Toliko je jednostavno!

Odlično, hajde da pokrenemo ovo:

	$ go run main.go

Zanimljivo je da izgleda da se naš program nije potpuno pokrenuo jer mu nedostaje deo izlaza. To je zato što je naša glavna gorutina izašla i nije čekala gorutinu koju smo kreirali.

Šta ako nateramo naš program da čeka koristeći time.Sleepfunkciju?
```
func main() {
	...
	time.Sleep(1 * time.Second)
}
```
	$ go run main.go
	Hello World

Eto, sada možemo videti naš kompletan rezultat.

U redu, ovo funkcioniše, ali nije idealno. Pa kako da ovo poboljšamo?

Pa, najzahtevniji deo korišćenja gorutina je znati kada će se zaustaviti. Važno je znati da se gorutine izvršavaju u istom adresnom prostoru, tako da pristup deljenoj memoriji mora biti sinhronizovan.

# Kanali

Jednostavno definisano, kanal je komunikaciona cev između gorutina. Stvari ulaze na jedan kraj, a izlaze na drugi istim redosledom dok se kanal ne zatvori.

Kanali u Go-u su zasnovani na komunikaciji sekvencijalnih procesa (CSP).

### Kreiranje kanala

Sada kada razumemo šta su kanali, hajde da vidimo kako ih možemo deklarisati.

	var ch chan T

Ovde ispred našeg tipa, Tkoji je tip podataka vrednosti koju želimo da pošaljemo i primimo, dodajemo ključnu reč chankoja predstavlja kanal.

Hajde da pokušamo da ispišemo vrednost našeg kanala ctipa string.

func main() {
	var ch chan string

	fmt.Println(c)
}

$ go run main.go
<nil>

Kao što vidimo, nulta vrednost kanala je nili ako pokušamo da pošaljemo podatke preko kanala, naš program će paničiti.

Dakle, slično kao kod isečki, možemo inicijalizovati naš kanal koristeći ugrađenu makefunkciju.

func main() {
	ch := make(chan string)

	fmt.Println(c)
}

I ako ovo pokrenemo, možemo videti da je naš kanal inicijalizovan.

$ go run main.go
0x1400010e060

Slanje i primanje podataka

Sada kada imamo osnovno razumevanje kanala, hajde da implementiramo naš prethodni primer koristeći kanale da bismo naučili kako ih možemo koristiti za komunikaciju između naših gorutina.

package main

import "fmt"

func speak(arg string, ch chan string) {
	ch <- arg // Send
}

func main() {
	ch := make(chan string)

	go speak("Hello World", ch)

	data := <-ch // Receive
	fmt.Println(data)
}

Obratite pažnju kako možemo slati podatke koristeći channel<-datai primati podatke koristeći data := <-channelsintaksu.

$ go run main.go
Hello World

Odlično, naš program je tekao kako smo očekivali.
Baferovani kanali

Takođe imamo baferovane kanale koji prihvataju ograničen broj vrednosti bez odgovarajućeg prijemnika za te vrednosti.

баферовани канал

Ova dužina ili kapacitet bafera može se odrediti korišćenjem drugog argumenta funkcije .make

func main() {
	ch := make(chan string, 2)

	go speak("Hello World", ch)
	go speak("Hi again", ch)

	data1 := <-ch
	fmt.Println(data1)

	data2 := <-ch
	fmt.Println(data2)
}

Pošto je ovaj kanal baferovan, možemo poslati ove vrednosti u kanal bez odgovarajućeg istovremenog prijema. To znači da šaljemo blok baferovanom kanalu samo kada je bafer pun i primamo blok kada je bafer prazan.

Podrazumevano, kanal je nebaferovan i ima kapacitet 0, stoga izostavljamo drugi argument funkcije make.

Zatim, imamo usmerene kanale.
Usmereni kanali

Kada koristimo kanale kao parametre funkcije, možemo da odredimo da li je kanal namenjen samo za slanje ili primanje vrednosti. Ovo povećava bezbednost tipa našeg programa jer podrazumevano kanal može i da šalje i da prima vrednosti.

усмерени канали

U našem primeru, možemo ažurirati speakdrugi argument naše funkcije tako da može poslati samo vrednost.

func speak(arg string, ch chan<- string) {
	ch <- arg // Send Only
}

Ovde chan<-se može koristiti samo za slanje vrednosti i doći će do panike ako pokušamo da primimo vrednosti.
Zatvaranje kanala

Takođe, baš kao i sa bilo kojim drugim resursom, kada završimo sa našim kanalom, potrebno ga je zatvoriti. To se može postići pomoću ugrađene closefunkcije.

Ovde možemo samo da prosledimo naš kanal funkciji close.

func main() {
	ch := make(chan string, 2)

	go speak("Hello World", ch)
	go speak("Hi again", ch)

	data1 := <-ch
	fmt.Println(data1)

	data2 := <-ch
	fmt.Println(data2)

	close(ch)
}

Opciono, prijemnici mogu da testiraju da li je kanal zatvoren dodeljivanjem drugog parametra izrazu za prijem.

func main() {
	ch := make(chan string, 2)

	go speak("Hello World", ch)
	go speak("Hi again", ch)

	data1 := <-ch
	fmt.Println(data1)

	data2, ok := <-ch
	fmt.Println(data2, ok)

	close(ch)
}

ako okjeste, falseonda nema više vrednosti za primanje i kanal je zatvoren.

Na neki način, ovo je slično načinu na koji proveravamo da li ključ postoji ili ne u mapi.
Nekretnine

Na kraju, hajde da razgovaramo o nekim svojstvima kanala:

    Slanje na nilkanal se blokira zauvek.

var c chan string
c <- "Hello, World!" // Panic: all goroutines are asleep - deadlock!

    Prijem sa nilkanala se blokira zauvek.

var c chan string
fmt.Println(<-c) // Panic: all goroutines are asleep - deadlock!

    Slanje na zatvoreni kanal izaziva paniku.

var c = make(chan string, 1)
c <- "Hello, World!"
close(c)
c <- "Hello, Panic!" // Panic: send on closed channel

    Prijem iz zatvorenog kanala odmah vraća nultu vrednost.

var c = make(chan int, 2)
c <- 5
c <- 4
close(c)
for i := 0; i < 4; i++ {
    fmt.Printf("%d ", <-c) // Output: 5 4 0 0
}

    Domet preko kanala.

Takođe možemo koristiti fori rangeza iteraciju kroz vrednosti primljene iz kanala.

package main

import "fmt"

func main() {
	ch := make(chan string, 2)

	ch <- "Hello"
	ch <- "World"

	close(ch)

	for data := range ch {
		fmt.Println(data)
	}
}

Izaberite

U ovom tutorijalu ćemo naučiti o selectizrazu u Go-u.

Izjava selectblokira kod i čeka na više operacija kanala istovremeno.

Blokira selectdok se jedan od njegovih slučajeva ne može pokrenuti, a zatim izvršava taj slučaj. Nasumično bira jedan ako je više njih spremno.

package main

import (
	"fmt"
	"time"
)

func main() {
	one := make(chan string)
	two := make(chan string)

	go func() {
		time.Sleep(time.Second * 2)
		one <- "One"
	}()

	go func() {
		time.Sleep(time.Second * 1)
		two <- "Two"
	}()

	select {
	case result := <-one:
		fmt.Println("Received:", result)
	case result := <-two:
		fmt.Println("Received:", result)
	}

	close(one)
	close(two)
}

Slično kao switch, selecttakođe ima podrazumevani slučaj koji se pokreće ako nijedan drugi slučaj nije spreman. Ovo će nam pomoći da šaljemo ili primamo bez blokiranja.

func main() {
	one := make(chan string)
	two := make(chan string)

	for x := 0; x < 10; x++ {
		go func() {
			time.Sleep(time.Second * 2)
			one <- "One"
		}()

		go func() {
			time.Sleep(time.Second * 1)
			two <- "Two"
		}()
	}

	for x := 0; x < 10; x++ {
		select {
		case result := <-one:
			fmt.Println("Received:", result)
		case result := <-two:
			fmt.Println("Received:", result)
		default:
			fmt.Println("Default...")
			time.Sleep(200 * time.Millisecond)
		}
	}

	close(one)
	close(two)
}

Takođe je važno znati da prazno select {}blokira zauvek.

func main() {
	...
	select {}

	close(one)
	close(two)
}

Sinhronizacija paketa

Kao što smo ranije saznali, gorutine se izvršavaju u istom adresnom prostoru, tako da pristup deljenoj memoriji mora biti sinhronizovan. syncPaket pruža korisne primitive.
Grupa čekanja

Grupa čeka da se završi izvršavanje kolekcije gorutina. Glavna gorutina poziva Addda bi podesila broj gorutina koje treba čekati. Zatim se svaka od gorutina pokreće i poziva Donekada se završi. Istovremeno, Waitmože se koristiti za blokiranje dok se sve gorutine ne završe.
Upotreba

Možemo koristiti sync.WaitGroupsledeće metode:

    Add(delta int)uzima celobrojnu vrednost koja je u suštini broj gorutina koje WaitGrouptreba da čeka. Ovo mora biti pozvano pre nego što izvršimo gorutinu.
    Done()se poziva unutar gorutine da signalizira da je gorutina uspešno izvršena.
    Wait()blokira program dok se sve gorutine koje je odredio Add()ne pozovu Done()iznutra.

Primer

Hajde da pogledamo jedan primer.

package main

import (
	"fmt"
	"sync"
)

func work() {
	fmt.Println("working...")
}

func main() {
	var wg sync.WaitGroup

	wg.Add(1)
	go func() {
		defer wg.Done()
		work()
	}()

	wg.Wait()
}

Ako ovo pokrenemo, možemo videti da naš program radi kako se očekuje.

$ go run main.go
working...

Takođe možemo WaitGroupdirektno proslediti funkciji.

func work(wg *sync.WaitGroup) {
	defer wg.Done()
	fmt.Println("working...")
}

func main() {
	var wg sync.WaitGroup

	wg.Add(1)

	go work(&wg)

	wg.Wait()
}

Ali je važno znati da se a WaitGroup ne sme kopirati nakon prve upotrebe. A ako se eksplicitno prosleđuje u funkcije, to treba da se uradi pomoću pointera. To je zato što može uticati na naš brojač, što će poremetiti logiku našeg programa.

Hajde da povećamo i broj gorutina pozivanjem Addmetode koja čeka 4 gorutine.

func main() {
	var wg sync.WaitGroup

	wg.Add(4)

	go work(&wg)
	go work(&wg)
	go work(&wg)
	go work(&wg)

	wg.Wait()
}

I kao što se i očekivalo, sve naše gorutine su izvršene.

$ go run main.go
working...
working...
working...
working...

Muteks

Mutex je međusobno isključujuća brava koja sprečava druge procese da uđu u kritični deo podataka dok ga neki proces zauzima kako bi se sprečilo nastajanje uslova trke.
Šta je kritični odeljak?

Dakle, kritična sekcija može biti deo koda koji ne sme da se izvršava od strane više niti istovremeno jer kod sadrži deljene resurse.
Upotreba

Možemo sync.Mutexkoristiti sledeće metode:

    Lock()stiče ili drži bravu.
    Unlock()otključava bravu.
    TryLock()pokušava da zaključa i javlja da li je uspelo.

Primer

Hajde da pogledamo primer, kreiraćemo Counterstrukturu i dodati Updatemetodu koja će ažurirati internu vrednost.

package main

import (
	"fmt"
	"sync"
)

type Counter struct {
	value int
}

func (c *Counter) Update(n int, wg *sync.WaitGroup) {
	defer wg.Done()
	fmt.Printf("Adding %d to %d\n", n, c.value)
	c.value += n
}

func main() {
	var wg sync.WaitGroup

	c := Counter{}

	wg.Add(4)

	go c.Update(10, &wg)
	go c.Update(-5, &wg)
	go c.Update(25, &wg)
	go c.Update(19, &wg)

	wg.Wait()
	fmt.Printf("Result is %d", c.value)
}

Hajde da ovo pokrenemo i vidimo šta će se desiti.

$ go run main.go
Adding -5 to 0
Adding 10 to 0
Adding 19 to 0
Adding 25 to 0
Result is 49

To ne izgleda tačno, izgleda kao da je naša vrednost uvek nula, ali smo nekako dobili tačan odgovor.

Pa, to je zato što, u našem primeru, više gorutina ažurira valuepromenljivu. I kao što ste verovatno pretpostavili, ovo nije idealno.

Ovo je savršen slučaj upotrebe za Mutex. Dakle, hajde da počnemo tako što ćemo koristiti sync.Mutexi umotati našu kritičnu sekciju između metoda Lock()i Unlock().

package main

import (
	"fmt"
	"sync"
)

type Counter struct {
	m     sync.Mutex
	value int
}

func (c *Counter) Update(n int, wg *sync.WaitGroup) {
	c.m.Lock()
	defer wg.Done()
	fmt.Printf("Adding %d to %d\n", n, c.value)
	c.value += n
	c.m.Unlock()
}

func main() {
	var wg sync.WaitGroup

	c := Counter{}

	wg.Add(4)

	go c.Update(10, &wg)
	go c.Update(-5, &wg)
	go c.Update(25, &wg)
	go c.Update(19, &wg)

	wg.Wait()
	fmt.Printf("Result is %d", c.value)
}

$ go run main.go
Adding -5 to 0
Adding 19 to -5
Adding 25 to 14
Adding 10 to 39
Result is 49

Izgleda da smo rešili problem i rezultat takođe izgleda ispravno.

Napomena: Slično kao kod WaitGroup, Mutex se ne sme kopirati nakon prve upotrebe.
RWMutex

RWMutex je međusobno isključena brava čitača/pisača. Bravu može da drži proizvoljan broj čitača ili jedan pisac.

Drugim rečima, čitaoci ne moraju da čekaju jedni druge. Treba samo da čekaju pisce koji drže katanac.

sync.RWMutexje stoga poželjnije za podatke koji se uglavnom čitaju, a resurs koji se štedi u poređenju sa je sync.Mutexvreme.
Upotreba

Slično kao sync.Mutex, možemo koristiti sync.RWMutexsledeće metode:

    Lock()stiče ili drži bravu.
    Unlock()otključava bravu.
    RLock()stiče ili drži zaključavanje za čitanje.
    RUnlock()otključava za čitanje.

Obratite pažnju kako RWMutex ima dodatne RLockmetode RUnlocku poređenju sa Mutex-om.
Primer

Dodajmo GetValuemetodu koja će čitati vrednost brojača. Takođe ćemo promeniti sync.Mutexu sync.RWMutex.

Sada možemo jednostavno koristiti metode RLocki RUnlocktako da čitaoci ne moraju da čekaju jedni druge.

package main

import (
	"fmt"
	"sync"
	"time"
)

type Counter struct {
	m     sync.RWMutex
	value int
}

func (c *Counter) Update(n int, wg *sync.WaitGroup) {
	defer wg.Done()

	c.m.Lock()
	fmt.Printf("Adding %d to %d\n", n, c.value)
	c.value += n
	c.m.Unlock()
}

func (c *Counter) GetValue(wg *sync.WaitGroup) {
	defer wg.Done()

	c.m.RLock()
	defer c.m.RUnlock()
	fmt.Println("Get value:", c.value)
	time.Sleep(400 * time.Millisecond)
}

func main() {
	var wg sync.WaitGroup

	c := Counter{}

	wg.Add(4)

	go c.Update(10, &wg)
	go c.GetValue(&wg)
	go c.GetValue(&wg)
	go c.GetValue(&wg)

	wg.Wait()
}

$ go run main.go
Get value: 0
Adding 10 to 0
Get value: 10
Get value: 10

Napomena: I sync.Mutexi sync.RWMuteximplementiraju sync.Lockerinterfejs.

type Locker interface {
    Lock()
    Unlock()
}

Kond

Uslovna sync.Condpromenljiva može se koristiti za koordiniranje onih gorutina koje žele da dele resurse. Kada se stanje deljenih resursa promeni, može se koristiti za obaveštavanje gorutina koje je blokirao mutex.

Svaki Cond ima pridruženu bravu (često a *Mutexili *RWMutex), koja mora biti zaključana pri promeni uslova i pri pozivanju Wait metode.
Ali zašto nam je to potrebno?

Jedan scenario može biti kada jedan proces prima podatke, a drugi procesi moraju da čekaju da ovaj proces primi podatke pre nego što mogu da pročitaju ispravne podatke.

Ako jednostavno koristimo kanal ili mutex, samo jedan proces može da čeka i čita podatke. Ne postoji način da se obaveste drugi procesi da čitaju podatke. Stoga možemo sync.Condda koordiniramo deljene resurse.
Upotreba

sync.Conddolazi sa sledećim metodama:

    NewCond(l Locker)vraća novi Uslov.
    Broadcast()budi sve gorutine koje čekaju na uslov.
    Signal()budi jednu gorutinu čekajući uslov ako ga ima.
    Wait()atomski otključava osnovni mutex zaključavanje.

Primer

Evo primera koji demonstrira interakciju različitih gorutina koristeći Cond.

package main

import (
	"fmt"
	"sync"
	"time"
)

var done = false

func read(name string, c *sync.Cond) {
	c.L.Lock()
	for !done {
		c.Wait()
	}
	fmt.Println(name, "starts reading")
	c.L.Unlock()
}

func write(name string, c *sync.Cond) {
	fmt.Println(name, "starts writing")
	time.Sleep(time.Second)

	c.L.Lock()
	done = true
	c.L.Unlock()

	fmt.Println(name, "wakes all")
	c.Broadcast()
}

func main() {
	var m sync.Mutex
	cond := sync.NewCond(&m)

	go read("Reader 1", cond)
	go read("Reader 2", cond)
	go read("Reader 3", cond)
	write("Writer", cond)

	time.Sleep(4 * time.Second)
}

$ go run main.go
Writer starts writing
Writer wakes all
Reader 2 starts reading
Reader 3 starts reading
Reader 1 starts reading

Kao što vidimo, čitaoci su bili suspendovani korišćenjem Waitmetode sve dok pisac nije koristio Broadcastmetodu da probudi proces.
Jednom

Jednom se osigurava da će se izvršiti samo jedno izvršenje čak i među nekoliko gorutina.
Upotreba

Za razliku od drugih primitiva, sync.Onceima samo jednu metodu:

    Do(f func())poziva funkciju f samo jednom . Ako Dose poziva više puta, samo prvi poziv će pozvati funkciju f.

Primer

Ovo deluje prilično jednostavno, uzmimo primer:

package main

import (
	"fmt"
	"sync"
)

func main() {
	var count int

	increment := func() {
		count++
	}

	var once sync.Once

	var increments sync.WaitGroup
	increments.Add(100)

	for i := 0; i < 100; i++ {
		go func() {
			defer increments.Done()
			once.Do(increment)
		}()
	}

	increments.Wait()
	fmt.Printf("Count is %d\n", count)
}

$ go run main.go
Count is 1

Kao što vidimo, čak i kada smo pokrenuli 100 gorutina, broj se povećao samo jednom.
Bazen

Pul je skalabilni pul privremenih objekata i takođe je bezbedan za konkurentnost. Bilo koja sačuvana vrednost u pulu može se izbrisati u bilo kom trenutku bez prijema obaveštenja. Pored toga, pod velikim opterećenjem, pul objekata se može dinamički proširiti, a kada se ne koristi ili konkurentnost nije visoka, pul objekata će se smanjiti.

Ključna ideja je ponovna upotreba objekata kako bi se izbeglo ponovno stvaranje i uništavanje, što će uticati na performanse.
Ali zašto nam je to potrebno?

Svrha bazena je da kešira dodeljene, ali nekorišćene stavke za kasniju ponovnu upotrebu, smanjujući pritisak na sakupljač smeća. To jest, olakšava kreiranje efikasnih, nitno bezbednih lista slobodnih stavki. Međutim, nije pogodan za sve liste slobodnih stavki.

Odgovarajuća upotreba bazena je upravljanje grupom privremenih stavki koje se tiho dele između i potencijalno ponovo koriste od strane istovremenih nezavisnih klijenata paketa. Bazen pruža način da se troškovi alokacije raspodele na više klijenata.

Važno je napomenuti da Pool takođe ima svoju cenu u pogledu performansi. Mnogo je sporiji za korišćenje sync.Poolod jednostavne inicijalizacije. Takođe, Pool se ne sme kopirati nakon prve upotrebe.
Upotreba

sync.Pooldaje nam sledeće metode:

    Get()bira proizvoljnu stavku iz bazena, uklanja je iz bazena i vraća je pozivaocu.
    Put(x any)dodaje stavku u pul.

Primer

Sada, pogledajmo jedan primer.

Prvo, kreiraćemo novi sync.Pool, gde opciono možemo da navedemo funkciju koja će generisati vrednost kada pozovemo , Getu suprotnom će vratiti nilvrednost.

package main

import (
	"fmt"
	"sync"
)

type Person struct {
	Name string
}

var pool = sync.Pool{
	New: func() any {
		fmt.Println("Creating a new person...")
		return &Person{}
	},
}

func main() {
	person := pool.Get().(*Person)
	fmt.Println("Get object from sync.Pool for the first time:", person)

	fmt.Println("Put the object back in the pool")
	pool.Put(person)

	person.Name = "Gopher"
	fmt.Println("Set object property name:", person.Name)

	fmt.Println("Get object from pool again (it's updated):", pool.Get().(*Person))
	fmt.Println("There is no object in the pool now (new one will be created):", pool.Get().(*Person))
}

I ako ovo pokrenemo, videćemo zanimljiv izlaz:

$ go run main.go
Creating a new person...
Get object from sync.Pool for the first time: &{}
Put the object back in the pool
Set object property name: Gopher
Get object from pool again (it's updated): &{Gopher}
Creating a new person...
There is no object in the pool now (new one will be created): &{}

Obratite pažnju kako smo uradili tvrdnju tipa kada smo pozvali Get.

Može se videti da sync.Poolje isključivo privremeni objektni pul, koji je pogodan za čuvanje nekih privremenih objekata koji će se deliti između gorutina.
Mapa

Mapa je kao standardna, map[any]anyali je bezbedna za istovremenu upotrebu od strane više gorutina bez dodatnog zaključavanja ili koordinacije. Učitavanja, čuvanja i brisanja su raspoređena tokom konstantnog vremena.
Ali zašto nam je to potrebno?

Tip Mapa je specijalizovan . Većina koda bi trebalo da koristi običnu Go mapu umesto toga, sa odvojenim zaključavanjem ili koordinacijom, radi bolje bezbednosti tipa i kako bi se olakšalo održavanje drugih invarijanti zajedno sa sadržajem mape.

Tip mape je optimizovan za dva uobičajena slučaja upotrebe:

    Kada se unos za dati ključ upisuje samo jednom, ali čita više puta, kao u keš memorijama koje samo rastu.
    Kada više gorutina čita, piše i prepisuje zapise za disjunktne skupove ključeva. U ova dva slučaja, upotreba sync.Mapmože značajno smanjiti konkurenciju za zaključavanje u poređenju sa Go mapom uparenom sa odvojenim Mutexili RWMutex.

Nulta mapa je prazna i spremna za upotrebu. Mapa se ne sme kopirati nakon prve upotrebe.
Upotreba

sync.Mapdaje nam sledeće metode:

    Delete()briše vrednost za ključ.
    Load(key any)vraća vrednost sačuvanu u mapi za ključ, ili nil ako vrednost nije prisutna.
    LoadAndDelete(key any)briše vrednost za ključ, vraćajući prethodnu vrednost ako postoji. Učitani rezultat izveštava da li je ključ bio prisutan.
    LoadOrStore(key, value any)vraća postojeću vrednost za ključ ako je prisutan. U suprotnom, čuva i vraća datu vrednost. Učitani rezultat je tačno ako je vrednost učitana, a netačno ako je sačuvana.
    Store(key, value any)podešava vrednost za ključ.
    Range(f func(key, value any) bool)poziva fsekvencijalno za svaki ključ i vrednost prisutne u mapi. Ako fvrati vrednost "false", opseg zaustavlja iteraciju.

Napomena: Domet ne mora nužno odgovarati bilo kom konzistentnom snimku sadržaja mape.
Primer

Pogledajmo primer. Ovde ćemo pokrenuti nekoliko gorutina koje će istovremeno dodavati i preuzimati vrednosti sa naše mape.

package main

import (
	"fmt"
	"sync"
)

func main() {
	var wg sync.WaitGroup
	var m sync.Map

	wg.Add(10)
	for i := 0; i <= 4; i++ {
		go func(k int) {
			v := fmt.Sprintf("value %v", k)

			fmt.Println("Writing:", v)
			m.Store(k, v)
			wg.Done()
		}(i)
	}

	for i := 0; i <= 4; i++ {
		go func(k int) {
			v, _ := m.Load(k)
			fmt.Println("Reading: ", v)
			wg.Done()
		}(i)
	}

	wg.Wait()
}

Kao što se i očekivalo, naša operacija skladištenja i preuzimanja biće bezbedna za istovremenu upotrebu.

$ go run main.go
Reading: <nil>
Writing: value 0
Writing: value 1
Writing: value 2
Writing: value 3
Writing: value 4
Reading: value 0
Reading: value 1
Reading: value 2
Reading: value 3

Atomski

Paket atomic pruža niskonivoske atomske memorijske primitive za cele brojeve i pointere koji su korisni za implementaciju algoritama sinhronizacije.
Upotreba

atomicPaket pruža nekoliko funkcija koje obavljaju sledećih 5 operacija za tipove int, uinti uintptr:

    Dodaj
    Učitaj
    Prodavnica
    Zamena
    Uporedi i zameni

Primer

Nećemo moći da pokrijemo sve funkcije ovde. Zato, hajde da pogledamo najčešće korišćene funkcije da bismo AddInt32stekli predstavu.

package main

import (
  "fmt"
	"sync"
	"sync/atomic"
)

func add(w *sync.WaitGroup, num *int32) {
	defer w.Done()
	atomic.AddInt32(num, 1)
}

func main() {
	var n int32 = 0
	var wg sync.WaitGroup

	wg.Add(1000)
	for i := 0; i < 1000; i = i + 1 {
		go add(&wg, &n)
	}

	wg.Wait()

	fmt.Println("Result:", n)
}

Ovde atomic.AddInt32se garantuje da će rezultat nbiti 1000 jer se izvršavanje instrukcija atomskih operacija ne može prekinuti.

$ go run main.go
Result: 1000

Napredni obrasci konkurentnosti

U ovom tutorijalu ćemo razmotriti neke napredne obrasce konkurentnosti u Gou. Često se ovi obrasci koriste u kombinaciji u stvarnom svetu.
Generator

генератор

Zatim se generator Pattern koristi za generisanje niza vrednosti koje se koriste za proizvodnju nekog izlaza.

U našem primeru, imamo generatorfunkciju koja jednostavno vraća kanal iz kojeg možemo da čitamo vrednosti.

Ovo funkcioniše na osnovu činjenice da se slanje i prijem blokiraju dok i pošiljalac i primalac nisu spremni. Ovo svojstvo nam je omogućilo da sačekamo dok se ne zatraži sledeća vrednost.

package main

import "fmt"

func main() {
	ch := generator()

	for i := 0; i < 5; i++ {
		value := <-ch
		fmt.Println("Value:", value)
	}
}

func generator() <-chan int {
	ch := make(chan int)

	go func() {
		for i := 0; ; i++ {
			ch <- i
		}
	}()

	return ch
}

Ako ovo pokrenemo, primetićemo da možemo da konzumiramo vrednosti koje su proizvedene na zahtev.

$ go run main.go
Value: 0
Value: 1
Value: 2
Value: 3
Value: 4

Ovo je slično ponašanje kao yieldu Javaskriptu i Pajtonu.
Ventilator-in

фан-ин

Šema uključivanja ventilatora kombinuje više ulaza u jedan jedinstveni izlazni kanal. U osnovi, multipleksiramo naše ulaze.

U našem primeru, kreiramo ulaze i1koristeći i2funkciju generateWork. Zatim koristimo našu varijabilnu funkciju fanIn da kombinujemo vrednosti sa ovih ulaza u jedan izlazni kanal iz kojeg možemo da konzumiramo vrednosti.

Napomena: redosled unosa neće biti zagarantovan.

package main

import (
	"fmt"
	"sync"
)

func main() {
	i1 := generateWork([]int{0, 2, 6, 8})
	i2 := generateWork([]int{1, 3, 5, 7})

	out := fanIn(i1, i2)

	for value := range out {
		fmt.Println("Value:", value)
	}
}

func fanIn(inputs ...<-chan int) <-chan int {
	var wg sync.WaitGroup
	out := make(chan int)

	wg.Add(len(inputs))

	for _, in := range inputs {
		go func(ch <-chan int) {
			for {
				value, ok := <-ch

				if !ok {
					wg.Done()
					break
				}

				out <- value
			}
		}(in)
	}

	go func() {
		wg.Wait()
		close(out)
	}()

	return out
}

func generateWork(work []int) <-chan int {
	ch := make(chan int)

	go func() {
		defer close(ch)

		for _, w := range work {
			ch <- w
		}
	}()

	return ch
}

$ go run main.go
Value: 0
Value: 1
Value: 2
Value: 6
Value: 8
Value: 3
Value: 5
Value: 7

Raspodela

распрострањеност

Šabloni raspodele nam u suštini omogućavaju da podelimo naš jedan ulazni kanal na više izlaznih kanala. Ovo je koristan šablon za distribuciju radnih elemenata u više uniformnih aktera.

U našem primeru, delimo ulazni kanal na 4 različita izlazna kanala. Za dinamički broj izlaza, možemo spojiti izlaze u zajednički "agregirani" kanal i koristiti select.

Napomena: obrazac širenja se razlikuje od pub/sub.

package main

import "fmt"

func main() {
	work := []int{1, 2, 3, 4, 5, 6, 7, 8}
	in := generateWork(work)

	out1 := fanOut(in)
	out2 := fanOut(in)
	out3 := fanOut(in)
	out4 := fanOut(in)

	for range work {
		select {
		case value := <-out1:
			fmt.Println("Output 1 got:", value)
		case value := <-out2:
			fmt.Println("Output 2 got:", value)
		case value := <-out3:
			fmt.Println("Output 3 got:", value)
		case value := <-out4:
			fmt.Println("Output 4 got:", value)
		}
	}
}

func fanOut(in <-chan int) <-chan int {
	out := make(chan int)

	go func() {
		defer close(out)

		for data := range in {
			out <- data
		}
	}()

	return out
}

func generateWork(work []int) <-chan int {
	ch := make(chan int)

	go func() {
		defer close(ch)

		for _, w := range work {
			ch <- w
		}
	}()

	return ch
}

Kao što vidimo, naš rad je podeljen između više gorutina.

$ go run main.go
Output 1 got: 1
Output 2 got: 3
Output 4 got: 4
Output 1 got: 5
Output 3 got: 2
Output 3 got: 6
Output 3 got: 7
Output 1 got: 8

Cevovod

цевовод

Šablon cevovoda je niz faza povezanih kanalima, gde je svaka faza grupa gorutina koje izvršavaju istu funkciju.

U svakoj fazi, gorutine:

    Primajte vrednosti iz uzvodnog sistema putem dolaznih kanala.
    Izvršite neku funkciju na tim podacima, obično proizvodeći nove vrednosti.
    Šaljite vrednosti nizvodno putem odlaznih kanala.

Svaka faza ima neograničen broj dolaznih i odlaznih kanala, osim prve i poslednje faze, koje imaju samo odlazne odnosno dolazne kanale. Prva faza se ponekad naziva izvor ili proizvođač ; poslednja faza je potrošač ili potrošač .

Korišćenjem cevovoda, razdvajamo brige svake faze, što pruža brojne prednosti kao što su:

    Izmenite faze nezavisno jednu od druge.
    Kombinujte načine kombinovanja faza nezavisno od same izmene faze.

U našem primeru, definisali smo tri faze, filter, squarei half.

package main

import (
	"fmt"
	"math"
)

func main() {
	in := generateWork([]int{0, 1, 2, 3, 4, 5, 6, 7, 8})

	out := filter(in) // Filter odd numbers
	out = square(out) // Square the input
	out = half(out)   // Half the input

	for value := range out {
		fmt.Println(value)
	}
}

func filter(in <-chan int) <-chan int {
	out := make(chan int)

	go func() {
		defer close(out)

		for i := range in {
			if i%2 == 0 {
				out <- i
			}
		}
	}()

	return out
}

func square(in <-chan int) <-chan int {
	out := make(chan int)

	go func() {
		defer close(out)

		for i := range in {
			value := math.Pow(float64(i), 2)
			out <- int(value)
		}
	}()

	return out
}

func half(in <-chan int) <-chan int {
	out := make(chan int)

	go func() {
		defer close(out)

		for i := range in {
			value := i / 2
			out <- value
		}
	}()

	return out
}

func generateWork(work []int) <-chan int {
	ch := make(chan int)

	go func() {
		defer close(ch)

		for _, w := range work {
			ch <- w
		}
	}()

	return ch
}

Izgleda da je naš unos ispravno obrađen od strane cevovoda na istovremeni način.

$ go run main.go
0
2
8
18
32

Bazen radnika

раднички тим

Radnički bazen je zaista moćan obrazac koji nam omogućava da istovremeno raspodelimo posao na više radnika (gorutina).

U našem primeru, imamo jobskanal na koji ćemo slati naše poslove i resultskanal na koji će naši radnici slati rezultate kada završe posao.

Nakon toga, možemo istovremeno pokrenuti naše radnike i jednostavno primati rezultate sa resultskanala.

Idealno totalWorkersbi bilo da bude podešeno na runtime.NumCPU()što nam daje broj logičkih procesora koje trenutni proces može da koristi.

package main

import (
	"fmt"
	"sync"
)

const totalJobs = 4
const totalWorkers = 2

func main() {
	jobs := make(chan int, totalJobs)
	results := make(chan int, totalJobs)

	for w := 1; w <= totalWorkers; w++ {
		go worker(w, jobs, results)
	}

	// Send jobs
	for j := 1; j <= totalJobs; j++ {
		jobs <- j
	}

	close(jobs)

	// Receive results
	for a := 1; a <= totalJobs; a++ {
		<-results
	}

	close(results)
}

func worker(id int, jobs <-chan int, results chan<- int) {
	var wg sync.WaitGroup

	for j := range jobs {
		wg.Add(1)

		go func(job int) {
			defer wg.Done()

			fmt.Printf("Worker %d started job %d\n", id, job)

			// Do work and send result
			result := job * 2
			results <- result

			fmt.Printf("Worker %d finished job %d\n", id, job)
		}(j)
	}

	wg.Wait()
}

Kao što se i očekivalo, naši poslovi su bili raspoređeni među našim radnicima.

$ go run main.go
Worker 2 started job 4
Worker 2 started job 1
Worker 1 started job 3
Worker 2 started job 2
Worker 2 finished job 1
Worker 1 finished job 3
Worker 2 finished job 2
Worker 2 finished job 4

Čekanje u redu

чекање у реду

Šablon čekanja nam omogućava da obrađujemo nviše elemenata istovremeno.

U našem primeru, koristimo baferovani kanal da simuliramo ponašanje reda čekanja. Jednostavno šaljemo praznu strukturu našem queuekanalu i čekamo da je prethodni proces oslobodi kako bismo mogli da nastavimo.

To je zato što šalje blok baferovanom kanalu samo kada je bafer pun, a prima blok kada je bafer prazan.

Ovde imamo ukupan obim posla od 10 stavki i ograničenje od 2. To znači da možemo obraditi 2 stavke istovremeno.

Obratite pažnju na to kako je naš queuekanal tipa struct{}, jer prazna struktura zauzima nula bajtova memorije.

package main

import (
	"fmt"
	"sync"
	"time"
)

const limit = 2
const work = 10

func main() {
	var wg sync.WaitGroup

	fmt.Println("Queue limit:", limit)
	queue := make(chan struct{}, limit)

	wg.Add(work)

	for w := 1; w <= work; w++ {
		process(w, queue, &wg)
	}

	wg.Wait()

	close(queue)
	fmt.Println("Work complete")
}

func process(work int, queue chan struct{}, wg *sync.WaitGroup) {
	queue <- struct{}{}

	go func() {
		defer wg.Done()

		time.Sleep(1 * time.Second)
		fmt.Println("Processed:", work)

		<-queue
	}()
}

Ako ovo pokrenemo, primetićemo da se nakratko pauzira kada se obradi svaka druga stavka (što je naš limit) dok naš red čeka da bude izbačen iz reda.

$ go run main.go
Queue limit: 2
Processed: 1
Processed: 2
Processed: 4
Processed: 3
Processed: 5
Processed: 6
Processed: 8
Processed: 7
Processed: 9
Processed: 10
Work complete

Dodatni obrasci

Neki dodatni obrasci koje bi moglo biti korisno znati:

    T-kanal
    Kanal mosta
    Kanal prstenastog bafera
    Ograničeni paralelizam

Kontekst

U istovremenim programima, često je potrebno preventivno zaustaviti operacije zbog isteka vremena, otkazivanja ili kvara drugog dela sistema.

Paket contextolakšava prosleđivanje vrednosti ograničenih na zahtev, signala za otkazivanje i rokova preko granica API-ja svim gorutinama uključenim u obradu zahteva.
Vrste

Hajde da razgovaramo o nekim osnovnim tipovima paketa context.
Kontekst

To Contextje interfacetip koji je definisan na sledeći način:

type Context interface {
	Deadline() (deadline time.Time, ok bool)
	Done() <-chan struct{}
	Err() error
	Value(key any) any
}

Tip Contextima sledeće metode:

    Done() <- chan struct{}vraća kanal koji je zatvoren kada se kontekst otkaže ili kada istekne vreme. Done može vratiti vrednost nilako se kontekst nikada ne može otkazati.
    Deadline() (deadline time.Time, ok bool)vraća vreme kada će kontekst biti otkazan ili će vremenski isteći. Rok vraća okkao falsekada rok nije podešen.
    Err() errorvraća grešku koja objašnjava zašto je kanal Done zatvoren. Ako Done još nije zatvoren, vraća nil.
    Value(key any) anyvraća vrednost povezanu sa ključem ili nilako nema.

Funkcija Otkaži

A CancelFuncnaređuje operaciji da prekine svoj rad i ne čeka da se rad zaustavi. Ako je pozove više gorutina istovremeno, nakon prvog poziva, naredni pozivi kategorije a CancelFuncne rade ništa.

type CancelFunc func()

Upotreba

Hajde da razgovaramo o funkcijama koje su izložene u contextpaketu:
Pozadina

Pozadina vraća praznu vrednost, različitu od nil Context. Nikada se ne otkazuje, nema vrednosti i nema rok.

Obično ga koriste glavna funkcija, inicijalizacija i testovi, i kao kontekst najvišeg nivoa za dolazne zahteve.

func Background() Context

ZADACI

Slično Backgroundfunkciji, TODOfunkcija takođe vraća vrednost koja nije nula, praznu vrednost Context.

Međutim, trebalo bi ga koristiti samo kada nismo sigurni koji kontekst da koristimo ili ako funkcija nije ažurirana da bi primila kontekst. To znači da planiramo da dodamo kontekst funkciji u budućnosti.

func TODO() Context

SaVrednošću

Ova funkcija uzima kontekst i vraća izvedeni kontekst gde je vrednost valpovezana sa kontekstom keyi prolazi kroz stablo konteksta sa njim.

To znači da kada dobijete kontekst sa vrednošću, svaki kontekst koji iz njega proizilazi dobija tu vrednost.

Ne preporučuje se prosleđivanje kritičnih parametara koristeći kontekstualne vrednosti, umesto toga, funkcije bi trebalo da prihvate te vrednosti u potpisu, čineći ga eksplicitnim.

func WithValue(parent Context, key, val any) Context

Primer

Uzmimo jednostavan primer da vidimo kako možemo dodati par ključ-vrednost u kontekst.

package main

import (
	"context"
	"fmt"
)

func main() {
	processID := "abc-xyz"

	ctx := context.Background()
	ctx = context.WithValue(ctx, "processID", processID)

	ProcessRequest(ctx)
}

func ProcessRequest(ctx context.Context) {
	value := ctx.Value("processID")
	fmt.Printf("Processing ID: %v", value)
}

I ako ovo pokrenemo, videćemo da processIDse prenosi preko našeg konteksta.

$ go run main.go
Processing ID: abc-xyz

SaOtkaži

Ova funkcija kreira novi kontekst iz roditeljskog konteksta i izvedenog konteksta i funkcije otkazivanja. Roditelj može biti context.Backgroundili kontekst koji je prosleđen u funkciju.

Otkazivanje ovog konteksta oslobađa resurse povezane sa njim, tako da bi kod trebalo da pozove funkciju otmena čim se operacije koje se izvršavaju u ovom kontekstu završe.

Prenošenje cancelfunkcije se ne preporučuje jer može dovesti do neočekivanog ponašanja.

func WithCancel(parent Context) (ctx Context, cancel CancelFunc)

Sa rokom

Ova funkcija vraća izvedeni kontekst iz svog roditelja koji se otkazuje kada istekne rok ili kada se pozove funkcija otkazivanja.

Na primer, možemo kreirati kontekst koji će se automatski otkazati u određenom trenutku u budućnosti i to proslediti podređenim funkcijama. Kada se taj kontekst otkaza zbog isteka roka, sve funkcije koje su dobile kontekst dobijaju obaveštenje da prestanu sa radom i vrate se.

func WithDeadline(parent Context, d time.Time) (Context, CancelFunc)

Sa vremenskim ograničenjem

Ova funkcija je samo omotač oko WithDeadlinefunkcije sa dodatnim vremenskim ograničenjem.

func WithTimeout(parent Context, timeout time.Duration) (Context, CancelFunc) {
	return WithDeadline(parent, time.Now().Add(timeout))
}

Primer

Pogledajmo jedan primer kako bismo učvrstili naše razumevanje konteksta.

U primeru ispod, imamo jednostavan HTTP server koji obrađuje zahtev.

package main

import (
	"fmt"
	"net/http"
	"time"
)

func handleRequest(w http.ResponseWriter, req *http.Request) {
	fmt.Println("Handler started")
	context := req.Context()

	select {
	// Simulating some work by the server, waits 5 seconds and then responds.
	case <-time.After(5 * time.Second):
		fmt.Fprintf(w, "Response from the server")

	// Handling request cancellation
	case <-context.Done():
		err := context.Err()
		fmt.Println("Error:", err)
	}

	fmt.Println("Handler complete")
}

func main() {
	http.HandleFunc("/request", handleRequest)

	fmt.Println("Server is running...")
	http.ListenAndServe(":4000", nil)
}

Otvorimo dva terminala. U terminalu jedan ćemo pokrenuti naš primer.

$ go run main.go
Server is running...
Handler started
Handler complete

U drugom terminalu, jednostavno ćemo poslati zahtev našem serveru. I ako sačekamo 5 sekundi, dobićemo odgovor.

$ curl localhost:4000/request
Response from the server

Sada, da vidimo šta se dešava ako otkažemo zahtev pre nego što se završi.

Napomena: možemo koristiti ctrl + cda otkažemo zahtev na pola puta.

$ curl localhost:4000/request
^C

I kao što vidimo, u mogućnosti smo da detektujemo otkazivanje zahteva zbog konteksta zahteva.

$ go run main.go
Server is running...
Handler started
Error: context canceled
Handler complete

Siguran sam da već možete videti koliko ovo može biti izuzetno korisno.

Na primer, ovo možemo koristiti da otkažemo bilo koji posao koji zahteva mnogo resursa ako više nije potreban ili je prekoračio rok ili vremenski istekao.
*/
