---
title: Referenční dokumentace jazyka F#
description: Umožňuje F# najít informace o funkcích jazyka z tohoto odkazu na jazykové tokeny, koncepty, typy, výrazy a témata konstrukce podporovaná kompilátorem.
ms.date: 05/16/2016
ms.openlocfilehash: ac7e268b28d6bb654e4443d04695cb15fe756e9f
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424992"
---
# <a name="f-language-reference"></a>Referenční dokumentace jazyka F#

Tato část je odkazem na F# jazyk, víceúrovňové programovací jazyk, který cílí na .NET. F# Jazyk podporuje funkční, objektově orientované a imperativní programovací modely.

## <a name="f-tokens"></a>F#Klíčov

V následující tabulce jsou uvedena referenční témata, která poskytují tabulky klíčová slova, symboly a literály používané F#jako tokeny v.

|Název|Popis|
|-----|-----------|
|[Referenční dokumentace klíčových slov](keyword-reference.md)|Obsahuje odkazy na informace o všech F# klíčových slovech jazyka.|
|[Referenční dokumentace symbolů a operátorů](./symbol-and-operator-reference/index.md)|Obsahuje tabulku symbolů a operátorů, které jsou používány v F# jazyce.|
|[Literály](literals.md)|Popisuje syntaxi pro hodnoty literálu v F# a, jak zadat informace o typu F# pro literály.|

## <a name="f-language-concepts"></a>F#Jazykové koncepty

V následující tabulce jsou uvedena referenční témata k dispozici, která popisují jazykové koncepty.

