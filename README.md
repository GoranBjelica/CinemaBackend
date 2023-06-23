# CinemaBackend
Cinema application backend Java, MySQL

Bioskop aplikacija

Web aplikacija - za backend korišćena Java kao programski jezik I Spring Boot kao radni okvir, kao baza podataka korišćen je MySQL.

Bioskopska aplikacija koju koriste 3 grupe korisnika: neprijavljeni korisnici, prijavljeni korisnici i administratori.

Aplikacija rukuje sledećim elementima:

-Tip projekcije (2D, 3D, 4D): ID, naziv.
-Sala: ID, naziv, tipovi projekcija (jedan ili više mogućih tipova projekcija).

-Sedište: Redni broj (jedinstveno na nivou sale), sala (kojoj sedište pripada).

-Film: ID, naziv, režiser, trajanje, distributer, zemlja porekla, godina proizvodnje, opis, link ka posteru filma I link ka imdb stranici filma.

-Projekcija:  ID, film koji se prikazuje (administrator bira među ponuđenima, a povezuje aplikacija), tip projekcije (administrator bira među ponuđenima, a povezuje aplikacija), sala (administrator bira među ponuđenima, a povezuje aplikacija), datum i vreme prikazivanja, cena karte, administrator koji je dodao projekciju (povezuje aplikacija).

Pri unosu nove projekcije sala mora da ispuni zahteve odabranog tipa projekcije. Datum i vreme prikazivanja ne smeju biti u prošlosti. Sala mora biti slobodna (ne sme imati za sebe vezanu projekciju takvu da trajanje filma u odnosu na njen datum i vreme prikazivanja premašuju datum i vreme prikazivanja projekcije koja se dodaje).

-Karta: ID, projekcija za koju se kupuje karta (običan korisnik bira, a povezuje aplikacija), sedište za koje se kupuje karta (običan korisnik bira, a povezuje aplikacija), datum i vreme prodaje (generiše aplikacija), običan korisnik koji je kupio kartu (povezuje aplikacija)
Pri kupovini karte, početak projekcije ne sme biti u prošlosti. Sedište ne sme biti zauzeto (ne sme imati prodatu kartu za datu projekciju).
-Korisnik: ID, korisničko ime (jedinstveno, može da sadrži samo alfanumeričke karaktere i to bez razmaka, minimalne dužine 3 karaktera), lozinka (može da sadrži samo alfanumeričke karaktere i to bez razmaka, minimalne dužine 5 karaktera), ime (minimalno dva slova), prezime (minimalno dva slova), email, datum registracije (generiše aplikacija), uloga (običan korisnik ili administrator)
Pri registraciji, uloga se ne unosi, a korisnik dobija ulogu običnog korisnika.

Aplikacija poseduje unapred definisane tipove projekcija:
Sala 1 podržava 2D I 3D projekcije,
Sala 2 podržava samo 2D projekcije,
Sala 3 podražava samo 2D projekcije,
Sala 4 podražava 3D I 4D projekcije,
Sala 5 podržava samo 4D projekcije
Filmovi
Stranica sa filmovima prikazuje  tabelu svih filmova sa svim podacima osim ID-a i režisera i opisa.
Omoogucena je pretraga I filtriranje filmova.
Samo aministratori imaju opciju dodavanja novog filma.
Na stranici svakog filma je prikazano sve o filmu osim ID-a.
Administratorima je omogućena komanda za izmenu filma i za brisanje filma. Ako film ima projekcije,brisanje je samo logičko (film se ne prikazuje na stranici za pregled svih filmova, niti ga je moguće odabrati za buduće kreirane projekcije, ali mu se i dalje može pristupiti putem linka
Projekcije
Podrazumevana glavna stranica aplikacije prikazuje tabelu svih projekcija za tekući datum sa filmovima, datumima I vremenima prikazivanja, tipovima projekcija, salama i cenama.
Omogućena je pretraga (filtriranje) projekcija po filmu, opsegu datuma i vremena, tipu projekcije, sali, i opsegu cena karata, kao i kombinacijama svih ovih kriterijuma. Omogućeno je i sortiranje projekcija po svakom od pomenutih kriterijuma, po rastućem ili opadajućem poretku.
Administratori imaju opciju za dodavanje nove projekcije.
Administratorima je prikazana komanda za brisanje projekcije. Ako projekcija ima prodate karte, brisanje je samo logičko (projekcija se ne prikazuje na početnoj stranici). 
Običnim korisnicima prikazana je opcija za kupovinu karte, ali samo ako projekcija nije u prošlosti i ako nije rasprodata.
Administratorima je prikazana opcija za pregled tabele prodatih karata (za posmatranu projekciju) sa datumom I vremenom prodaje karte i korisničkim imenom kupca. 

Kupljene karte
Ulogovanim korisnicima je omoguceno da kupe kartu za slobodna mesta za projekciju
Izvršavanjem ove komande se za svako odabrano sedište kreira kupljena karta za prijavljenog običnog korisnika.
Administratorima je na prilikom prikaza projekcije I prodatih karata za projekciju prikazan i korisnik koji je kupio kartu.
Korisnici
Neprijavljeni korisnik može da se registruje na sistem. 
Administrator moze da vidi tabelu svih korisnika sa korisničkim imenom, datumom (vremenom) registracije i ulogom.
Omogućena je pretraga korisnika po korisničkom imenu i ulozi. Omogućeno je i sortiranje korisnika po korisničkom imenu i ulozi po rastućem ili opadajućem poretku.
Na stranici svakog korisnika su prikazani svi podaci osim lozinke.
Omogućena je i izmenu lozinke. Korisnik može da izmeni samo svoju lozinku, pri čemu mora da unese validnu staru lozinku, administratorima je omogućeno da svakom korisniku promeni lozinku bez unosa stare lozinke.
Administratorima je omogućena izmenu uloge svakog korisnika.
Administratorima je omogućeno brisanje korisnika. Ako korisnik ima prodate karte, brisanje je samo logičko (korisnik ne treba da se prikazuje u administratorovoj tabeli korisnika, ali mu se i dalje može videti na stranicama prodatih karata za projekcije).
Korisnicima čija se stranica posmatra i administratorima je prikazana tabela kupljenih karata (tog korisnika) sa datumom i vremenom prodaje karte, sortiranu po opadajućem poretku.
Obrisani korisnik ne može da se prijavi.
Izveštavanje
Administratorima je omogućen pristup posebnoj stranici za izveštavanje. Za unet opseg datuma prikazana je tabela svih filmova i za svaki:
1) naziv filma
2) broj projekcija
3) broj prodatih karata
4) ukupnu cenu prodatih karata
U poslednjem redu tabele prikazan je i ukupan broj projekcija, ukupan broj prodatih karata i ukupna cena svih prodatih karata po svim filmovima za odabrani period.


