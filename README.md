# rock-paper-scissors

Egy kő-papír-olló játékot fogunk lekódolni, amiben a felhasználó a gép ellen játszik.

Gondold át, milyen osztálystruktúrára és endpointokra lesz szükséged! Hogy fog kinézni a frontend?
Mikor mi fog kiíratódni, mit fog a felhasználó beírni?

Ha körvonalazódott, megnézheted a `res` mappa tartalmát, valami ilyesmire kell számítani!


# Project Setup

Készíts a Sprint Initializr segítségével egy új projektet rock-paper-scissors néven!
A szokásos beállításokat használd (Type: Maven, Group: hu.progmatic), 
majd a Next gomra kattintás után add hozzá az alábbi 3 dependenciát:

- Developer Tools: Spring Boot DevTools
- Web: Spring Web
- Template Enginges: Thymeleaf

# GameController

A játékunk vezérléséért ez az osztály felelős. Készíts egy `controller` package-et és ebbe tedd
a vezérlésért felelős osztályokat!

## Home Page

Készíts egy `GameController` osztályt a `controller` package-ben és lásd el `@Controller` annotációval!
Vegyél fel bele egy `@GetMapping("/")` annotációval ellátott metódust, ami egy home page-et ad vissza!
```
 @GetMapping("/")
 public String home() {
     return "homePage";
 }
```
Készítsd el ezt a `.html` fájlt, ami kiír egy üdvözlőszöveget,
konvenció szerint tedd a `resources/templates` mappába!

Teszteld le, hogy (az appilikáció futása közben) a `localhost:8080/`-t megnyitva megjelnik a főoldal!

## GameService

A játékunk logikájáért ez az osztály felelős.
Készíts egy `service` package-et és ebbe kerüljenek a logikáért felelős osztályok!

## Interfészhez tervezés
Próbálj most meg nagyvonalakban gondolkozni, ne a konkrét implementáción gondolkodj!
Milyen metódusokra lenne szükséged egy kő-papír-olló játék levezényléséhez?
Mi az ami midenképp kell? Milyen metódusokat szeretnél használni a `GameController`-ben?
Mit szeretnél majd megejeleníteni?

- Beolvasás a felhasználótól, hogy mit választ?
- Lekérdezés, hogy a kő üti-e a paraméterként kapott elemet?
- Kiíratás, hogy éppen mi történik?
- Enumok, amik eltárolják a válaszokat?
- Metódus, ami paraméterként kapja, hogy a számítógép mit választott, a játékos mit választott és
kiírja, hogy ki nyert?
- Ki szeretnéd írni, hogy a gép mit választott?

Itt tényleg állj meg és gondold át, mire lesz szükség, írtam az opciók közé tök nagy marhaságokat is, szívesen! ;)
Most egy interfészt írunk, tehát csak metódusokat kell felvenned implementáció nélkül!

Készítsd el ezt az interfészt `GameSerice` néven!

## Játék logika
Amint elkészültél az interfésszel, készíts egy azt megvalósító osztályt (tehát ne felejts le az `implements` kulcsszót)
`BasicGameService` néven, `@Service` annotációval ellátva és valósítsd meg a metódusokat! Természetesen segédmetódusokat felvehetesz az interfészben
definiáltak mellé.

# GameController
Ugrjunk vissza a `controller` package-be!

## Play endpoint
Vegyél fel a `GameController` osztályban a játék lebonyolításáért felelős metódus(ok)at!
Ehhez szükség lesz a service osztály(ok) beinjektálására!

```
private final GameService basicGameService;

@Autowired
public GameController(
   GameService basicGameService){
    this.basicGameService = basicGameService;
}
```


Készítsd el hozzá a `.html` fájlokat!

# Haladó feladatok

Ha kész vagy, szépítheted a kódodat, pl. ezekkel:

## Frontend
Bootstrapet neki!

## Új logika implementáció
Készíts egy új osztályt, ami a `GameLogic` interfészt valósítja meg:

```
@Service("extraGameService")
public class ExtraGameService extends GameService {
```
Ennek a mintájára írd át a meglévő service-t is! (Az annotáció után adj neki nevet.)
Honnan fogja most tudni a Spring, hogy a controllerbe melyiket injektálja be?
Nézz utána a `@Qualifier`-nek és használd!