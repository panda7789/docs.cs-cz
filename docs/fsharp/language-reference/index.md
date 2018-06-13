---
title: Referenční dokumentace jazyka F#
description: 'Najdete F # jazykové funkce informace z tohoto odkazu na tokeny jazyka, koncepty, typy, výrazy a témata týkající se podporovaných kompilátoru konstrukce.'
ms.date: 05/16/2016
ms.openlocfilehash: 1c25ab4a4936b532a21aed8b2b0202fec1dd7133
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33566688"
---
# <a name="f-language-reference"></a>Referenční dokumentace jazyka F#

Tato část se odkaz na F # jazyka, více zlepší programovací jazyk cílení na rozhraní .NET. Jazyk F # podporuje funkční, objektově orientovaný a imperativní programovací modely.


## <a name="f-tokens"></a>F # tokeny
V následující tabulce jsou uvedeny referenční témata, které poskytují tabulky klíčová slova, značky a literály použít jako tokeny v jazyce F #.



|Název|Popis|
|-----|-----------|
|[Referenční dokumentace klíčových slov](keyword-reference.md)|Obsahuje odkazy na informace o všech klíčových jazyka F #.|
|[Referenční dokumentace symbolů a operátorů](symbol-and-operator-reference/index.md)|Obsahuje tabulku symbolů a operátory, které se používají v jazyce F #.|
|[Literály](literals.md)|Popisuje syntaxe literálových hodnot v F # a jak určit informace o typu pro literály F #.|

## <a name="f-language-concepts"></a>Koncepty jazyka F #
V následující tabulce jsou uvedeny referenční témata, které jsou k dispozici, které popisují – jazykové koncepty.



