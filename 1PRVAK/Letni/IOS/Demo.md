# Demo 5.5.2017

## Zadání

1. Jaký je maximální počet TLB miss u instrukce o délce 4B, která čte 4B z paměti? Jaký je tento počet v případě přesunu 4B v paměti? Jak se toto maximum změní, víme-li, že se jedná o instrukci, která v kódu lineárně následuje za aktuálně prováděnou instrukcí? … A pro práci s daty délky 1B?
1. Jaký je maximální počet přístupů do paměti při použití čtyřúrovňové tabulky stránek u instrukce o délce 4B přistupující pro 4B do paměti (čtení nebo zápis)? Jak se tento počet změní v případě přesunu v paměti? Jak se toto maximum změní, víme-li, že se jedná o instrukci, která v kódu lineárně následuje za aktuálně prováděnou instrukcí?
1. _(6b)_ Jaký je maximální počet přístupů do primární paměti RAM při použití N-úrovňové hierarchické tabulky stránek v rámci provedení předem načtené instrukce o délce 4B, která načítá z paměti 4B dat, předpokládáme-li práci se stránkami o velikosti 4KiB. Pro načtení jedné položky jednotlivých dílčích tabulek stránek postačuje jako obvykle jeden přístup do paměti. Odvodněný vztah zdůvodněte. (limity: jeden vztah a cca 3 rozvité věty [ vztah bez zdůvodnění je za 0 bodů ]).
1. _(9b)_ Předpokládejte existenci struktury `struct inv_tb_item` popisující v jazyce C položku invertované tabulky stránek kombinované s použitím hashováním (!). Dále nechť číselný typ `pg_num_t` popisuje čísla stránek a rámců a číselný typ `pid_t` čísla procesů. Dále předpokládejme, že je definovaná funkce `pg_num_t hashPg(pg_num_t pg, pid_t pid)`, která ke stránce číslo pg procesu s číslem pid vrací odkaz (index) do uvažované tabulky stránek. Implementujte v jazyce C funkci pro převod čísla stránky na číslo rámce s prototypem `pg_num_t page_to_frame(struct inv_tb_item *inv_tb, pg_num_t pg, pid_t pid);`. Předpokládejte přitom, že parametr `inv_tb` ukazuje na první položku uvažované tabulky stránek, pid je číslo procesu, který převod provádí, a pg je číslo převáděné stránky. Můžete předpokládat, že všechny číselné položky všech nepoužitých řádků tabulky mají hodnotu NEGATIVE, která neodpovídá žádné stránce, rámci ani procesu. Funkce v případě, kdy je možno dané číslo stránky převést na odpovídající číslo rámce, vrací příslušné číslo rámce. Pokud převod není možno převést, funkce vrací hodnotu NEGATIVE. Pro potřeby implementace funkce `page_to_frame` si doplňte potřebné položky struktury `inv_tb_item` (limity: cca 6 řádků kódu pro tělo funkce bez deklarací a patřičné položky struktury `inv_tb_item`)
1. _(6b)_ Jaký je maximální počet výpadků stránek v systému se stránkami o velikosti 4 KiB, 4-úrovňovou tabulkou stránek, u které pouze dílčí tabulka nejvyšší úrovně je chráněna proti výpadku, při provádění předem nenačtené instrukce o délce 4 B, která přesouvá 8 KiB z jedné adresy paměti na jinou?
1. _(4b)_ Předpokládáme systém s virtuální pamětí, ve které se používá lokální výměna stránek a ve kterém se při výběru odkládané stránky používá algoritmus LRU. Předpokládáme dále, že v tomto systému je spuštěn proces, který má napevno přiděleny 4 rámce, do nichž na začátku není namapována žádná stránka. Ke kolika výpadkům stránky dojde, pokud daný proces postupně přistoupí k následujícím stránkám: 1 2 3 4 4 1 5 2 2 3 5 1.