---
title: Základy výrazů dotazů (LINQ v JAZYKU C#)
description: Představuje koncepty související s výrazy dotazu
ms.date: 11/30/2016
ms.assetid: 027db1f8-346f-44d2-a16e-043fcea3a4e0
ms.openlocfilehash: 68f338381e354f4944539d63ca3a3cc3500031c1
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43884364"
---
# <a name="query-expression-basics"></a>Základy výrazů dotazů

Tento článek představuje základní koncepty související s výrazy dotazů v jazyce C#.

## <a name="what-is-a-query-and-what-does-it-do"></a>Co je dotaz a co to dělá?

A *dotazu* je sada instrukcí, které popisují, jaká data pro načtení do daného zdroje dat (nebo zdroje) a jaké tvar a organizaci by měl mít vrácená data. Dotaz se liší od výsledky, které vytvoří.

Obecně platí zdroj dat je logicky uspořádaná jako sekvenci prvků stejného typu. Například tabulky databáze SQL obsahuje posloupnosti řádků. V souboru XML je "sekvence" elementů XML (i když tyto funkce jsou uspořádané hierarchicky ve stromové struktuře). Kolekci v paměť obsahuje pouze sekvenci objektů.

Z hlediska aplikace konkrétní typ a strukturu původní zdroj dat není důležité. Aplikace vždy zobrazí zdroj dat jako <xref:System.Collections.Generic.IEnumerable%601> nebo <xref:System.Linq.IQueryable%601> kolekce. Například v technologii LINQ to XML, zdrojová data jsou dostupná jako `IEnumerable` \< <xref:System.Xml.Linq.XElement>>.

Zadaný této zdrojové sekvence, dotaz může proveďte jednu z tři věci:

- Načtení podmnožiny prvků k vytvoření nového pořadí beze změny jednotlivé prvky. Dotaz může pak řazení nebo seskupení vrácené posloupnosti různými způsoby, jak je znázorněno v následujícím příkladu (Předpokládejme `scores` je `int[]`):

    [!code-csharp[csrefQueryExpBasics#45](~/samples/snippets/csharp/concepts/linq/query-expression-basics_1.cs)]

- Načíst řadu prvků, jako v předchozím příkladu, ale transformují je na nový typ objektu. Například dotaz může načíst pouze poslední názvy z určité záznamy o zákaznících ve zdroji dat. Nebo může načíst úplný záznam a pak přes ni vytvořit jiného typu objektů v paměti do mezipaměti nebo dokonce data XML před generováním pořadí konečný výsledek. Následující příklad ukazuje projekce ze `int` k `string`. Všimněte si nového typu `highScoresQuery`.

    [!code-csharp[csrefQueryExpBasics#46](~/samples/snippets/csharp/concepts/linq/query-expression-basics_2.cs)]

- Načtěte hodnotu singleton zdrojových dat, jako například:

  - Počet prvků, které splňují určité podmínky.

  - Prvek, který má nejvyšší či nejnižší hodnotu.

  - První prvek, který odpovídá podmínce nebo součet konkrétní hodnoty v zadané sadě prvků. Například následující dotaz vrátí počet skóre větší než 80 z `scores` celočíselné pole:

    [!code-csharp[csrefQueryExpBasics#47](~/samples/snippets/csharp/concepts/linq/query-expression-basics_3.cs)]

    V předchozím příkladu, Všimněte si použití závorek okolo výrazu dotazu před voláním `Count` metody. To lze vyjádřit pomocí nové proměnné k ukládání konkrétních výsledků. Tato technika je lépe čitelný, protože udržuje odděleně od dotaz, který ukládá výsledek proměnné, která ukládá dotaz.

    [!code-csharp[csrefQueryExpBasics#48](~/samples/snippets/csharp/concepts/linq/query-expression-basics_4.cs)]

V předchozím příkladu je dotaz proveden při volání funkce `Count`, protože `Count` musí iteraci přes výsledky, aby bylo možné zjistit počet prvků vrácených `highScoresQuery`.

## <a name="what-is-a-query-expression"></a>Co je výraz dotazu?

A *výrazu dotazu* je dotaz vyjádřené v syntaxi dotazu. Výraz dotazu je typů prvotřídní jazykové konstrukce. Je stejně jako libovolný jiný výraz a je možné v libovolném kontextu, ve kterém je platný výraz jazyka C#. Výraz dotazu obsahuje sadu klauzulí napsané v deklarativní syntaxe podobně jako SQL nebo výraz XQuery. Každou klauzuli zase obsahuje jeden nebo více výrazy jazyka C# a tyto výrazy mohou sami být výrazu dotazu nebo obsahovat výraz dotazu.

Výraz dotazu musí začínat [z](../language-reference/keywords/from-clause.md) klauzule a musí končit [vyberte](../language-reference/keywords/select-clause.md) nebo [skupiny](../language-reference/keywords/group-clause.md) klauzuli. Mezi první `from` klauzule a poslední `select` nebo `group` klauzule, může obsahovat jeden nebo více z těchto klauzulí volitelné: [kde](../language-reference/keywords/where-clause.md), [orderby](../language-reference/keywords/orderby-clause.md), [spojení ](../language-reference/keywords/join-clause.md), [nechat](../language-reference/keywords/let-clause.md) a dokonce i další [z](../language-reference/keywords/from-clause.md) klauzule. Můžete také použít [do](../language-reference/keywords/into.md) – klíčové slovo umožňující výsledek `join` nebo `group` klauzuli, která bude sloužit jako zdroj pro další klauzule dotazu ve stejném výrazu dotazu.

### <a name="query-variable"></a>Proměnné dotazu

V technologii LINQ, proměnná dotazu je jakákoli proměnná, která ukládá *dotazu* místo *výsledky* dotazu. Přesněji řečeno, proměnná dotazu je vždy Výčtový typ, který vytvoří řadu prvků, když ho je procházena `foreach` příkazu nebo přímého volání jeho `IEnumerator.MoveNext` metoda.

Následující příklad kódu ukazuje výraz jednoduchý dotaz s jedním zdrojem dat, jednu klauzuli filtrování, jednu klauzuli pořadí a žádná transformace zdrojové elementy. `select` Končí klauzule dotazu.

[!code-csharp[csrefQueryExpBasics#49](~/samples/snippets/csharp/concepts/linq/query-expression-basics_5.cs)]

V předchozím příkladu `scoreQuery` je *proměnné dotazu* které se někdy označuje jako jenom *dotazu*. Ukládá žádná data skutečný výsledek, který je vytvořen v proměnné dotazu `foreach` smyčky. A když `foreach` spuštění příkazů výsledky dotazu nevrací prostřednictvím proměnné dotazu `scoreQuery`. Místo toho jsou vráceny prostřednictvím proměnné iterace `testScore`. `scoreQuery` Proměnnou můžete provést iteraci za sekundu `foreach` smyčky. To se vytvářejí stejné výsledky, tak dlouho, dokud ho ani zdroj dat byl změněn.

Proměnné dotazu může uložit dotaz, který je vyjádřena v syntaxi dotazu nebo syntaxe využívající metody nebo kombinaci obojího. V následujících příkladech obě `queryMajorCities` a `queryMajorCities2` jsou proměnné dotazu:

[!code-csharp[csrefQueryExpBasics#50](~/samples/snippets/csharp/concepts/linq/query-expression-basics_6.cs)]

Na druhé straně následující dva příklady ukazovat proměnné, které nejsou proměnné dotazu, i když každá je inicializován pomocí dotazu. Nejsou se proměnné dotazu, protože jsou v nich uložené výsledky:

[!code-csharp[csrefQueryExpBasics#51](~/samples/snippets/csharp/concepts/linq/query-expression-basics_7.cs)]

Další informace o různých způsobech rychlé dotazy, naleznete v tématu [syntaxe využívající dotazy a syntaxe využívající metody v LINQ](../programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md).

#### <a name="explicit-and-implicit-typing-of-query-variables"></a>Explicitní a implicitní zadáním proměnné dotazu

Tato dokumentace obvykle poskytuje explicitní typ proměnné dotazu chcete-li zobrazit typ vztahu mezi proměnné dotazu a [klauzule select](../language-reference/keywords/select-clause.md). Ale můžete také použít [var](../language-reference/keywords/var.md) – klíčové slovo, abyste instruovali kompilátor k odvození typu proměnné dotazu (nebo jakoukoli jinou místní proměnnou) v době kompilace. Například příklad dotazu, které se zobrazilo dříve v tomto tématu se dají vyjádřit také pomocí implicitního zápisu:

[!code-csharp[csrefQueryExpBasics#52](~/samples/snippets/csharp/concepts/linq/query-expression-basics_8.cs)]

Další informace najdete v tématu [implicitně typované lokální proměnné](../programming-guide/classes-and-structs/implicitly-typed-local-variables.md) a [vztahy typů v LINQ dotaz operace](../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).

### <a name="starting-a-query-expression"></a>Spuštění výrazu dotazu

Výraz dotazu musí začínat `from` klauzuli. Určuje zdroj dat spolu s proměnnou rozsahu. Proměnná rozsahu představuje každý prvek po sobě jdoucích ze zdrojové sekvence, jak procházet řízený zdrojové sekvence. Proměnná rozsahu je silně typováno podle typu ve zdroji dat prvků. V následujícím příkladu protože `countries` je pole `Country` objekty, proměnná rozsahu je také zadán jako `Country`. Vzhledem k tomu, že proměnná rozsahu je silně typováno, můžete použít operátor tečky pro přístup k libovolné dostupné členy typu.

[!code-csharp[csrefQueryExpBasics#53](~/samples/snippets/csharp/concepts/linq/query-expression-basics_9.cs)]

Proměnná rozsahu je v oboru, dokud nebude ukončen dotaz středníkem nebo s *pokračování* klauzuli.

Výraz dotazu může obsahovat více `from` klauzule. Pomocí dalších `from` klauzule pokud každý prvek ve zdrojové sekvenci je samotný soubor, nebo obsahuje kolekci. Například předpokládejme, že máte kolekci `Country` objektů, z nichž každý obsahuje kolekci `City` objektů s názvem `Cities`. Dotaz `City` objekty v každém `Country`, použijte dva `from` klauzule, jak je znázorněno zde:

[!code-csharp[csrefQueryExpBasics#54](~/samples/snippets/csharp/concepts/linq/query-expression-basics_10.cs)]

Další informace najdete v tématu [klauzule from](../language-reference/keywords/from-clause.md).

### <a name="ending-a-query-expression"></a>Ukončení výrazu dotazu

Buď musí končit výrazu dotazu `group` klauzule nebo `select` klauzuli.

#### <a name="group-clause"></a>group – klauzule

Použití `group` klauzule, která vytvoří posloupnost skupiny uspořádané podle klíče, který zadáte. Klíč může být libovolného datového typu. Například následující dotaz vytvoří posloupnost skupiny, která obsahuje jeden nebo více `Country` objekty a jehož klíč je `char` hodnotu.

[!code-csharp[csrefQueryExpBasics#55](~/samples/snippets/csharp/concepts/linq/query-expression-basics_11.cs)]

Další informace o seskupování najdete v tématu [group – klauzule](../language-reference/keywords/group-clause.md).

#### <a name="select-clause"></a>select – klauzule (C#)

Použití `select` klauzule, která vytvoří všechny ostatní typy pořadí. Jednoduchý `select` klauzule generuje pouze sekvenci objektů stejného typu jako objekty, které jsou obsaženy ve zdroji dat. V tomto příkladu zdroj dat obsahuje `Country` objekty. `orderby` Klauzule právě Seřadí prvky do nového pořadí a `select` klauzule generuje sekvenci uspořádaný `Country` objekty.

[!code-csharp[csrefQueryExpBasics#56](~/samples/snippets/csharp/concepts/linq/query-expression-basics_12.cs)]

`select` Klauzule je možné získat zdrojová data sekvencí nových typů. Je také název této transformace *projekce*. V následujícím příkladu `select` klauzule *projekty* sekvenci anonymních typů, která obsahuje pouze podmnožinu polí v původní elementu. Všimněte si, že nové objekty jsou inicializovány pomocí inicializátoru objektu.

[!code-csharp[csrefQueryExpBasics#57](~/samples/snippets/csharp/concepts/linq/query-expression-basics_13.cs)]

Další informace o tom, jak, který `select` klauzuli lze použít transformují zdrojová data, přečtěte si téma [klauzule select](../language-reference/keywords/select-clause.md).

#### <a name="continuations-with-into"></a>Pokračování s "do"

Můžete použít `into` – klíčové slovo v `select` nebo `group` klauzule vytvořit dočasné identifikátor, který ukládá dotaz. To proveďte, když musíte provádět operace dalších dotazů na dotazu po seskupení nebo vyberte operaci. V následujícím příkladu `countries` se seskupí podle naplnění oblastí 10 milionů. Poté, co tyto skupiny jsou vytvořené, další klauzule filtru některé skupiny a pak řazení skupin ve vzestupném pořadí. K provedení dalších operací, pokračování reprezentována `countryGroup` je povinný.

[!code-csharp[csrefQueryExpBasics#58](~/samples/snippets/csharp/concepts/linq/query-expression-basics_14.cs)]

Další informace najdete v tématu [do](../language-reference/keywords/into.md).

### <a name="filtering-ordering-and-joining"></a>Filtrování, řazení a propojení

Mezi počáteční `from` klauzule a konec `select` nebo `group` klauzule, všechny ostatní klauzule (`where`, `join`, `orderby`, `from`, `let`) jsou volitelné. Libovolné volitelné klauzule lze nula doby nebo více než jednou v textu dotazu.

#### <a name="where-clause"></a>where – klauzule

Použití `where` klauzule můžete filtrovat prvky ze zdroje dat založené na jeden nebo více výrazů predikátu. `where` Klauzule v následujícím příkladu má jeden predikát s dvě podmínky.

[!code-csharp[csrefQueryExpBasics#59](~/samples/snippets/csharp/concepts/linq/query-expression-basics_15.cs)]

Další informace najdete v tématu [kde klauzule](../language-reference/keywords/where-clause.md).

#### <a name="orderby-clause"></a>orderby – klauzule

Použití `orderby` klauzule seřadit výsledky ve vzestupném nebo sestupném pořadí. Můžete také určit pořadí řazení sekundární. Následující příklad provede primární řazení `country` objektů pomocí `Area` vlastnost. Pak pomocí provádí sekundární řazení `Population` vlastnost.

[!code-csharp[csrefQueryExpBasics#60](~/samples/snippets/csharp/concepts/linq/query-expression-basics_16.cs)]

`ascending` – Klíčové slovo je volitelné, je výchozí pořadí řazení, pokud není zadána žádná objednávka. Další informace najdete v tématu [klauzule orderby](../language-reference/keywords/orderby-clause.md).

#### <a name="join-clause"></a>join – klauzule

Použití `join` klauzuli spojení a/nebo zkombinovat prvky z jednoho zdroje dat s prvky z jiného zdroje dat založené na porovnání rovnosti mezi klíči zadaného v jednotlivých prvcích. V technologii LINQ spojení operace provádějí v pořadí, jehož prvky jsou různé typy objektů. Po připojení dvou sekvencí, je nutné použít `select` nebo `group` příkaz a zadejte které elementy pro ukládání do výstupní sekvenci. Anonymního typu můžete použít také ke sloučení vlastnosti ze všech sad přidružených elementů do nový typ pro výstupní sekvenci. V následujícím příkladu `prod` objekty, jejichž `Category` vlastnost odpovídá jednomu z kategorií v `categories` pole řetězců. Produkty jehož `Category` neodpovídá libovolný řetězec v `categories` , budou odfiltrovány. `select` Příkaz projekty nového typu, jehož vlastnosti pocházejí z obou `cat` a `prod`.

[!code-csharp[csrefQueryExpBasics#61](~/samples/snippets/csharp/concepts/linq/query-expression-basics_17.cs)]

Spojení skupiny můžete také provádět pomocí ukládání výsledků `join` operace do dočasné proměnné s použitím [do](../language-reference/keywords/into.md) – klíčové slovo. Další informace najdete v tématu [klauzule join](../language-reference/keywords/join-clause.md).

#### <a name="let-clause"></a>let – klauzule 

Použití `let` klauzule, která uloží výsledek výrazu, jako je například volání metody v nové proměnné rozsahu. V následujícím příkladu proměnná rozsahu `firstName` ukládá první prvek pole řetězců, které vrací `Split`.

[!code-csharp[csrefQueryExpBasics#62](~/samples/snippets/csharp/concepts/linq/query-expression-basics_18.cs)]

Další informace najdete v tématu [let – klauzule](../language-reference/keywords/let-clause.md).

### <a name="subqueries-in-a-query-expression"></a>Poddotazy ve výrazu dotazu

Klauzule dotazu mohou obsahovat výraz dotazu, který se někdy označuje jako *poddotaz*. Každý poddotaz spustí vlastní `from` klauzuli, která není nutně cesta ke stejnému zdroji dat v prvním `from` klauzuli. Například následující dotaz ukazuje výraz dotazu, který se používá v příkazu select k načtení výsledků operace seskupení.

[!code-csharp[csrefQueryExpBasics#63](~/samples/snippets/csharp/concepts/linq/query-expression-basics_19.cs)]

Další informace najdete v tématu [postupy: provádění poddotazů na operace seskupení](perform-a-subquery-on-a-grouping-operation.md).

## <a name="see-also"></a>Viz také:

- [Průvodce programovacího jazyka C#](../programming-guide/index.md)  
- [LINQ (Language Integrated Query)](index.md)  
- [Klíčová slova dotazu (LINQ)](../language-reference/keywords/query-keywords.md)  
- [Přehled standardních operátorů dotazu](../programming-guide/concepts/linq/standard-query-operators-overview.md)  