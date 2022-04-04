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
        Ljudima bi bilo olakšano da vrše popis ili proveravaju brojno stanje knjiga u biblioteci ili prodavnici knjiga
        tako što slikaju i automatski dobiju spisak knjiga na toj slici. Kada bi se rešenje unapredilo i kada bi se radilo
        sa snimkom, ovaj proces bi dodatno bio olakšan.
        Takođe, ako bi postojala aplikacija za naručivanje ili pretragu online knjiga, bilo bi korisno da korisnik uslika
        knjige koje ga zanimaju i da aplikacija pronađe knjige koje su detektovane na slici.

SKUP PODATAKA:
        Problem zahteva da se kreira skup podataka. Ograničićemo skup uslovom da knjige slikamo sa strane (kako bi se svi
        neophodni podaci videli - naslov, autor, izdavač). Na jednoj slici će biti 1 ili više knjiga. Prikupljaćemo podatke
        u lokalnim bibliotekama i izdavačkim kućama da bismo imale raznovrsniji izbor knjiga. Kada istestiramo podatke,
        videćemo da li su rezultati prihvatljivi, a ukoliko ne budu povećaćemo skup podataka.
		- Fotografije su iz fonda odelenja "Đura Daničić" Gradske biblioteke u Novom Sadu, Biblioteke "Branko Radičević" u Derventi
        	i  privatne fotografije nastale radi izrade projekta.

METODOLOGIJA:
        1. Pretprocesiranje slike: prebacivanje u grayscale.
        2. Detekcija knjiga: upotreba hog deskriptora i metode predict iz biblioteke joblib.
        3. Detekcija naslova, autora i izdavača: korišćena je rotacija slika, kao i metode iz biblioteke easyocr.

EVALUACIJA:
        Tačnost sistema je određena dvema vrednostima:
        1. Tačnost određivanja da li ima slika: 88.67%. 
        	sum(predikcija_slike == labela_slike)/br_slika
        	Posmatramo labele za svaku sliku iz test skupa, poredimo vrednost labele (0 ili 1) sa vrednošću predikcije za datu sliku.
        	Na sumu dodamo 1 ukoliko smo za sliku tačno predvideli da li ima knjiga. Na kraju tu vrednost podelimo sa brojem slika. 
        2. Tačnost određivanja reči: 81.2%. 
        	sum(sum(nadjena_rec in lista_reci)/len(lista_reci))/tacne_slike
        	Za sve slike na kojima smo tačno detektovali da ima knjiga proveravamo za svaku reč da li smo je našli na slici, to delimo
        	sa brojem reči na slici i zatim dodajemo sumi za sve slike. Zatim tu sumu delimo brojem dobro labeliranih slika kako bismo 
        	dobile konačnu tačnost.

POKRETANJE:
        Potrebno je uraditi pip install easyocr (i možda pip install "opencv-python-headless<4.3").
        Potrebno je kopirati folder env/Lib/site-packages/joblib u folder env/Lib/site-packages/sklearn/externals.

        Pokrenuti jupyter notebook i zatim projekat.ipynb. 

	- Procene u vremenu su napravljene za računar sa 4 fizička jezgara i 16GB RAM-a.
```
