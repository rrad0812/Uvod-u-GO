
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
