# DIKU's Instruktorforening

Formålet med DIKU's instruktorforening er at samle og fordele erfaring om at
være instruktor i datalogiske fag. Foreningen vil forsøge at være både en faglig
og en didaktisk hjælp. I praksis vil foreningen bestå af en samling praktiske
erfaringer som ikke henvender sig til enkelte kurser, samt ressourcer som er
nyttige som instruktor for specifikke kurser. Foreningen vil også være en måde
at kommunikere mellem instruktorer på kurser og kan være et kontaktpunkt for
instituttet når der søges instruktorater.

## Eksempler på praktiske erfaringer

### Gem feedback på disken før du uploader

Skriv aldrig dit feedback direkte ind i Absalons feedback-felt. Absalon er ikke
sky for at slette indhold i feedback-tekstfelter, hvis den beslutter sig for at
du ikke er logget ind længere.

Gem i stedet feedback i en eller flere tekstfiler, hvor du enten uploader
enkelte tekstfiler til hver person eller copy-paster afsnit ind i Absalons
feedback-tekstfelt.

Et godt værktøj som nogle bruger er Emacs org-mode, da man kan lave punktlister
som kan kollapses så man kun kigger på en enkelt sektion af gangen. Et lignende
miljø kan opnås med Vim og "foldning".

### Ret folks opgaver efter deres sandsynlighed for genaflevering

Ved første obligatoriske opgave, så ret folk alfabetisk. Men ved anden
obligatoriske opgave, så sortér folk efter hvem som skulle genaflevere den
første. Det giver dem som har mest brug for det mere tid til genafleveringen.
Ved efterfølgende afleveringer kan man vælge, hvor langt man vil se tilbage,
eller om man bare vil bruge sin erindring om hvem som har mest brug for tidlig
respons.

### Formulering af feedback

For at gøre det nemmere både at lave og rette genafleveringer, er det en fordel
at formulere en punktliste af ting som skal virke ved genaflevering før den
bliver godkendt. Det giver en praktisk, afgrænset plan til den studerende, og
det fremhæver, når genafleveringer ikke kræver at alting er perfekt, hvad der er
det vigtigste. Indsatsen for beståelse afhænger naturligvis af rammerne for den
enkelte opgave. Og det gør rettelsen af genafleveringer meget mekanisk.

Et eksempel på feedback:

    Du må gerne genaflevere med minimum følgende rettelser:
     - Husk at kalde din fil for det rigtige.
     - Fiks to ud af tre af 4I3, 4I4 og 4I5. Se hints nedenfor.
    
    4I1: Ok.
    
    4I2: Ok. Du kunne også lægge 1 til Int.max(x, y) i stedet.
    
    4I3: Ikke ok.
     - Ordenen for en knude er aldrig lig summen af ordenerne for dens børn.
       Opgaveformuleringen er en smule næsvis her: "Hvis en knudes børn har samme
       orden, er knudens orden 1 plus ordenen af børnene." -- Man fristes til at tro
       at det betyder "plus summen af ordenen af børnene", men det betyder egentlig
       "plus den orden som børnene har til fælles".
     - Lad være med at pattern matche så dybt. Det er nok at følge følgende mønster:
    <pre>
    fun order (LEAF _) = 1
      | order (NODE (left, right)) =
        let val ...
        in if ...
        end
    </pre>
    
    4I4: Ikke ok.
     - balanced (LEAF _) burde give true.
     - Du forklarer ikke din strategi eller hvorfor den er berettiget.
     - Det ligner at du har forsøgt at lave en global tællevariabel. Det er en skidt
       idé når vi bruger rekursion i stedet for iteration. Her er i stedet en måde
       du kan forsøge at løse den på:
    
    Hint:
    
    For at et træ kan være balanceret, er det nødvendigt at tjekke at to undertræer
    har samme "størrelse" (i en eller anden forstand) samt at dets undertræer også
    er balancerede.
    
    Dette træ er balanceret:
    <pre>
          KNUDE
          /   \
      KNUDE   KNUDE
      /   \   /   \
    </pre>
    
    Disse træer er for eksempel ikke balancerede:
    <pre>
               KNUDE                        KNUDE
               /   \                       /     \
           KNUDE   KNUDE              KNUDE       KNUDE
           /   \   /   \              /   \       /   \
       KNUDE           KNUDE      KNUDE   KNUDE
       /   \           /   \      /   \   /   \
    </pre>
    
    Det er altså ikke nok at tjekke om to træer har samme højde eller orden, da det
    kan være sandt uden at de er balancerede (eksemplet til venstre). Og det er ikke
    nok at tjekke om alle undertræer er balancerede, da det kan være sandt uden at
    venstre og højre undertræ er "lige store" (eksemplet til højre). Men man kunne
    tjekke at begge ting galdt.
    
    4I5: Halvfærdig. Her er et generelt hint til denne:
    
    For at lave replaceMax skal man egentlig gøre to ting:
     1) Finde det største element
     2) Erstatte alle andre elementer med det
    
    Lav derfor to hjælpefunktioner, en <tt>findMax : int binTree -&gt; int</tt> og en
    <tt>replace : int binTree * int -&gt; int binTree</tt>.  Da kan man finde det største
    tal i et givet træ og dernæst indsætte dette tal i funktionen replace. Begge funktioner
    skal være rekursive og rekursere hen over træet. Men findMax må gerne "nedbryde" træet
    da den kun skal finde et tal som svar, mens replace faktisk skal returnere et træ med
    præcis samme struktur, bare hvor alle blade får erstattet deres bladværdi med maxværdien
    som replace har fået med som argument.
