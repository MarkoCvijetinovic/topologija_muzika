# Primena u neuralnim mrežama za analizu muzičkih audio signala
## Uvod
Ovaj projekat istražuje primenu **topološke perzistencije** u analizi muzičkih audio signala, sa ciljem izdvajanja globalnih strukturnih informacija iz audio reprezentacija koje nisu lako uočljive standardnim konvolucionim pristupima.

Korišćenjem **persistentne homologije** nad mel-spektrogramima, analiziraju se topološke osobine signala kroz različite nivoe filtracije (threshold-a). Na taj način se izdvajaju karakteristike kao što su povezane komponente i rupe, koje opisuju strukturu signala na više skala.

Dobijene topološke informacije pružaju stabilan i robusan opis audio signala i predstavljaju osnovu za njihovu potencijalnu integraciju sa konvolucionim neuronskim mrežama.
## Transformacija audio signala
Kao prvi korak, audio zapis se transformiše u log-mel spektrogram. Spektrogram predstavlja dvodimenzionalni prikaz signala u kome horizontalna osa odgovara vremenu, vertikalna frekvenciji, dok intenzitet boje označava energiju signala.

Ovakav prikaz omogućava da audio signal posmatramo kao matricu pogodnu za dalju topološku analizu.

## Filtracija spektrograma i kubični kompleksi

Nakon formiranja log-mel spektrograma, nad njim se definiše proces filtracije u cilju analize topološke strukture signala na različitim nivoima.

Spektrogram se može posmatrati kao diskretna 2D funkcija definisana na mreži piksela, gde svaki piksel predstavlja jednu ćeliju kubičnog kompleksa sa pridruženom vrednošću intenziteta.

Uvođenjem praga (threshold-a), formira se niz podskupova spektrograma:
- za svaku vrednost praga posmatra se skup piksela čije su vrednosti iznad tog praga
- menjanjem praga dobija se filtracija koja menja topologiju posmatranog prostora

Tokom ovog procesa prate se osnovne topološke karakteristike:
- β₀ – broj povezanih komponenti
- β₁ – broj rupa

Ove veličine omogućavaju analizu globalne strukture spektrograma kroz različite nivoe filtracije.

## Persistentna homologija

Persistentna homologija omogućava praćenje evolucije topoloških karakteristika kroz celu filtraciju.
Umesto posmatranja strukture za jedan fiksni prag, analizira se kako se topološke osobine pojavljuju i nestaju kako se prag menja.
Svaka topološka osobina se opisuje kroz:
- trenutak nastanka (birth)
- trenutak nestanka (death)
Na osnovu toga se formira persistence dijagram koji predstavlja sažet prikaz stabilnih i nestabilnih struktura u signalu.
## Persistence dijagrami
Persistence dijagrami predstavljaju skup tačaka u 2D prostoru, gde svaka tačka odgovara jednoj topološkoj osobini.
- Osobine koje su blizu dijagonale predstavljaju kratkotrajne strukture (šum)
- Osobine koje su udaljene od dijagonale predstavljaju stabilne strukture

Na ovaj način persistence dijagram daje kompaktan opis topološke strukture audio signala kroz više skala.
## Persistence landscapes
Kako bi se informacije iz persistence dijagrama mogle koristiti u modelima mašinskog učenja, potrebno ih je transformisati u vektorski oblik.
U ovom radu koriste se persistence landscapes, koje transformišu persistence dijagrame u numeričke vektore fiksne dimenzije.
Ova reprezentacija omogućava direktnu integraciju topoloških informacija u neuronske mreže.
Persistentna homologija upravo dopunjuje ovaj nedostatak jer hvata robusne topološke karakteristike koje su invarijantne na lokalne perturbacije.
Zbog toga kombinacija CNN i topoloških karakteristika predstavlja komplementaran pristup koji poboljšava reprezentaciju audio signala za zadatke klasifikacije.
