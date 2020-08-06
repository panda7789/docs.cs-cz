---
title: Referenční dokumentace jazyka
description: 'Najde informace o funkcích jazyka F # z tohoto odkazu na jazykové tokeny, koncepty, typy, výrazy a témata konstrukce podporovaná kompilátorem.'
ms.date: 05/16/2016
ms.openlocfilehash: e8a6c7ef83c4e2d292cc6a12a59e420708240a39
ms.sourcegitcommit: 09bad6ec0cbf18be7cd7f62e77286d305a18b607
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/05/2020
ms.locfileid: "87795473"
---
# <a name="f-language-reference"></a>Referenční dokumentace jazyka F#

Tato část je odkaz na jazyk F #, víceúrovňové programovací jazyk, který cílí na .NET. Jazyk F # podporuje funkční, objektově orientované a imperativní programovací modely.

## <a name="f-tokens"></a>Tokeny F #

V následující tabulce jsou uvedena referenční témata, která poskytují tabulky klíčová slova, symboly a literály používané jako tokeny v jazyce F #.

|Nadpis|Popis|
|-----|-----------|
|[Referenční dokumentace klíčových slov](keyword-reference.md)|Obsahuje odkazy na informace o všech klíčových slovech jazyka F #.|
|[Referenční dokumentace symbolů a operátorů](./symbol-and-operator-reference/index.md)|Obsahuje tabulku symbolů a operátorů, které jsou používány v jazyce F #.|
|[Literály](literals.md)|Popisuje syntaxi pro literálové hodnoty v jazyce F # a určení informací o typu pro literály F #.|

## <a name="f-language-concepts"></a>Jazykové koncepty F #

V následující tabulce jsou uvedena referenční témata k dispozici, která popisují jazykové koncepty.