|Název|Popis|
|-----|-----------|
|[Funkce](./functions/index.md)|Funkce jsou základní jednotkou spuštění programu v jakémkoli programovacím jazyce. Stejně jako v jiných jazycích má F# funkce název, může mít parametry a přebírat argumenty a má tělo. F#také podporuje konstrukce funkčního programování, jako je zpracování funkcí jako hodnot, použití nepojmenovaných funkcí ve výrazech, složení funkcí pro vytváření nových funkcí, funkcí curryfikované a implicitní definice funkcí pomocí možností částečného. použití argumentů funkce.|
|[Typy F#](fsharp-types.md)|Popisuje typy, které se používají v F# a způsob F# pojmenování a popsaných typů.|
|[Odvození typu](type-inference.md)|Popisuje, jak F# kompilátor odvodí typy hodnot, proměnných, parametrů a vrácených hodnot.|
|[Automatická generalizace](./generics/automatic-generalization.md)|Popisuje obecné konstrukce v F#.|
|[Dědičnost](inheritance.md)|Popisuje dědění, které se používá k modelování vztahu "je-a", nebo při přetypování do objektově orientovaného programování.|
|[Členové](./members/index.md)|Popisuje členy typů F# objektů.|
|[Parametry a argumenty](Parameters-and-Arguments.md)|Popisuje jazykovou podporu pro definování parametrů a předávání argumentů funkcím, metodám a vlastnostem. Obsahuje informace o tom, jak předat odkazem.|
|[Přetížení operátoru](operator-overloading.md)|Popisuje, jak přetížit aritmetické operátory v typu třídy nebo záznamu a na globální úrovni.|
|[Přetypování a převody](casting-and-conversions.md)|Popisuje podporu pro převody typu v F#.|
|[Řízení přístupu](access-control.md)|Popisuje řízení přístupu v F#nástroji. Řízení přístupu znamená deklaraci toho, co klienti mohou používat určité programové prvky, jako jsou typy, metody, funkce a tak dále.|
|[Porovnávání vzorů](pattern-matching.md)|Popisuje vzory, které jsou pravidla pro transformaci vstupních dat, která se používají v celém F# jazyce k extrakci porovnávacích dat se vzorem, rozložení dat na části prvků nebo extrakci informací z dat různými způsoby.|
|[Aktivní vzory](active-patterns.md)|Popisuje aktivní vzory. Aktivní vzory umožňují definovat pojmenované oddíly, které rozdělují vstupní data. Můžete použít aktivní vzory a rozložit data vlastním způsobem pro každý oddíl.|
|[Kontrolní výrazy](assertions.md)|Popisuje výraz `assert`, což je funkce ladění, kterou můžete použít k otestování výrazu. Po selhání v režimu ladění vygeneruje kontrolní výraz dialogové okno systémové chyby.|
|[Zpracování výjimek](./exception-handling/index.md)|Obsahuje informace o podpoře zpracování výjimek v F# jazyce.|
|[atribut](attributes.md)|Popisuje atributy, které povolují použití metadat pro programovací konstrukci.|
|[Správa prostředků: klíčové slovo `use`](resource-management-the-use-keyword.md)|Popisuje klíčová slova `use` a `using`, která mohou řídit inicializaci a vydání prostředků.|
|[obsažené](namespaces.md)|Popisuje podporu oboru názvů F#v. Obor názvů umožňuje organizovat kód do oblastí souvisejících funkcí tím, že umožňuje připojit název k seskupení prvků programu.|
|[Moduly](modules.md)|Popisuje moduly. F# Modul je seskupení F# kódu, jako jsou hodnoty, typy a hodnoty funkcí v F# programu. Seskupení kódu v modulech pomáhá udržet související kód dohromady a pomáhá vyhnout se konfliktům názvů v programu.|
|[Deklarace importu: klíčové slovo `open`](import-declarations-the-open-keyword.md)|Popisuje, jak `open` funguje. Deklarace importu určuje modul nebo obor názvů, jehož prvky můžete odkazovat bez použití plně kvalifikovaného názvu.|
|[Signatury](signature-files.md)|Popisuje signatury a soubory signatur. Podpisový soubor obsahuje informace o veřejných podpisech sady prvků F# programu, jako jsou typy, obory názvů a moduly. Dá se použít k určení přístupnosti těchto prvků programu.|
|[Dokumentace XML](xml-documentation.md)|Popisuje podporu pro generování souborů dokumentace pro komentáře dokumentu XML, označované také jako komentáře se třemi lomítky. Můžete získat dokumentaci z komentářů F# k kódu, stejně jako v jiných jazycích .NET.|
|[Podrobná syntaxe](verbose-syntax.md)|Popisuje syntaxi pro F# konstrukce, pokud není povolena odlehčená syntaxe. Podrobná syntaxe je označena direktivou `#light "off"` v horní části souboru kódu.|

## <a name="f-types"></a>Typy F#

Následující tabulka uvádí referenční témata k dispozici, která popisují typy podporované F# jazykem.

|Název|Popis|
|-----|-----------|
|[hodnota](./values/index.md)|Popisuje hodnoty, což jsou neměnné množství, které má určitý typ; hodnoty mohou být integrální nebo plovoucí desetinné čárky, znaky nebo text, seznamy, sekvence, pole, řazené kolekce členů, rozlišené sjednocení, záznamy, typy tříd nebo hodnoty funkcí.|
|[Základní typy](basic-types.md)|Popisuje základní typy, které se používají v F# jazyce. Poskytuje také odpovídající typy rozhraní .NET a minimální a maximální hodnoty pro každý typ.|
|[Typ jednotky](unit-type.md)|Popisuje typ `unit`, což je typ, který označuje absenci konkrétní hodnoty; typ `unit` má pouze jednu hodnotu, která funguje jako zástupný symbol, pokud žádná jiná hodnota neexistuje nebo je potřeba.|
|[Řetězce](strings.md)|Popisuje řetězce v F#. Typ `string` představuje neměnný text jako posloupnost znaků Unicode. `string` je alias pro `System.String` v .NET Framework.|
|[Řazené kolekce členů](tuples.md)|Popisuje řazené kolekce členů, které jsou seskupeními nepojmenovaných, ale seřazené hodnoty možných různých typů.|
|[Typy kolekcí F#](fsharp-collection-types.md)|Přehled typů F# funkční kolekce, včetně typů pro pole, seznamy, posloupnosti (seq), mapy a sady.|
|[Seznamy](lists.md)|Popisuje seznamy. Seznam v F# je seřazená, neproměnlivá řada prvků stejného typu.|
|[Možnosti](options.md)|Popisuje typ možnosti. Možnost v F# se používá, pokud hodnota může nebo nemusí existovat. Možnost má podkladový typ a může buď obsahovat hodnotu tohoto typu, nebo nemusí mít hodnotu.|
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
|[Měrné jednotky](units-of-measure.md)|Popisuje měrné jednotky. Hodnoty s plovoucí desetinnou čárkou v F# můžou mít přidružené měrné jednotky, které se obvykle používají k označení délky, objemu, hmotnosti a tak dále.|
|[Zprostředkovatelé typů](../tutorials/type-providers/index.md)|Popisuje typ a obsahuje odkazy na návody k používání předdefinovaných poskytovatelů typů pro přístup k databázím a webovým službám.|

## <a name="f-expressions"></a>F#Expression

V následující tabulce jsou uvedena témata, F# která popisují výrazy.

|Název|Popis|
|-----|-----------|
|[Podmíněné výrazy: `if...then...else`](conditional-expressions-if-then-else.md)|Popisuje výraz `if...then...else`, který spouští různé větve kódu a také je vyhodnocen na jinou hodnotu v závislosti na daném logickém výrazu.|
|[Výrazy shody](match-expressions.md)|Popisuje výraz `match`, který poskytuje řízení větvení, které je založeno na porovnání výrazu se sadou vzorů.|
|[Smyčky: výraz `for...to`](loops-for-to-expression.md)|Popisuje výraz `for...to`, který se používá k iteraci ve smyčce přes rozsah hodnot proměnné smyčky.|
|[Smyčky: výraz `for...in`](loops-for-in-expression.md)|Popisuje výraz `for...in`, smyčka, která se používá k iterování přes shody vzoru ve vyčíslitelné kolekci, jako je například výraz rozsahu, sekvence, seznam, pole nebo jiný konstruktor, který podporuje výčet.|
|[Smyčky: výraz `while...do`](loops-while-do-expression.md)|Popisuje výraz `while...do`, který se používá k provedení iterativního spuštění (opakování), zatímco zadaná podmínka testu je pravdivá.|
|[Objektové výrazy](object-expressions.md)|Popisuje výrazy objektu, které jsou výrazy, které vytvářejí nové instance dynamicky vytvořeného typu anonymního objektu, který je založen na stávajícím základním typu, rozhraní nebo sadě rozhraní.|
|[Výrazy Lazy](lazy-expressions.md)|Popisuje opožděné výrazy, které jsou výpočty, které nejsou vyhodnocovány okamžitě, ale jsou vyhodnoceny, když je výsledek skutečně požadován.|
|[Výpočetní výrazy](computation-expressions.md)|Popisuje výrazy výpočtů v F#, které poskytují praktickou syntaxi pro zápis výpočtů, které mohou být seřazeny a kombinovány pomocí konstrukcí a vazeb toku řízení. Dají se použít k poskytnutí pohodlné syntaxe pro *monádami*, funkce programování, která se dá použít ke správě dat, řízení a vedlejších účinků ve funkčních programech. Jeden typ výpočetního výrazu, asynchronní pracovní postup, poskytuje podporu pro asynchronní a paralelní výpočty. Další informace najdete v tématu [asynchronní pracovní postupy](asynchronous-workflows.md).|
|[Asynchronní pracovní postupy](asynchronous-workflows.md)|Popisuje asynchronní pracovní postupy, funkce jazyka, která umožňuje psát asynchronní kód způsobem, který je velmi blízko způsobu, jakým byste mohli přirozeně psát synchronní kód.|
|[Citace kódu](code-quotations.md)|Popisuje citace kódu, funkci jazyka, která umožňuje vygenerovat a pracovat s F# výrazy kódu programově.|
|[Výrazy dotazu](query-expressions.md)|Popisuje výrazy dotazu, funkci jazyka, která implementuje LINQ pro F# a umožňuje zapisovat dotazy na zdroj dat nebo vyčíslitelné kolekce.|

## <a name="compiler-supported-constructs"></a>Konstrukce podporované kompilátorem

V následující tabulce jsou uvedena témata, která popisují speciální konstrukce podporované kompilátorem.

|Téma|Popis|
|-----|-----------|
|[Možnosti kompilátoru](compiler-options.md)|Popisuje možnosti příkazového řádku pro F# kompilátor.|
|[Direktivy kompilátoru](compiler-directives.md)|Popisuje direktivy procesoru a direktivy kompilátoru.|
|[Identifikátory zdrojového řádku, souboru a cesty](source-line-file-path-identifiers.md)|Popisuje identifikátory `__LINE__`, `__SOURCE_DIRECTORY__` a `__SOURCE_FILE__`, což jsou předdefinované hodnoty, které umožňují přístup ke zdrojovému číslu řádku, adresáři a názvu souboru ve vašem kódu.|

## <a name="see-also"></a>Viz také:

- [Visual F#](../index.md)
