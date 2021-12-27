# Soft kompjuting na SIIT-u
```
TIM:
        Milica Đumić, sw-27-2018
        Tatjana Gavrilović, sw-53-2018

ASISTENT:
        Dragan Vidaković

DEFINICIJA PROBLEMA:
        Detekcija knjiga na slici i detekcija naslova, autora i izdavača knjige.

MOTIVACIJA PROBLEMA:
        Ljudima bi bilo olakšano da vrše popis ili proveravaju brojno stanje knjiga u biblioteci ili prodavnici knjiga tako što slikaju i automatski dobiju spisak knjiga na toj slici. Kada bi se rešenje unapredilo i kada bi se radilo sa snimkom, ovaj proces bi dodatno bio olakšan.
        Takođe, ako bi postojala aplikacija za naručivanje ili pretragu online knjiga, bilo bi korisno da korisnik uslika knjige koje ga zanimaju i da aplikacija pronađe knjige koje su detektovane na slici.

SKUP PODATAKA:
        Problem zahteva da se kreira skup podataka. Ograničićemo skup uslovom da knjige slikamo sa strane (kako bi se svi neophodni podaci videli - naslov, autor, izdavač). Na jednoj slici će biti 1 ili više knjiga. Prikupljaćemo podatke u lokalnim bibliotekama i izdavačkim kućama da bismo imale raznovrsniji izbor knjiga. Kada istestiramo podatke, videćemo da li su rezultati prihvatljivi, a ukoliko ne budu povećaćemo skup podataka.

METODOLOGIJA:
        1. Pretprocesiranje slike: morfološte operacije (erozija, dilacija), prebacivanje u grayscale i potencijalno korišćenje adaptivnog threshold-a.
        2. Detekcija knjiga: pronalaženje kontura (pravougaonika). U slučaju da ova metoda ne bude davala zadovoljavajuće rezultate ukoliko budemo u mogućnosti možemo probati da implamentiramo Hough transformacije.
        3. Detekcija naslova, autora i izdavača: koristiće se ocr za detekciju slova. Takođe, iz razloga što su slova često različito okrenuta, moguće je da će se u ovom koraku raditi i rotacija slike. Ukoliko bude potrebe, radićemo detekciju celina kako bismo izdvojile odgovarajuće delove (naslov, autora i izdavača).

EVALUACIJA:
        Upoređivaćemo labele koje smo dodelili svakoj slici iz skupa podataka sa tim što smo dobile kao rezultat. Za svaku sliku ćemo odrediti koliko knjiga je detektovano – to će biti 1 bod ukoliko su sve zamišljene knjige i pronađene. Takođe za sve pravilno detektovane naslove, autore i izdavače ćemo dodeliti 1 bod. Kada sumiramo sve bodove podelićemo to sa brojem slika puta 2 i pomnožiti sa 100 kako bismo dobile procentualnu tačnost.
        sum((br_detektovanih_knjiga/tacan_br_knjiga)+sum(isti_naslov+isti_autor+isti_izdavac)/(3 * tacan_br_knjiga))*100/(2 * br_slika)
```
