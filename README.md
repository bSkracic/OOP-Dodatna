# OOP: priprema za M1 i dodatni zadaci za vježbu
Sljedeća tri zadatka potrebno je riješiti koristeći objektno orijentiranu paradigmu upotrebom najboljih praksi i naputaka za pisanje "čistog" izvornog koda. Rješenja zadataka potrebno je predati kao zip datoteke na moj mail bskracic@racunarstvo.hr, po mogućnosti do subote **20.11**.u **8:00**, kada ću održati poseban sat dodatne nastave gdje ću riješavati ove zadatke, komentirati vaša rješenja i odgovarati na sva moguća pitanja i poteškoće. 

Prilikom rješavanja zadataka nemojte staviti naglasak na izradu  programa pokretača (*drivera*) i funkcionalnosti aplikacije već se usredotočite na konstrukciju razreda (eng. class), nasljeđivanja, sučelja, enumeracije itd.

## 1. Zadatak: Košarica
Košarica je online trgovina gdje je moguće nabaviti različite proizvode. Potrebno je osmilisiti jednsotavnu CLI aplikaciju koja bi korisniku omogućila ispis liste svih proizvoda, odabir proizvoda te ga tako dodati u košaricu i pri završetku dodavanja proizvoda izvršiti naplatu. \
Proizvodi imaju jedinstven identifikator po kojem se razlikuju na skladištu te uz to imaju ime, cijenu i raspoloživost u poslovnicama. Proizvodi se dijele na fizičke proizvode (npr. "Usb C adapter") i usluge (npr. MS Office paket). Proizvodima se cijena računa kao količina x cijena komada, dok se uslugama cijena računa kao 12 x mjesečna cijena (njegova količina označava u listi proizvoda označava se sa 'x').

```
Dobrodosli u Kosaricu!
Danas je <datum> i id vase kosarice je: <uuid>
Proizvodi koje nudimo:

100000 | Usb C adapter    | 2  |  25.00 kn
100001 | MS Powerpoint    | x  |  150.kn/mjesec
100002 | Nintendo Switch  | 5  |  2899.99 kn
...
```
Od korisnika se potom traži unos identifikatora proizvoda i količine (odvojene razmakom), te ukoliko proizvod postoji na skladištu, potrebno ga je dodati u košaricu i ispisati ukupnu cijenu proizvoda trenutno u košarici. Prilikom unosa identifikatora proizvoda čija je je raspoloživa količina označena sa 'x' (odnosno kada je riječ o usluzi), nije potrebno unositi količinu.
```
Dodajte proizvod [proizvod_id] [kolicina]: 100002 1 
(Ispis) Proizvod je uspjesno dodan, suma: 2899.99 kn
###
Dodajte proizvod [proizvod_id] [kolicina]:  100001
(Ispis) Proizvod je uspjesno dodan, suma: 4699.99 kn
###
Dodajte proizvod [proizvod_id] [kolicina]:  100001 3
Proizvod nije dostupan u trazenoj kolicini
```

## 2. Zadatak: Napad-Obrana-Pregovor

Potrebno je osmilisiti *text-based* igru u kojoj vaša junakinja ili junak nasumično susreće sljedeće neprijatelje:

Na početku igre, igrač upisuje ime svog junaka ili junakinje.
Tijekom igre ispred junaka se stvara neprijatelj kojeg igrač pobjeđuje odabirom jedne od tri akcije. 

Junakinja ili junak i neprijatelji imaju tri tipa **akcije**: 
1. **Napad**
2. **Obrana**
3. **Pregovor**

koji se međusobno odnose kao entiteti u igri kamen-škare-papir: 
1. Obrana pobjeđuje napad
2. Napad pobjeđuje pregovor
3. Pregovor pobjeđuje obranu 

Svaki neprijatelj ima svoju definiranu poruku pozdrava, koja se prikazuje kada igrač naiđe na njega i poruku gubitka, koja se prikazuje kada ga igrač pobijedi u igri. (po izboru) te ime (npr. uhljeb Borna)
Potom počinje igra koja se ponavlja u krugovima dok god ne dode do pobjede.
Neprijatelji se 

