---
title: Základy výrazů dotazu (LINQ v jazyce C#)
description: Zavádí koncepty související s výrazy dotazu.
ms.date: 11/30/2016
ms.assetid: 027db1f8-346f-44d2-a16e-043fcea3a4e0
ms.openlocfilehash: 83beaa82d4b4b42ff9da5230edddd391b33a0717
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173351"
---
# <a name="query-expression-basics"></a>Základy výrazů dotazů

Tento článek představuje základní pojmy související s výrazy dotazu v jazyce C#.

## <a name="what-is-a-query-and-what-does-it-do"></a>Co je dotaz a co dělá?

*Dotaz* je sada pokynů, která popisuje, jaká data se mají načíst z daného zdroje dat (nebo zdrojů) a jaký obrazec a organizace by měla mít vrácená data. Dotaz se liší od výsledků, které vytváří.

Obecně je zdrojová data uspořádána logicky jako posloupnost prvků stejného druhu. Například databázová tabulka SQL obsahuje posloupnost řádků. V souboru XML je "sekvence" elementů XML (i když jsou uspořádány hierarchicky ve stromové struktuře). Kolekce v paměti obsahuje posloupnost objektů.

Z hlediska aplikace není důležitý konkrétní typ a struktura původních zdrojových dat. Aplikace vždy vidí zdrojová data <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Linq.IQueryable%601> jako kolekce nebo kolekce. Například v LINQ na XML jsou zdrojová `IEnumerable` \< <xref:System.Xml.Linq.XElement> data viditelná jako>.

Vzhledem k této zdrojové sekvenci může dotaz provést jednu ze tří věcí:

- Načíst podmnožinu prvků k vytvoření nové sekvence bez úpravy jednotlivých prvků. Dotaz pak může seřadit nebo seskupit vrácenou sekvenci různými způsoby, jak je znázorněno v následujícím příkladu `scores` `int[]`(předpokládejme, že je ):

    [!code-csharp[csrefQueryExpBasics#45](~/samples/snippets/csharp/concepts/linq/query-expression-basics_1.cs)]

- Načíst posloupnost prvků jako v předchozím příkladu, ale transformovat je na nový typ objektu. Dotaz může například načíst pouze příjmení z určitých záznamů zákazníků ve zdroji dat. Nebo může načíst celý záznam a potom jej použít k vytvoření jiného typu objektu v paměti nebo dokonce dat XML před generováním konečné sekvence výsledků. Následující příklad ukazuje projekce `int` z `string`do . Poznamenejte `highScoresQuery`si nový typ .

    [!code-csharp[csrefQueryExpBasics#46](~/samples/snippets/csharp/concepts/linq/query-expression-basics_2.cs)]

- Načíst hodnotu singleton o zdrojových datech, například:

  - Počet prvků, které odpovídají určité podmínce.

  - Prvek, který má největší nebo nejmenší hodnotu.

  - První prvek, který odpovídá podmínce nebo součet konkrétních hodnot v zadané sadě prvků. Například následující dotaz vrátí počet skóre větší než `scores` 80 z celého pole:

    [!code-csharp[csrefQueryExpBasics#47](~/samples/snippets/csharp/concepts/linq/query-expression-basics_3.cs)]

    V předchozím příkladu si všimněte použití závorek kolem výrazu dotazu před voláním `Count` metody. Můžete také vyjádřit pomocí nové proměnné pro uložení konkrétní výsledek. Tato technika je čitelnější, protože udržuje proměnnou, která ukládá dotaz odděleně od dotazu, který ukládá výsledek.

    [!code-csharp[csrefQueryExpBasics#48](~/samples/snippets/csharp/concepts/linq/query-expression-basics_4.cs)]

V předchozím příkladu je dotaz proveden ve `Count`volání `Count` , protože musí itrovat výsledky, aby bylo `highScoresQuery`možné určit počet prvků vrácených .

## <a name="what-is-a-query-expression"></a>Co je výraz dotazu?

*Výraz dotazu* je dotaz vyjádřený v syntaxi dotazu. Výraz dotazu je konstrukce jazyka první třídy. Je stejně jako jakýkoli jiný výraz a lze použít v libovolném kontextu, ve kterém je platný výraz Jazyka C#. Výraz dotazu se skládá ze sady klauzulí napsaných v deklarativní syntaxi podobné SQL nebo XQuery. Každá klauzule zase obsahuje jeden nebo více výrazů Jazyka C# a tyto výrazy mohou být samy o sobě výrazem dotazu nebo výrazem dotazu.

Výraz dotazu musí začínat klauzulí [from](../language-reference/keywords/from-clause.md) a musí končit klauzulí [select](../language-reference/keywords/select-clause.md) nebo [group.](../language-reference/keywords/group-clause.md) Mezi první `from` klauzule `select` a `group` poslední nebo klauzule, může obsahovat jednu nebo více z těchto volitelných doložek: [kde](../language-reference/keywords/where-clause.md), [orderby](../language-reference/keywords/orderby-clause.md), [join](../language-reference/keywords/join-clause.md), [let](../language-reference/keywords/let-clause.md) a dokonce i další [z](../language-reference/keywords/from-clause.md) doložek. Můžete také použít [do](../language-reference/keywords/into.md) klíčové slovo povolit výsledek `join` nebo `group` klauzule sloužit jako zdroj pro další klauzule dotazu ve stejném výrazu dotazu.

### <a name="query-variable"></a>Proměnná dotazu

V LINQ je proměnná dotazu libovolná proměnná, která ukládá *dotaz* namísto *výsledků* dotazu. Přesněji řečeno, proměnná dotazu je vždy výčíslný typ, který vytvoří posloupnost prvků, když je iterována přes v příkazu `foreach` nebo přímé volání jeho `IEnumerator.MoveNext` metody.

Následující příklad kódu ukazuje jednoduchý výraz dotazu s jedním zdrojem dat, jednou klauzulí filtrování, jednou klauzulí řazení a žádnou transformací zdrojových prvků. Klauzule `select` ukončí dotaz.

[!code-csharp[csrefQueryExpBasics#49](~/samples/snippets/csharp/concepts/linq/query-expression-basics_5.cs)]

V předchozím příkladu `scoreQuery` je *proměnná dotazu,* která se někdy označuje jako pouze *dotaz*. Proměnná dotazu ukládá žádná data skutečného `foreach` výsledku, která jsou vytvořena ve smyčce. A když `foreach` se příkaz spustí, výsledky dotazu nejsou `scoreQuery`vráceny prostřednictvím proměnné dotazu . Spíše jsou vráceny prostřednictvím `testScore`iterace proměnné . Proměnná `scoreQuery` může být iterována ve druhé `foreach` smyčce. Bude mít stejné výsledky, dokud nebude změněn ani zdroj dat.

Proměnná dotazu může uložit dotaz, který je vyjádřen v syntaxi dotazu nebo syntaxi metody nebo jejich kombinaci. V následujících příkladech `queryMajorCities` `queryMajorCities2` jsou proměnné dotazu:

[!code-csharp[csrefQueryExpBasics#50](~/samples/snippets/csharp/concepts/linq/query-expression-basics_6.cs)]

Na druhé straně následující dva příklady zobrazit proměnné, které nejsou proměnné dotazu, i když každý je inicializován s dotazem. Nejedná se o proměnné dotazu, protože ukládají výsledky:

[!code-csharp[csrefQueryExpBasics#51](~/samples/snippets/csharp/concepts/linq/query-expression-basics_7.cs)]

Další informace o různých způsobech vyjádření dotazů naleznete [v tématu Syntaxe a syntaxe metody dotazu v linq](../programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md).

#### <a name="explicit-and-implicit-typing-of-query-variables"></a>Explicitní a implicitní psaní proměnných dotazu

Tato dokumentace obvykle poskytuje explicitní typ proměnné dotazu, aby se zobrazil vztah typu mezi proměnnou dotazu a [klauzulí select](../language-reference/keywords/select-clause.md). Můžete však také použít klíčové slovo [var](../language-reference/keywords/var.md) k pokynu kompilátoru odvodit typ proměnné dotazu (nebo jiné místní proměnné) v době kompilace. Příklad dotazu, který byl zobrazen dříve v tomto tématu lze také vyjádřit pomocí implicitní psaní:

[!code-csharp[csrefQueryExpBasics#52](~/samples/snippets/csharp/concepts/linq/query-expression-basics_8.cs)]

Další informace naleznete [v tématu Implicitně zadané místní proměnné](../programming-guide/classes-and-structs/implicitly-typed-local-variables.md) a vztahy typu v [operacích dotazu LINQ](../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).

### <a name="starting-a-query-expression"></a>Spuštění výrazu dotazu

Výraz dotazu `from` musí začínat klauzulí. Určuje zdroj dat spolu s proměnnou rozsahu. Proměnná rozsahu představuje každý po sobě jdoucí prvek ve zdrojové sekvenci při procházení zdrojové sekvence. Proměnná rozsahu je silně zařazována na základě typu prvků ve zdroji dat. V následujícím příkladu, protože `countries` `Country` je pole objektů, je proměnná rozsahu také zadána jako `Country`. Vzhledem k tomu, že proměnná rozsahu je silně zadaný, můžete použít operátor tečka pro přístup k všem dostupným členům typu.

[!code-csharp[csrefQueryExpBasics#53](~/samples/snippets/csharp/concepts/linq/query-expression-basics_9.cs)]

Proměnná rozsahu je v oboru, dokud není dotaz ukončen s středníkem nebo *s klauzulí pokračování.*

Výraz dotazu může `from` obsahovat více klauzulí. Další `from` klauzule použijte, pokud každý prvek ve zdrojové sekvenci je sám kolekce nebo obsahuje kolekci. Předpokládejme například, že máte `Country` kolekci objektů, z `City` nichž `Cities`každá obsahuje kolekci objektů s názvem . Chcete-li `City` zadat `Country`dotaz na `from` objekty v každém z nich , použijte dvě klauzule, jak je znázorněno zde:

[!code-csharp[csrefQueryExpBasics#54](~/samples/snippets/csharp/concepts/linq/query-expression-basics_10.cs)]

Další informace naleznete v [tématu z klauzule](../language-reference/keywords/from-clause.md).

### <a name="ending-a-query-expression"></a>Ukončení výrazu dotazu

Výraz dotazu musí končit `group` klauzulí `select` nebo klauzulí.

#### <a name="group-clause"></a>group – klauzule

Klauzuli `group` použijte k vytvoření posloupnosti skupin uspořádaných podle zadaného klíče. Klíč může být libovolný datový typ. Například následující dotaz vytvoří posloupnost skupin, `Country` které obsahují jeden `char` nebo více objektů a jejichž klíč je hodnota.

[!code-csharp[csrefQueryExpBasics#55](~/samples/snippets/csharp/concepts/linq/query-expression-basics_11.cs)]

Další informace o seskupování naleznete v tématu [group clause](../language-reference/keywords/group-clause.md).

#### <a name="select-clause"></a>select – klauzule (C#)

Pomocí `select` klauzule vytvořit všechny ostatní typy sekvencí. Jednoduchá `select` klauzule pouze vytváří posloupnost stejného typu objektů jako objekty, které jsou obsaženy ve zdroji dat. V tomto příkladu obsahuje `Country` zdroj dat objekty. Klauzule `orderby` pouze seřadí prvky do `select` nového pořadí a klauzule vytvoří posloupnost přeřazené `Country` objekty.

[!code-csharp[csrefQueryExpBasics#56](~/samples/snippets/csharp/concepts/linq/query-expression-basics_12.cs)]

Klauzule `select` lze transformovat zdrojová data do posloupností nových typů. Tato transformace se také nazývá *projekce*. V následujícím příkladu `select` klauzule *projekty* posloupnost anonymní typy, která obsahuje pouze podmnožinu polí v původní prvek. Všimněte si, že nové objekty jsou inicializovány pomocí inicializátoru objektu.

[!code-csharp[csrefQueryExpBasics#57](~/samples/snippets/csharp/concepts/linq/query-expression-basics_13.cs)]

Další informace o všech způsobech, kterými lze `select` klauzuli použít k transformaci zdrojových dat, naleznete v [tématu select clause](../language-reference/keywords/select-clause.md).

#### <a name="continuations-with-into"></a>Pokračování s "into"

Klíčové `into` slovo v klauzuli `select` nebo `group` můžete použít k vytvoření dočasného identifikátoru, který ukládá dotaz. To provedete, když je nutné provést další operace dotazu na dotaz po seskupení nebo vybrat operaci. V následujícím `countries` příkladu jsou seskupeny podle populace v rozsahu 10 milionů. Po vytvoření těchto skupin další klauzule odfiltrovat některé skupiny a potom seřadit skupiny ve vzestupném pořadí. K provedení těchto dalších operací `countryGroup` je vyžadováno pokračování reprezentované.

[!code-csharp[csrefQueryExpBasics#58](~/samples/snippets/csharp/concepts/linq/query-expression-basics_14.cs)]

Další informace naleznete [v tématu](../language-reference/keywords/into.md).

### <a name="filtering-ordering-and-joining"></a>Filtrování, řazení a spojování

Mezi počáteční `from` klauzulí a `select` `group` koncovou nebo klauzulí`where` `join`jsou `orderby` `from`všechny `let`ostatní klauzule ( , , , , ) volitelné. Všechny volitelné klauzule mohou být použity nula krát nebo vícekrát v textu dotazu.

#### <a name="where-clause"></a>where – klauzule

Pomocí `where` klauzule můžete odfiltrovat prvky ze zdrojových dat na základě jednoho nebo více predikátových výrazů. Klauzule `where` v následujícím příkladu má jeden predikát se dvěma podmínkami.

[!code-csharp[csrefQueryExpBasics#59](~/samples/snippets/csharp/concepts/linq/query-expression-basics_15.cs)]

Další informace naleznete v tématu [where clause](../language-reference/keywords/where-clause.md).

#### <a name="orderby-clause"></a>orderby – klauzule

Pomocí `orderby` klauzule můžete seřadit výsledky vzestupně nebo sestupně. Můžete také zadat sekundární pořadí řazení. Následující příklad provádí primární řazení `country` na objekty pomocí vlastnosti. `Area` Potom provede sekundární řazení pomocí `Population` vlastnosti.

[!code-csharp[csrefQueryExpBasics#60](~/samples/snippets/csharp/concepts/linq/query-expression-basics_16.cs)]

Klíčové `ascending` slovo je volitelné; jedná se o výchozí pořadí řazení, pokud není zadáno žádné pořadí. Další informace naleznete v [tématu orderby klauzule](../language-reference/keywords/orderby-clause.md).

#### <a name="join-clause"></a>join – klauzule

Pomocí `join` klauzule můžete přidružit nebo kombinovat prvky z jednoho zdroje dat s prvky z jiného zdroje dat na základě porovnání rovnosti mezi zadanými klíči v každém prvku. V LINQ operace spojení jsou prováděny na sekvence objektů, jejichž prvky jsou různé typy. Po vytvoření dvou sekvencí je `select` `group` nutné použít příkaz nebo k určení prvku, který má být do výstupní sekvence uložit. Anonymní typ můžete také použít ke kombinaci vlastností z každé sady přidružených prvků do nového typu pro výstupní sekvenci. Následující příklad přidruží objekty, `prod` jejichž `Category` `categories` vlastnost odpovídá jedné z kategorií v poli řetězců. Produkty, `Category` jejichž neodpovídá `categories` žádnému řetězci, jsou odfiltrovány. Příkaz `select` projekty nový typ, jehož `cat` `prod`vlastnosti jsou převzaty z obou a .

[!code-csharp[csrefQueryExpBasics#61](~/samples/snippets/csharp/concepts/linq/query-expression-basics_17.cs)]

Můžete také provést spojení skupiny uložením výsledky `join` operace do dočasné proměnné pomocí [do](../language-reference/keywords/into.md) klíčového slova. Další informace naleznete v tématu [join clause](../language-reference/keywords/join-clause.md).

#### <a name="let-clause"></a>let – klauzule

Klauzuli `let` použijte k uložení výsledku výrazu, například volání metody, do nové proměnné rozsahu. V následujícím příkladu proměnná `firstName` rozsahu ukládá první prvek pole řetězců, `Split`které je vráceno .

[!code-csharp[csrefQueryExpBasics#62](~/samples/snippets/csharp/concepts/linq/query-expression-basics_18.cs)]

Další informace naleznete v tématu [let klauzule](../language-reference/keywords/let-clause.md).

### <a name="subqueries-in-a-query-expression"></a>Poddotazy ve výrazu dotazu

Klauzule dotazu může sama o sobě obsahovat výraz dotazu, který se někdy označuje jako *poddotaz*. Každý poddotaz začíná `from` vlastní klauzulí, která nemusí nutně ukazovat `from` na stejný zdroj dat v první klauzuli. Například následující dotaz zobrazuje výraz dotazu, který se používá v příkazu select k načtení výsledků operace seskupení.

[!code-csharp[csrefQueryExpBasics#63](~/samples/snippets/csharp/concepts/linq/query-expression-basics_19.cs)]

Další informace naleznete [v tématu Provedení poddotazu na operaci seskupení](perform-a-subquery-on-a-grouping-operation.md).

## <a name="see-also"></a>Viz také

- [Průvodce programováním v C#](../programming-guide/index.md)
- [LINQ (Language Integrated Query)](index.md)
- [Klíčová slova dotazu (LINQ)](../language-reference/keywords/query-keywords.md)
- [Standardní operátory dotazů – přehled](../programming-guide/concepts/linq/standard-query-operators-overview.md)
