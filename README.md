# Algoritmer og datastrukturer - Oblig2

## Oppgave 1
I konstruktøren public DobbeltLenketListe() har jeg laget en tom dobbeltlenket liste, ved å sette hode og hale til null, og antall og endringer til 0.
I konstruktøren public DobbeltLenketListe(T[] a) har jeg laget en dobbeltlenket liste fra arrayet a, uten null-verdier. Går gjennom arrayet med en for-løkke, og hvis verdien ikke er lik null, legges den inn i lista med metoden leggTil(). Metoden leggTil() oppretter en ny node for hver verdi. Dersom lista er tom fra før, settes hode og hale til den nye noden. Dersom lista har noder fra før, settes nåværende halens neste-peker til den nye noden, den nye nodens forrige-peker settes til nåværende hale, og til slutt flyttes hale-pekeren til den nye noden.
I public int antall() returneres bare antallet.
I public boolean tom() returnerer true hvis lista er tom, dvs. antall er lik 0.

## Oppgave 2
I public String toString() returnerer en tegnstreng med listens verdier. Bruker en StringBuilder for å bygge opp strengen. Starter strengen med '[' , og legger til noden som hode peker på. Så går man gjennom resten av nodene i lista med en while-løkke. Da legges først ', ' til, for deretter å legge til verdien i noden. Dermed blir det ikke komma etter den siste verdien er lagt til. Så avsluttes strengen med klammeparantes. Til slutt gjøres StringBuilderen om til String og returnerer denne.
I public String omvendtString() har jeg gjort akkurat det samme, men motsatt vei. Da har jeg bare byttet ut hode med hale, dvs. den starter bakerst, og bruker forrige-pekerne i stedet for neste-pekerne.
I public boolean leggInn(T verdi) legges en nye noder med verdi inn bakerst i lista, så lenge den ikke er null. Hvis lista er tom fra før, opprettes en ny node som blir både hode og hale, og pekerne settes til null. Hvis det er noder i lista fra før, legges ny node bakerst, halen settes til å peke på den nye noden, og den nye nodens forrige-peker til nåværende hale. Dvs. noden før. Returnerer true hvis innsettingen var vellykket.

## Oppgave 3
I metoden private Node finnNode(int indeks) har jeg laget en metode for å finne en node med en gitt indeks. Metoden starter med å sette en variabel kalt nåværendeNode, som passer på referansen til noden. Har en if-test som sjekker om indeksen som sendes inn er mindre enn halvparten av antallet. Setter nåværendeNode til å være hodet, og deretter går gjennom lista med en for-løkke fra starten og utover. Så flyttes nåværendeNode til å være nåværendeNode.neste osv. I else, altså hvis indeksen er større eller lik halvparten av antallet, settes nåværendeNode til å være halen. Så går gjennom lista med en for-løkke, men man går bakover i lista. NåværendeNode flyttes derfor via forrige-peker. Til slutt returneres noden som er funnet på indeksen.

I metoden public T hent(int indeks) hentes en verdi ut, som har en gitt indeks. Den sjekker først at indeksen er gyldig, med metoden indeksKontroll. Deretter brukes finnNode-metoden for å finne den noden som står på den aktuelle indeksen. Returnerer deretter nodens verdi.

I metoden public T oppdater(int indeks, T nyverdi) oppdaterer eller erstattes en verdi på en gitt indeks. Sjekker først om nyverdi er null, og kaster en NullPointerException hvis den er det. Så bruker jeg metoden indeksKontroll for å sjekke at indeksen er gyldig. Så brukes finnNode-metoden for å finne noden på den aktuelle indeksen. Så lagres verdien til denne noden som gammelVerdi. Deretter oppdaterer verdien til noden til den nye verdien, og til slutt returneres den gamle verdien.

I metoden public Liste subliste(int fra, int til) returneres en ny liste med verdier fra det halvåpne intervallet [fra, til>. Starter med en fraTilKontroll for å sjekke om indeksene er lovlige. Deretter opprettes en ny dobbeltlenket liste. If-testen sjekker så om intervallet er tomt, og returnerer i så fall en tom liste. Deretter brukes finnNode-metoden for å finne startnoden, altså fra. Så går man gjennom intervallet med en for-løkke, og bruker leggTil-metoden for å legge til verdiene i den nye lista. Til slutt returnerer den den nye lista.

## Oppgave 4
I metoden public int indeksTil(T verdi) brukes en for-løkke for å gå gjennom nodene i lista. Så brukes equals() for å sjekke om verdien i nåværende node er lik verdien som letes etter, og returnerer indeksen hvis det er riktig. Ellers flyttes pekeren til neste node. Dersom verdien ikke finnes i lista returneres -1.
I metoden public boolean inneholder(T verdi) brukes indeksTil-metoden for å finne ut om verdien finnes i lista. Hvis den gjør det, returneres true, hvis ikke returneres false.

## Oppgave 5
I metoden public void leggInn(int indeks, T verdi) bruker jeg if og else for å finne ut om indeksen er 0, da skal verdien legges inn først, dersom indeksen er lik antall, skal verdien bakerst og ellers skal den legges et sted midt i lista. Har derfor laget tre hjelpemetoder; leggInnFørst, leggInnSist og leggInnMidten.
leggInnFørst(T verdi): Hvis lista er tom, settes hode og hale til den nye noden. Hvis ikke, lages ny node med neste-peker på hode, setter hode til å være den nye noden.
leggInnSist(T verdi): Hvis lista er tom, settes hode og hale til den nye noden. Hvis ikke, lages ny node med forrige-peker på hale, og setter halen til å være den nye noden.
leggInnMidten(int indeks, T verdi): For-løkke går gjennom lista frem til noden på indeks - 1. Den nye noden plasseres mellom denne noden og den neste.

## Oppgave 6
I metoden public T fjern(int indeks) finner jeg noden som skal fjernes med finnNode-metoden. Så noden før og etter, og sender inn disse til hjelpemetoden fjernNode.
I hjelpemetoden fjernNode(Node p, Node q, Node r) sjekkes det først at p ikke er null, i såfall flyttes p sin neste-peker til r. Hvis p er null (dvs. noden som fjernes er først), settes hode til å peke på r. Sjekker så at r ikke er null, flytter i såfall r sin forrige-peker til p. Hvis r er null (dvs. q er siste node) settes hale til å peke på p. Så hentes verdien til noden som fjernes, pekerne settes til null, og denne returneres.
I metoden public boolean fjern(T verdi) går man gjennom lista med en while-løkke, til man finner verdien som tilsvarer verdien man leter etter. Da sendes denne, noden før og etter til hjelpemetoden fjernNode. Returnerer true hvis det går fint, og false hvis man ikke finner verdien i lista.

## Oppgave 8
public Iterator iterator() returnerer en instans av iteratoren, starter fra starten.
public Iterator iterator(int indeks) returnerer en instans av iteratoren, som starter ved aktuell indeks.
private DobbeltLenketListeIterator(int indeks) er en konstruktør som starter iteratoren ved aktuell indeks. Finner noden til indeksen, lagrer antallet endringer og setter kanFjerne til false.
public T next() sjekker først at iteratorendringer er lik endringer, og sjekker om det er flere elementer igjen i lista. Henter verdien til nåværende node og setter til "denne", flytter "denne" til neste node. Setter kanFjerne lik true, og returnerer verdien til nåværende node.