- Uhljeb \
Uhljeb uvijek odabire istu akciju koju je prvu odabrao.

- Lopov \
U prvom krugu odabire nasumičnu akciju, a ukoliko dođe do izjednačenja (eng. *tie*), lopov u sljedećem krugu odabire akciju koja pobjeđuje akciju koju je igrač odigrao u trenutno završenom krugu.

- Encikolpedist \
Ima 60 % šanse da odigra akciju napada, 20% šanse da odigra akciju obrane i 10% šanse da odigra akciju pregovora i 10% šanse da se preda, odnosno da se odma pokaže poruka njegovog gubitka.

- Šefovi: \
Šef "Ćaća" ima 90% šanse da odigra akciju obrane, 5% šanse da odigra akciju pregovora i 5% šanse da odigra akciju obrane. \
Šef "Franjo" ima 90% šanse da izvuce napad, 5% sanse da izvuce obranu i 5% sanse da izvuce obranu. \
Šef "Milo moje" ima 90% šanse da izvuce pregovore, 5% sanse da izvuce napad i 5% sanse da izvuce obranu. 

Primjer početka:\
(Igračev unos označen je između znakova '<' i '>', npr. <Pero<t>>)
```
Dobrodosli u Politicki lov!
Unesite ime: <Pero>
Pero krece u avanturu!
```

Sada je potrebno iz liste instanciranih neprijatelja, nasumično odabrati jednoga koji će biti neprijatelj, u našem slučaju to je uhljeb Šime.

Primjer kruga igre:
```
Pero je susreo uhljeba Simu!
Odaberite akciju [napad, obrana, pregovor]: <napad>
Sime: "Ja sam superioran!"
Sime je pobijedio/la koristeci napad.
KRAJ IGRE
```

Dodatni primjer kruga igre:
```
Pero je sreo uhljeba Simu!
Odaberite akciju [napad, obrana, pregovor]: <napad>
Izjednacenje: I Sime i Pero su koristili napad.
Odaberite akciju [napad, obrana, pregovor]: <obrana>
Sime: "Oh ne ja sam izgubio..."
Pero je pobijedio/la koristeci obranu.
--------------------------------------------------
Pero je sreo lopova Janka!
Odaberite akciju [napad, obrana, pregovor]: <pregovor>
Izjednacenje: I Janko i Pero su koristili pregovor.
Odaberite akciju [napad, obrana, pregovor]: <obrana>
Janko: "Kako je to moguce? Trebao sam pobijediti!!"
Pero je pobijedio/la koristeci obranu.

....

```

## 3. Zadatak: Sustav provjera vjerodajnica
Provjera vjerodajnica ili autentifikacija je proces s kojima korisnici aplikacije potvrđuju svoj identitet. Potrebno je napraviti CLI aplikaciju koja traži od korisnika upis emaila i lozinke i ulogu koju korisnik obavlja: 
- Radnik
Kada se korisnik prijavi kao radnik potrebno je od njega tražiti unos URL-a čiji je sadržaj potrebno ispisati koristeći odgovor(response) HTTP GET zahtjeva (request).

- Moderator \
Kada se korisnik prijavi kao moderator potrebno je ispisati trenutno vrijeme u obliku UNIX timestampa.

- Administrator \
Kada se korisnik prijavi kao administrator potrebno je učitati i ispisati listu svih korisnika(moderatora, administratora i radnika) te implementirati mogućnost dodavanja novih korisnika dok god to administrator želi. Podaci koje treba učitati su email, lozinka i tip korisnika(radnik, moderator i administrator). UUID korisnika se generira nasumično. 

Podatke o korisnicima potrebno je spremiti u tekstualnu datoteku te prilikom provjera vjerodajnica (autentifikacije) učitavati podatke o korisnicima.