|Nadpis|Popis|
|-----|-----------|
|[Functions](./functions/index.md)|Funkce jsou základní jednotkou spuštění programu v jakémkoli programovacím jazyce. Stejně jako v jiných jazycích má funkce jazyka F # název, může mít parametry a přebírat argumenty a má tělo. Jazyk F # také podporuje konstrukce funkčního programování, jako je zpracování funkcí jako hodnot, použití nepojmenovaných funkcí ve výrazech, složení funkcí pro vytváření nových funkcí, funkcí curryfikované a implicitní definice funkcí pomocí částečného použití argumentů funkce.|
|[Typy F#](fsharp-types.md)|Popisuje typy, které se používají v F # a jak jsou typy F # pojmenovány a popsány.|
|[Odvození typu](type-inference.md)|Popisuje, jak kompilátor jazyka F # odvodí typy hodnot, proměnných, parametrů a vrácených hodnot.|
|[Automatická generalizace](./generics/automatic-generalization.md)|Popisuje obecné konstrukce v jazyce F #.|
|[Dědičnost](inheritance.md)|Popisuje dědění, které se používá k modelování vztahu "je-a", nebo při přetypování do objektově orientovaného programování.|
|[Členové](./members/index.md)|Popisuje členy typů objektů jazyka F #.|
|[Parametry a argumenty](Parameters-and-Arguments.md)|Popisuje jazykovou podporu pro definování parametrů a předávání argumentů funkcím, metodám a vlastnostem. Obsahuje informace o tom, jak předat odkazem.|
|[Přetížení operátoru](operator-overloading.md)|Popisuje, jak přetížit aritmetické operátory v typu třídy nebo záznamu a na globální úrovni.|
|[Přetypování a převody](casting-and-conversions.md)|Popisuje podporu pro převody typu v F #.|
|[Access Control](access-control.md)|Popisuje řízení přístupu v F #. Řízení přístupu znamená deklaraci toho, co klienti mohou používat určité programové prvky, jako jsou typy, metody, funkce a tak dále.|
|[Porovnávání vzorů](pattern-matching.md)|Popisuje vzory, které jsou pravidla pro transformaci vstupních dat, která se používají v celém jazyce F # k extrakci porovnání dat se vzorem, rozložení dat na části prvků nebo extrakci informací z dat různými způsoby.|
|[Aktivní vzory](active-patterns.md)|Popisuje aktivní vzory. Aktivní vzory umožňují definovat pojmenované oddíly, které rozdělují vstupní data. Můžete použít aktivní vzory a rozložit data vlastním způsobem pro každý oddíl.|
|[Kontrolní výrazy](assertions.md)|Popisuje `assert` výraz, což je funkce ladění, kterou můžete použít k otestování výrazu. Po selhání v režimu ladění vygeneruje kontrolní výraz dialogové okno systémové chyby.|
|[Zpracování výjimek](./exception-handling/index.md)|Obsahuje informace o podpoře zpracování výjimek v jazyce F #.|
|[atribut](attributes.md)|Popisuje atributy, které povolují použití metadat pro programovací konstrukci.|
|[Správa prostředků: `use` klíčové slovo](resource-management-the-use-keyword.md)|Popisuje klíčová slova `use` a `using` , která mohou řídit inicializaci a vydání prostředků.|
|[obsažené](namespaces.md)|Popisuje podporu oboru názvů v jazyce F #. Obor názvů umožňuje organizovat kód do oblastí souvisejících funkcí tím, že umožňuje připojit název k seskupení prvků programu.|
|[Moduly](modules.md)|Popisuje moduly. Modul jazyka F # je seskupení kódu F #, jako jsou hodnoty, typy a hodnoty funkcí v programu F #. Seskupení kódu v modulech pomáhá udržet související kód dohromady a pomáhá vyhnout se konfliktům názvů v programu.|
|[Deklarace importu: `open` klíčové slovo](import-declarations-the-open-keyword.md)|Popisuje `open` , jak funguje. Deklarace importu určuje modul nebo obor názvů, jehož prvky můžete odkazovat bez použití plně kvalifikovaného názvu.|
|[Signatury](signature-files.md)|Popisuje signatury a soubory signatur. Podpisový soubor obsahuje informace o veřejných podpisech sady prvků programu F #, jako jsou typy, obory názvů a moduly. Dá se použít k určení přístupnosti těchto prvků programu.|
|[Dokumentace XML](xml-documentation.md)|Popisuje podporu pro generování souborů dokumentace pro komentáře dokumentu XML, označované také jako komentáře se třemi lomítky. Můžete získat dokumentaci z komentářů kódu v F # stejně jako v jiných jazycích .NET.|
|[Podrobná syntaxe](verbose-syntax.md)|Popisuje syntaxi pro konstrukce F #, pokud není povolena zjednodušená syntaxe. Podrobná syntaxe je označena `#light "off"` direktivou v horní části souboru kódu.|
|[Formátování prostého textu](plaintext-formatting.md)|Naučte se používat sprintf – a jiné formátování prostého textu v aplikacích a skriptech F #.|

## <a name="f-types"></a>Typy F#

Následující tabulka uvádí referenční témata k dispozici, která popisují typy podporované jazykem F #.

|Nadpis|Popis|
|-----|-----------|
|[hodnota](./values/index.md)|Popisuje hodnoty, což jsou neměnné množství, které má určitý typ; hodnoty mohou být integrální nebo plovoucí desetinné čárky, znaky nebo text, seznamy, sekvence, pole, řazené kolekce členů, rozlišené sjednocení, záznamy, typy tříd nebo hodnoty funkcí.|
|[Základní typy](basic-types.md)|Popisuje základní typy, které se používají v jazyce F #. Poskytuje také odpovídající typy rozhraní .NET a minimální a maximální hodnoty pro každý typ.|
|[Typ jednotky](unit-type.md)|Popisuje `unit` typ, který je typ, který označuje absenci konkrétní hodnoty; `unit` typ má pouze jednu hodnotu, která funguje jako zástupný symbol, pokud žádná jiná hodnota neexistuje nebo je vyžadována.|
|[Řetězce](strings.md)|Popisuje řetězce v jazyce F #. `string`Typ představuje neměnný text jako posloupnost znaků Unicode. `string`je alias pro `System.String` v .NET Framework.|
|[N-tice](tuples.md)|Popisuje řazené kolekce členů, které jsou seskupeními nepojmenovaných, ale seřazené hodnoty možných různých typů.|
|[Typy kolekcí F#](fsharp-collection-types.md)|Přehled typů kolekce funkcí F #, včetně typů pro pole, seznamy, posloupnosti (seq), mapy a sady.|
|[Seznamy](lists.md)|Popisuje seznamy. Seznam v jazyce F # je seřazená, neproměnlivá řada prvků všech stejného typu.|
|[Možnosti](options.md)|Popisuje typ možnosti. Možnost v jazyce F # se používá v případě, že hodnota může nebo nemusí existovat. Možnost má podkladový typ a může buď obsahovat hodnotu tohoto typu, nebo nemusí mít hodnotu.|
|[Sekvence](sequences.md)|Popisuje sekvence. Sekvence je logická řada prvků všech jednoho typu. Jednotlivé prvky sekvence jsou vypočítány pouze v případě potřeby, takže reprezentace může být menší než počet prvků literálu.|
|[Pole](arrays.md)|Popisuje pole. Pole mají pevnou velikost, s nulovým základem, proměnlivé sekvence po sobě jdoucích datových prvků, a to vše stejného typu.|
|[Záznamy](records.md)|Popisuje záznamy. Záznamy reprezentují jednoduché agregované hodnoty pojmenovaných hodnot, volitelně s členy.|
|[Rozlišovaná sjednocení](discriminated-unions.md)|Popisuje rozlišené sjednocení, které poskytuje podporu pro hodnoty, které mohou být jedním z různých pojmenovaných případů, z nichž každá má možné různé hodnoty a typy.|
|[Výčty](enumerations.md)|Popisuje výčty typů, které mají definovanou sadu pojmenovaných hodnot. Můžete je použít místo literálů, aby bylo možné čitelnější a udržovatelnější kód.|
|[Referenční buňky](reference-cells.md)|Popisuje referenční buňky, což jsou umístění úložiště, která umožňují vytvořit proměnlivé proměnné s referenční sémantikou.|
|[Zkratky typů](type-abbreviations.md)|Popisuje zkratky typu, což jsou alternativní názvy pro typy.|
|[Třídy](classes.md)|Popisuje třídy, které jsou typy reprezentující objekty, které mohou mít vlastnosti, metody a události.|
|[Struktury](structures.md)|Popisuje struktury, které jsou typy kompaktních objektů, které mohou být efektivnější než třída pro typy, které mají malé množství dat a jednoduché chování.|
|[Rozhraní](interfaces.md)|Popisuje rozhraní, která určují sady souvisejících členů, které implementují jiné třídy.|
|[Abstraktní třídy](abstract-classes.md)|Popisuje abstraktní třídy, které jsou třídy, které ponechávají některé nebo všechny členy neimplementované, takže implementace mohou být poskytnuty odvozenými třídami.|
|[Rozšíření typů](type-extensions.md)|Popisuje rozšíření typu, která umožňují přidat nové členy do dříve definovaného typu objektu.|
|[Flexibilní typy](flexible-types.md)|Popisuje flexibilní typy. Flexibilní anotace typu je indikaci, že parametr, proměnná nebo hodnota má typ, který je kompatibilní se zadaným typem, kde kompatibilita je určena pozicí v objektově orientované hierarchii tříd nebo rozhraní.|
|[Delegáty](delegates.md)|Popisuje delegáty, které reprezentují volání funkce jako objekt.|
|[Měrné jednotky](units-of-measure.md)|Popisuje měrné jednotky. Hodnoty s plovoucí desetinnou čárkou v jazyce F # můžou mít přidružené měrné jednotky, které se obvykle používají k označení délky, objemu, hmotnosti a tak dále.|
|[Zprostředkovatelé typů](../tutorials/type-providers/index.md)|Popisuje typ a obsahuje odkazy na návody k používání předdefinovaných poskytovatelů typů pro přístup k databázím a webovým službám.|

## <a name="f-expressions"></a>Výrazy F #

V následující tabulce jsou uvedena témata, která popisují výrazy jazyka F #.

|Nadpis|Popis|
|-----|-----------|
|[Podmíněné výrazy:`if...then...else`](conditional-expressions-if-then-else.md)|Popisuje `if...then...else` výraz, který spouští různé větve kódu a také je vyhodnocen na jinou hodnotu v závislosti na daném logickém výrazu.|
|[Výrazy shody](match-expressions.md)|Popisuje `match` výraz, který poskytuje řízení větvení, které je založeno na porovnání výrazu se sadou vzorů.|
|[Smyčky: `for...to` výraz](loops-for-to-expression.md)|Popisuje `for...to` výraz, který se používá k iterování smyčky v rámci rozsahu hodnot proměnné smyčky.|
|[Smyčky: `for...in` výraz](loops-for-in-expression.md)|Popisuje `for...in` výraz, konstrukci smyčky, která se používá k iterování přes shody vzoru ve vyčíslitelné kolekci, jako je například výraz rozsahu, sekvence, seznam, pole nebo jiná konstrukce, která podporuje výčet.|
|[Smyčky: `while...do` výraz](loops-while-do-expression.md)|Popisuje `while...do` výraz, který se používá k provedení iterativního spuštění (smyčky), zatímco zadaná podmínka testu je pravdivá.|
|[Objektové výrazy](object-expressions.md)|Popisuje výrazy objektu, které jsou výrazy, které vytvářejí nové instance dynamicky vytvořeného typu anonymního objektu, který je založen na stávajícím základním typu, rozhraní nebo sadě rozhraní.|
|[Výrazy Lazy](lazy-expressions.md)|Popisuje opožděné výrazy, které jsou výpočty, které nejsou vyhodnocovány okamžitě, ale jsou vyhodnoceny, když je výsledek skutečně požadován.|
|[Výpočetní výrazy](computation-expressions.md)|Popisuje výrazy výpočtů v jazyce F #, které poskytují praktickou syntaxi pro zápis výpočtů, které mohou být seřazeny a kombinovány pomocí konstrukcí a vazeb toku řízení. Dají se použít k poskytnutí pohodlné syntaxe pro *monádami*, funkce programování, která se dá použít ke správě dat, řízení a vedlejších účinků ve funkčních programech. Jeden typ výpočetního výrazu, asynchronní pracovní postup, poskytuje podporu pro asynchronní a paralelní výpočty. Další informace najdete v tématu [asynchronní pracovní postupy](asynchronous-workflows.md).|
|[Asynchronní pracovní postupy](asynchronous-workflows.md)|Popisuje asynchronní pracovní postupy, funkce jazyka, která umožňuje psát asynchronní kód způsobem, který je velmi blízko způsobu, jakým byste mohli přirozeně psát synchronní kód.|
|[Uvozovky kódu](code-quotations.md)|Popisuje citace kódu, funkci jazyka, která umožňuje vygenerovat a pracovat s výrazy kódu jazyka F # programově.|
|[Výrazy dotazu](query-expressions.md)|Popisuje výrazy dotazu, funkci jazyka, která implementuje LINQ pro F # a umožňuje zapisovat dotazy na zdroj dat nebo vyčíslitelné kolekce.|

## <a name="compiler-supported-constructs"></a>Konstrukce podporované kompilátorem

V následující tabulce jsou uvedena témata, která popisují speciální konstrukce podporované kompilátorem.

|Téma|Popis|
|-----|-----------|
|[Možnosti kompilátoru](compiler-options.md)|Popisuje možnosti příkazového řádku pro kompilátor F #.|
|[Direktivy kompilátoru](compiler-directives.md)|Popisuje direktivy procesoru a direktivy kompilátoru.|
|[Identifikátory zdrojového řádku, souboru a cesty](source-line-file-path-identifiers.md)|Popisuje identifikátory `__LINE__` `__SOURCE_DIRECTORY__` a `__SOURCE_FILE__` , což jsou předdefinované hodnoty, které vám umožňují přístup ke zdrojovému číslu řádku, adresáři a názvu souboru ve vašem kódu.|