|Název|Popis|
|-----|-----------|
|[Funkce](functions/index.md)|Funkce jsou základní jednotkou spouštění programu v žádný programovací jazyk. Funkce F # jako v jiných jazycích, má název, může mít parametry a argumenty proveďte a má text. F # podporuje také funkční programovací konstrukce, jako je například replikace funkce jako hodnoty, pomocí nepojmenované funkcí na výrazy, složení funkcí k vytvoření nové funkce, curryfikované funkce a implicitní definici funkce prostřednictvím s částečným aplikace argumenty funkce.|
|[Typy F#](fsharp-types.md)|Popisuje typy, které se používají v F # a jak jsou s názvem a popsané typů F #.|
|[Odvození typu](type-inference.md)|Popisuje, jak kompilátor jazyka F # odvodí typy hodnot, proměnné, parametry a návratové hodnoty.|
|[Automatická generalizace](generics/automatic-generalization.md)|Popisuje obecné konstrukce v F #.|
|[Dědičnost](inheritance.md)|Popisuje dědičnosti, který se používá pro modelování vztahů "je a", nebo vytvoření podtypů v objektově orientované programování.|
|[Členové](members/index.md)|Popisuje členy typy objektů F #.|
|[Parametry a argumenty ](Parameters-and-Arguments.md)|Popisuje jazyková podpora pro definování parametry a předání argumentů do funkce, metod a vlastností. Obsahuje informace o tom, jak předat odkazem.|
|[Přetížení operátoru](operator-overloading.md)|Popisuje, jak přetížení aritmetické operátory ve třídě nebo typ záznamu a na globální úrovni.|
|[Přetypování a převody](casting-and-conversions.md)|Popisuje podporu pro převody typů v jazyce F #.|
|[Řízení přístupu](access-control.md)|Popisuje řízení přístupu v jazyce F #. Řízení přístupu znamená deklarace klientů, kteří jsou schopné používat určité prvky programu, například typy, metody, funkce a tak dále.|
|[Porovnávání vzorů](pattern-matching.md)|Popisuje vzorů, které jsou pravidla pro transformaci vstupní data, která se používají v rámci jazyk F # pro rozbalení porovnání dat pomocí vzoru, rozloží data na základní části nebo extrahovat informace z dat různými způsoby.|
|[Aktivní vzory](active-patterns.md)|Popisuje aktivní vzorky. Aktivní vzorky umožňují definovat pojmenované oddíly, které rozdělit vstupní data. Aktivní vzorky můžete rozložit data způsobem přizpůsobené pro každý oddíl.|
|[Kontrolní výrazy](assertions.md)|Popisuje `assert` výraz, který je ladění funkce, která můžete použít k otestování výrazu. Kontrolní výrazy při selhání v režimu ladění, generuje dialogové okno chyby systému.|
|[Zpracování výjimek](exception-handling/index.md)|Obsahuje informace o zpracování podpory v jazyce F # výjimek.|
|[Atributy](attributes.md)|Popisuje atributy, které umožňují metadata, která má být použita pro programovací konstrukce.|
|[Správa prostředků: `use` – klíčové slovo](resource-management-the-use-keyword.md)|Popisuje klíčová slova `use` a `using`, které můžete ovládat inicializace a verzi zdroje|
|[obory názvů](namespaces.md)|Popisuje podporu oboru názvů v jazyce F #. Obor názvů umožňuje uspořádat kódu do oblasti související funkce tím, že vám k seskupení prvků programu připojit název.|
|[Moduly](modules.md)|Popisuje moduly. Modul F # je seskupení F # kódu, například hodnoty, typy a hodnoty funkce v programu F #. Kód v modulech seskupení vám pomůže uchovávat související kód společně a pomáhá zabránit název je v konfliktu v programu.|
|[Deklarace importu: `open` – klíčové slovo](import-declarations-the-open-keyword.md)|Popisuje, jak `open` funguje. Deklarace importu určuje modulu nebo obor názvů, jehož elementy bez použití plně kvalifikovaný název, můžete odkazovat.|
|[Signatury](signatures.md)|Popisuje podpisy a soubory podpisu. Soubor podpis obsahuje informace o veřejné podpisy sadu F # program prvky, jako jsou například moduly, obory názvů a typy. Slouží k určení usnadnění z těchto elementů programu.|
|[Dokumentace XML](xml-documentation.md)|Popisuje podporu pro generování soubory dokumentace pro komentáře doc XML, také známé jako Trojitá lomítko komentáře. Může vytvářet dokumentace z komentáře kódu v jazyce F # jako v případě jinými jazyky rozhraní .NET.|
|[Podrobná syntaxe](verbose-syntax.md)|Popisuje syntaxi pro F # konstrukce, není-li povoleno prostá syntaxe. Podrobná syntaxe je indikován `#light "off"` direktivy v horní části souboru kódu.|

## <a name="f-types"></a>Typy F#
V následující tabulce jsou k dispozici referenční témata, které popisují typy podporované systémem jazyk F #.



|Název|Popis|
|-----|-----------|
|[Hodnoty](values/index.md)|Popisuje hodnoty, které jsou neměnné množství, které mají určitý typ; hodnoty může být nedílnou nebo plovoucí desetinnou čárkou, znaků nebo text, seznamy, pořadí, pole, řazené kolekce členů, rozlišovaná sjednocení, záznamy, typy tříd nebo hodnoty funkce.|
|[Primitivní typy](primitive-types.md)|Popisuje základní primitivní typy, které se používají v jazyce F #. Poskytuje taky odpovídající typy .NET a minimální a maximální hodnoty pro každý typ.|
|[Typ jednotky](unit-type.md)|Popisuje `unit` typu, který je typem, který ukazuje na nepřítomnost konkrétní hodnotu `unit` typ má pouze jednu hodnotu, která funguje jako zástupný znak, pokud jiná hodnota existuje nebo je potřeba.|
|[Řetězce](strings.md)|Popisuje řetězce v jazyce F #. `string` Typ představuje neměnné text jako posloupnosti znaků Unicode. `string` je alias `System.String` v rozhraní .NET Framework.|
|[Řazené kolekce členů](tuples.md)|Popisuje řazené kolekce členů, které jsou seskupení nepojmenované ale seřazené hodnoty pravděpodobně různých typů.|
|[Typy kolekcí F#](fsharp-collection-types.md)|Přehled typů F # funkční kolekcí, včetně typů pro pole, seznamy, pořadí (seq), mapy a sad.|
|[Seznamy](lists.md)|Popisuje seznamy. Seznam v F # je seřazený, neměnné řadu elementy všechny stejného typu.|
|[Možnosti](options.md)|Popisuje typ možnosti. Možnost v F # se používá, pokud hodnota může nebo nemusí existovat. Možnost má základní typ a může buď sdílet hodnotu daného typu nebo ho nesmí mít hodnotu.|
|[Sekvence](sequences.md)|Popisuje pořadí. Posloupnost je logické řadu elementy všechny jednoho typu. Pořadí jednotlivých elementů se vypočítávají v případě potřeby pouze v tak reprezentace může být nižší než počet literál elementu označuje.|
|[Pole](arrays.md)|Popisuje pole. Pole jsou pevné velikosti, počítáno od nuly, měnitelný posloupnosti po sobě jdoucích datové prvky, všechny stejného typu.|
|[Záznamy](records.md)|Popisuje záznamy. Záznamy představují jednoduché agregace pojmenovaných hodnot, případně se členy.|
|[Rozlišovaná sjednocení](discriminated-unions.md)|Popisuje rozlišovaná sjednocení, která poskytuje podporu pro hodnoty, které může být jeden z různých případech, s názvem, každý s typy a které by mohly mít odlišné hodnoty.|
|[Výčty](enumerations.md)|Popisuje výčty jsou pojmenované typy, které mají definovanou sadu hodnot. Můžete je používat místo literály, aby kód víc čitelný a udržovatelný.|
|[Referenční buňky](reference-cells.md)|Popisuje referenční buňky, které jsou umístění úložiště, které vám umožní vytvářet měnitelný proměnné s sémantiku odkaz.|
|[Zkratky typů](type-abbreviations.md)|Popisuje zkratky typů, které jsou alternativní názvy typů.|
|[Třídy](classes.md)|Popisuje třídy, které jsou typy, které představují objekty, které mohou mít vlastnosti, metod a události.|
|[Struktury](structures.md)|Popisuje, struktury, které jsou typy compact objektů, které může být efektivnější než třída pro typy, které mají malé množství dat a jednoduché chování.|
|[Rozhraní](interfaces.md)|Popisuje rozhraní, které určují sady souvisejících členů, které implementují jiné třídy.|
|[Abstraktní třídy](abstract-classes.md)|Popisuje abstraktní třídy, které jsou třídy, která opouští některé nebo všechny členy Neimplementovaný, tak, aby implementace lze zadat odvozené třídy.|
|[Rozšíření typů](type-extensions.md)|Popisuje typ rozšíření, které umožňuje přidat nové členy do typu dříve definovaném objektu.|
|[Flexibilní typy](flexible-types.md)|Popisuje flexibilní typy. Flexibilní typ poznámky je zadán jako ukazatel toho, že parametr, proměnné nebo hodnota má typ, který je kompatibilní s typem, kde je určen kompatibility pozici v hierarchii objektově orientované třídy nebo rozhraní.|
|[Delegáti](delegates.md)|Popisuje delegáti, které představují volání funkce jako objekt.|
|[Měrné jednotky](units-of-measure.md)|Popisuje měrné jednotky. Plovoucí hodnoty bodu v jazyce F # může mít přidružené jednotky míry, které jsou obvykle používány k označení délka, svazek, velkokapacitních a tak dále.|
|[Zprostředkovatelé typů](../tutorials/type-providers/index.md)|Popisuje typ poskytuje a poskytuje odkazy na postupy týkající se použití předdefinovaný typ zprostředkovatele pro přístup k databázím a webové služby.|

## <a name="f-expressions"></a>F # výrazy
Následující tabulka uvádí témata, která popisují F # výrazy.

|Název|Popis|
|-----|-----------|
|[Podmíněné výrazy: `if...then...else`](conditional-expressions-if-then-else.md)|Popisuje `if...then...else` výraz, který běží jiné větví kódu a také vyhodnocuje na jinou hodnotu, v závislosti na logický výraz zadaný.|
|[Výrazy shody](match-expressions.md)|Popisuje `match` výraz, který poskytuje větvení ovládací prvek, který je založena na porovnávání výrazu sadu vzory.|
|[Smyčky: `for...to` výraz](loops-for-to-expression.md)|Popisuje `for...to` výraz, který se používá k iterace ve smyčce v rozsahu hodnot proměnné smyčky.|
|[Smyčky: `for...in` výraz](loops-for-in-expression.md)|Popisuje `for...in` výrazu, opakování konstruktor, který se používá k iteraci nad na odpovídá vzoru v kolekci vyčíslitelná například výraz rozsahu, pořadí, seznam, pole nebo jiné konstruktor, který podporuje výčtu.|
|[Smyčky: `while...do` výraz](loops-while-do-expression.md)|Popisuje `while...do` výraz, který se používá k provádění iterativní provádění (opakování ve smyčce), když je splněna podmínka zadaný testovací.|
|[Objektové výrazy](object-expressions.md)|Popisuje objektové výrazy, které jsou výrazy, které vytvářejí nové instance typu dynamicky vytvořený, anonymní objekt, který je založen na existující základní typ, rozhraní nebo sadu rozhraní.|
|[Opožděné výpočty](lazy-computations.md)|Popisuje opožděné výpočty, které jsou výpočty, které se nevyhodnotily okamžitě, ale místo toho vyhodnocují při výsledek je skutečně potřeba.|
|[Výpočetní výrazy](computation-expressions.md)|Popisuje výpočetní výrazy v jazyce F #, které poskytují pohodlný syntaxe pro zápis výpočtů, u kterých může být sekvencování a spojovat pomocí konstrukce toku řízení a vazeb. Slouží k poskytování vhodné syntaxe pro *monads*, funkční programovací funkce, která slouží ke správě dat, řízení a vedlejší efekty při funkční programy. Jeden typ výpočetní výraz asynchronní pracovní postup, poskytuje podporu pro asynchronní a paralelní výpočty. Další informace najdete v tématu [asynchronní pracovní postupy](asynchronous-workflows.md).|
|[Asynchronní pracovní postupy](asynchronous-workflows.md)|Asynchronní pracovní postupy, popisuje funkce jazyka, která umožňuje zapisovat, že asynchronní kód tak, že je velmi brzy bude dosaženo způsob, jakým jste přirozeně zapíše synchronní kódu.|
|[Citace kódu](code-quotations.md)|Popisuje uvozovky kódu jazyka funkce, která umožňuje generovat a pracovat s výrazy kódu F # prostřednictvím kódu programu.|
|[Výrazy dotazu](query-expressions.md)|Výrazy dotazů, popisuje funkce jazyka, která implementuje LINQ pro F # a umožňuje psát dotazy na zdroj dat nebo výčtové kolekce.|

## <a name="compiler-supported-constructs"></a>Podporované kompilátoru konstrukce
Následující tabulka uvádí témata, která popisují speciální konstrukce kompilátoru podporována.

|Téma|Popis|
|-----|-----------|
|[Možnosti kompilátoru](compiler-options.md)|Popisuje možnosti příkazového řádku pro kompilátor jazyka F #.|
|[Direktivy kompilátoru](compiler-directives.md)|Popisuje direktivy procesoru a direktivy kompilátoru.|
|[Identifikátory zdrojového řádku, souboru a cesty](source-line-file-path-identifiers.md)|Popisuje identifikátorů `__LINE__`, `__SOURCE_DIRECTORY__` a `__SOURCE_FILE__`, které jsou předdefinované hodnoty, které vám umožní přístup k zdroj řádku číslo, adresář a název souboru ve svém kódu.|

## <a name="see-also"></a>Viz také
[Visual F#](../index.md)
