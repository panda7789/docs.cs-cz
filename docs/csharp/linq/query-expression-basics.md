---
title: Základy výrazů dotazů (LINQ in C#)
description: Představuje koncepty související s výrazy dotazu.
ms.date: 11/30/2016
ms.assetid: 027db1f8-346f-44d2-a16e-043fcea3a4e0
ms.openlocfilehash: 5ebe2163df47c60c677d7ac911ce0f65529835eb
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2020
ms.locfileid: "75635857"
---
# <a name="query-expression-basics"></a>Základy výrazů dotazů

V tomto článku se seznámíte se základními koncepty týkajícími se výrazů dotazů v C#.

## <a name="what-is-a-query-and-what-does-it-do"></a>Co je dotaz a co dělá?

*Dotaz* je sada instrukcí, která popisuje, jaká data se mají načíst z daného zdroje dat (nebo zdrojů) a jaký tvar a organizace vrácená data mají mít. Dotaz se liší od výsledků, které vytváří.

Obecně jsou zdrojová data uspořádána logicky jako sekvence prvků stejného druhu. Například tabulka SQL Database obsahuje posloupnost řádků. V souboru XML je "sekvence" prvků XML (i když jsou uspořádány hierarchicky ve stromové struktuře). Kolekce v paměti obsahuje sekvenci objektů.

Z pohledu aplikace není konkrétní typ a struktura původních zdrojových dat důležité. Aplikace vždy uvidí zdrojová data jako <xref:System.Collections.Generic.IEnumerable%601> nebo <xref:System.Linq.IQueryable%601> kolekci. Například v LINQ to XML se zdrojová data zobrazují jako `IEnumerable`\<<xref:System.Xml.Linq.XElement>>.

V této zdrojové sekvenci může dotaz provádět jednu ze tří věcí:

- Načte podmnožinu prvků pro vytvoření nové sekvence bez změny jednotlivých prvků. Dotaz pak může seřadit nebo seskupit vrácenou posloupnost různými způsoby, jak je znázorněno v následujícím příkladu (Předpokládejme, `scores` je `int[]`):

    [!code-csharp[csrefQueryExpBasics#45](~/samples/snippets/csharp/concepts/linq/query-expression-basics_1.cs)]

- Načte sekvenci prvků jako v předchozím příkladu, ale transformuje je na nový typ objektu. Dotaz může například načíst pouze poslední názvy z určitých záznamů zákazníka ve zdroji dat. Nebo může načíst úplný záznam a pak ho použít k vytvoření dalšího typu objektu v paměti nebo dokonce dat XML před generováním výsledné sekvence výsledků. Následující příklad ukazuje projekci z `int` na `string`. Všimněte si nového typu `highScoresQuery`.

    [!code-csharp[csrefQueryExpBasics#46](~/samples/snippets/csharp/concepts/linq/query-expression-basics_2.cs)]

- Načtěte hodnotu typu Singleton týkající se zdrojových dat, jako například:

  - Počet prvků, které odpovídají určité podmínce.

  - Prvek, který má největší nebo nejnižší hodnotu.

  - První prvek, který odpovídá podmínce, nebo součet konkrétních hodnot v zadané sadě prvků. Například následující dotaz vrátí počet skóre větší než 80 z `scores` pole s celými čísly:

    [!code-csharp[csrefQueryExpBasics#47](~/samples/snippets/csharp/concepts/linq/query-expression-basics_3.cs)]

    V předchozím příkladu si poznamenejte použití závorek kolem výrazu dotazu před voláním metody `Count`. Můžete to také vyjádřit pomocí nové proměnné pro uložení konkrétního výsledku. Tato technika je čitelnější, protože uchovává proměnnou, která ukládá dotaz odděleně od dotazu, který ukládá výsledek.

    [!code-csharp[csrefQueryExpBasics#48](~/samples/snippets/csharp/concepts/linq/query-expression-basics_4.cs)]

V předchozím příkladu je dotaz proveden při volání `Count`, protože `Count` musí iterovat na výsledky, aby bylo možné určit počet prvků vrácených `highScoresQuery`.

## <a name="what-is-a-query-expression"></a>Co je výraz dotazu?

*Výraz dotazu* je dotaz vyjádřený v syntaxi dotazu. Výraz dotazu je konstrukce jazyka první třídy. Funguje stejně jako jakýkoli jiný výraz a lze jej použít v jakémkoli kontextu, ve kterém je C# výraz platný. Výraz dotazu se skládá ze sady klauzulí napsaných v deklarativní syntaxi, podobně jako SQL nebo XQuery. Každá klauzule zase obsahuje jeden nebo více C# výrazů a tyto výrazy mohou být buď výraz dotazu, nebo obsahují výraz dotazu.

Výraz dotazu musí začínat klauzulí [from](../language-reference/keywords/from-clause.md) a musí končit klauzulí [Select](../language-reference/keywords/select-clause.md) nebo [Group](../language-reference/keywords/group-clause.md) . Mezi první klauzulí `from` a poslední klauzulí `select` nebo `group` může obsahovat jednu nebo více z těchto volitelných klauzulí: [WHERE](../language-reference/keywords/where-clause.md), [OrderBy](../language-reference/keywords/orderby-clause.md), [Join](../language-reference/keywords/join-clause.md), [let](../language-reference/keywords/let-clause.md) a ještě další klauzule [from](../language-reference/keywords/from-clause.md) . Můžete také použít klíčové slovo [into](../language-reference/keywords/into.md) k povolení výsledku `join` nebo `group` klauzule, která slouží jako zdroj pro další klauzule dotazu ve stejném výrazu dotazu.

### <a name="query-variable"></a>Proměnná dotazu

V LINQ je proměnná dotazu jakákoli proměnná, která namísto *výsledků* dotazu ukládá *dotaz* . Přesněji řečeno je proměnná dotazu vždy vyčíslitelného typu, který vytvoří sekvenci prvků při iteraci v příkazu `foreach` nebo přímého volání své `IEnumerator.MoveNext` metody.

Následující příklad kódu ukazuje jednoduchý výraz dotazu s jedním zdrojem dat, jednou klauzulí filtrování, jednou klauzulí řazení a bez transformace zdrojových elementů. Klauzule `select` ukončí dotaz.

[!code-csharp[csrefQueryExpBasics#49](~/samples/snippets/csharp/concepts/linq/query-expression-basics_5.cs)]

V předchozím příkladu je `scoreQuery` *proměnnou dotazu,* která je někdy označována jako pouze *dotaz*. Proměnná dotazu ukládá žádná skutečná data výsledků, která jsou vytvořena ve smyčce `foreach`. A když se příkaz `foreach` spustí, výsledky dotazu se nevrátí pomocí proměnné dotazu `scoreQuery`. Místo toho jsou vráceny prostřednictvím proměnné iterace `testScore`. Proměnnou `scoreQuery` lze iterovat v druhé smyčce `foreach`. Výsledkem bude stejné výsledky, pokud to není ani upravený zdroj dat.

Proměnná dotazu může uložit dotaz, který je vyjádřen v syntaxi dotazu nebo syntaxi metody, nebo kombinaci dvou. V následujících příkladech jsou proměnné dotazu `queryMajorCities` i `queryMajorCities2`:

[!code-csharp[csrefQueryExpBasics#50](~/samples/snippets/csharp/concepts/linq/query-expression-basics_6.cs)]

Na druhé straně následující dva příklady znázorňují proměnné, které nejsou proměnné dotazů, i když každá z nich je inicializována s dotazem. Nejedná se o proměnné dotazů, protože ukládají výsledky:

[!code-csharp[csrefQueryExpBasics#51](~/samples/snippets/csharp/concepts/linq/query-expression-basics_7.cs)]

Další informace o různých způsobech, jak vyjádřit dotazy, naleznete [v tématu Syntaxe dotazu a syntaxe metody v jazyce LINQ](../programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md).

#### <a name="explicit-and-implicit-typing-of-query-variables"></a>Explicitní a implicitní zadání proměnných dotazu

Tato dokumentace obvykle poskytuje explicitní typ proměnné dotazu, aby se zobrazil vztah typu mezi proměnnou dotazu a [klauzulí Select](../language-reference/keywords/select-clause.md). Můžete však také použít klíčové slovo [var](../language-reference/keywords/var.md) k tomu, aby kompilátor mohl odvodit typ proměnné dotazu (nebo jakékoli jiné místní proměnné) v době kompilace. Například příklad dotazu, který byl zobrazen dříve v tomto tématu, lze vyjádřit také pomocí implicitního zadání:

[!code-csharp[csrefQueryExpBasics#52](~/samples/snippets/csharp/concepts/linq/query-expression-basics_8.cs)]

Další informace naleznete v tématu [implicitně typované lokální proměnné](../programming-guide/classes-and-structs/implicitly-typed-local-variables.md) a [vztahy typů v operacích dotazu LINQ](../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).

### <a name="starting-a-query-expression"></a>Spuštění výrazu dotazu

Výraz dotazu musí začínat klauzulí `from`. Určuje zdroj dat spolu s proměnnou rozsahu. Proměnná Range reprezentuje každý následný prvek ve zdrojové sekvenci, protože je zdrojová sekvence procházena. Proměnná rozsahu je typově silný na základě typu prvků ve zdroji dat. V následujícím příkladu, protože `countries` je pole `Country` objektů, proměnná rozsahu je také zadána jako `Country`. Vzhledem k tomu, že je proměnná rozsahu silného typu, můžete použít operátor tečka pro přístup k některým z dostupných členů typu.

[!code-csharp[csrefQueryExpBasics#53](~/samples/snippets/csharp/concepts/linq/query-expression-basics_9.cs)]

Proměnná rozsahu je v oboru, dokud se neukončí dotaz buď středníkem, nebo klauzulí *pokračování* .

Výraz dotazu může obsahovat více klauzulí `from`. Pokud je každý prvek ve zdrojové sekvenci sám kolekcí nebo obsahuje kolekci, použijte další klauzule `from`. Předpokládejme například, že máte kolekci `Country` objektů, z nichž každá obsahuje kolekci objektů `City` s názvem `Cities`. Chcete-li zadat dotaz na objekty `City` v každém `Country`, použijte dvě klauzule `from`, jak je znázorněno zde:

[!code-csharp[csrefQueryExpBasics#54](~/samples/snippets/csharp/concepts/linq/query-expression-basics_10.cs)]

Další informace naleznete v tématu [from – klauzule](../language-reference/keywords/from-clause.md).

### <a name="ending-a-query-expression"></a>Ukončení výrazu dotazu

Výraz dotazu musí být ukončen buď klauzulí `group`, nebo klauzulí `select`.

#### <a name="group-clause"></a>group – klauzule

Použijte klauzuli `group` pro vytvoření posloupnosti skupin uspořádaných podle klíče, který zadáte. Klíč může být libovolný datový typ. Následující dotaz například vytvoří sekvenci skupin, které obsahují jeden nebo více `Country` objektů a jejichž klíč je `char` hodnota.

[!code-csharp[csrefQueryExpBasics#55](~/samples/snippets/csharp/concepts/linq/query-expression-basics_11.cs)]

Další informace o seskupování naleznete v tématu [Group Group](../language-reference/keywords/group-clause.md).

#### <a name="select-clause"></a>select – klauzule (C#)

Použijte klauzuli `select` k tvorbě všech ostatních typů sekvencí. Jednoduchá klauzule `select` pouze vytvoří sekvenci stejného typu objektů jako objekty, které jsou obsaženy ve zdroji dat. V tomto příkladu zdroj dat obsahuje `Country` objekty. Klauzule `orderby` pouze Seřadí prvky do nové objednávky a klauzule `select` vytvoří sekvenci přeřazených objektů `Country`.

[!code-csharp[csrefQueryExpBasics#56](~/samples/snippets/csharp/concepts/linq/query-expression-basics_12.cs)]

Klauzuli `select` lze použít pro transformaci zdrojových dat do sekvencí nových typů. Tato transformace se také nazývá *projekce*. V následujícím příkladu *obsahuje klauzule `select`* sekvenci anonymních typů, které obsahují pouze podmnožinu polí v původním prvku. Všimněte si, že nové objekty jsou inicializovány pomocí inicializátoru objektu.

[!code-csharp[csrefQueryExpBasics#57](~/samples/snippets/csharp/concepts/linq/query-expression-basics_13.cs)]

Další informace o všech způsobech, jak lze použít klauzuli `select` pro transformaci zdrojových dat, naleznete v tématu [Select klauzule](../language-reference/keywords/select-clause.md).

#### <a name="continuations-with-into"></a>Pokračování s "do"

Pomocí klíčového slova `into` v klauzuli `select` nebo `group` můžete vytvořit dočasný identifikátor, který ukládá dotaz. Tuto akci proveďte v případě, že je nutné provést další operace dotazování pro dotaz po operaci seskupení nebo výběru. V následujícím příkladu se `countries` seskupují podle populace v rozsahu 10 000 000. Po vytvoření těchto skupin se v dalších klauzulích odfiltrují některé skupiny a pak se skupiny seřadí ve vzestupném pořadí. Pro provedení těchto dalších operací je vyžadováno pokračování reprezentované `countryGroup`.

[!code-csharp[csrefQueryExpBasics#58](~/samples/snippets/csharp/concepts/linq/query-expression-basics_14.cs)]

Další informace najdete [v tématu.](../language-reference/keywords/into.md)

### <a name="filtering-ordering-and-joining"></a>Filtrování, řazení a spojování

Mezi počáteční klauzulí `from` a koncová klauzule `select` nebo `group` jsou všechny ostatní klauzule (`where`, `join`, `orderby`, `from`, `let`) volitelné. Kterákoli z volitelných klauzulí může být v těle dotazu použita v nenulovém nebo více časech.

#### <a name="where-clause"></a>where – klauzule

Použijte klauzuli `where` pro filtrování prvků ze zdrojových dat na základě jednoho nebo více výrazů predikátů. Klauzule `where` v následujícím příkladu má jeden predikát se dvěma podmínkami.

[!code-csharp[csrefQueryExpBasics#59](~/samples/snippets/csharp/concepts/linq/query-expression-basics_15.cs)]

Další informace naleznete v tématu [Where klauzule](../language-reference/keywords/where-clause.md).

#### <a name="orderby-clause"></a>orderby – klauzule

Použijte klauzuli `orderby` pro řazení výsledků ve vzestupném nebo sestupném pořadí. Můžete také zadat sekundární objednávky řazení. Následující příklad provádí primární řazení na `country` objekty pomocí vlastnosti `Area`. Pak provede sekundární řazení pomocí vlastnosti `Population`.

[!code-csharp[csrefQueryExpBasics#60](~/samples/snippets/csharp/concepts/linq/query-expression-basics_16.cs)]

Klíčové slovo `ascending` je volitelné; Jedná se o výchozí pořadí řazení, pokud není zadána žádná objednávka. Další informace naleznete v tématu [OrderBy klauzule](../language-reference/keywords/orderby-clause.md).

#### <a name="join-clause"></a>join – klauzule

Použijte klauzuli `join` pro přidružení a/nebo kombinování prvků z jednoho zdroje dat s prvky z jiného zdroje dat na základě porovnání rovnosti mezi zadanými klíči v každém elementu. V LINQ jsou operace join prováděny na sekvencích objektů, jejichž prvky jsou různé typy. Po spojení dvou sekvencí je nutné použít příkaz `select` nebo `group` k určení prvku, který má být uložen ve výstupní sekvenci. Můžete také použít anonymní typ ke kombinování vlastností z každé sady přidružených prvků do nového typu pro výstupní sekvenci. Následující příklad přidruží `prod` objektů, jejichž vlastnost `Category` odpovídá jedné z kategorií v poli `categories` řetězců. Produkty, jejichž `Category` se neshodují s žádným řetězcem v `categories` jsou odfiltrovány. Příkaz `select` vytvoří nový typ, jehož vlastnosti jsou odebírány z `cat` a `prod`.

[!code-csharp[csrefQueryExpBasics#61](~/samples/snippets/csharp/concepts/linq/query-expression-basics_17.cs)]

Můžete také provést spojení se skupinou, a to uložením výsledků `join` operace do dočasné proměnné pomocí klíčového slova [into](../language-reference/keywords/into.md) . Další informace najdete v tématu [klauzule JOIN](../language-reference/keywords/join-clause.md).

#### <a name="let-clause"></a>let – klauzule 

Použijte klauzuli `let` pro uložení výsledku výrazu, jako je například volání metody, do nové proměnné rozsahu. V následujícím příkladu proměnná rozsahu `firstName` ukládá první prvek pole řetězců, který je vrácen `Split`.

[!code-csharp[csrefQueryExpBasics#62](~/samples/snippets/csharp/concepts/linq/query-expression-basics_18.cs)]

Další informace naleznete v [klauzuli let](../language-reference/keywords/let-clause.md).

### <a name="subqueries-in-a-query-expression"></a>Poddotazy ve výrazu dotazu

Klauzule dotazu může obsahovat výraz dotazu, který se někdy označuje jako *poddotaz*. Každý poddotaz začíná svou vlastní klauzulí `from`, která nutně neukazuje na stejný zdroj dat v první klauzuli `from`. Následující dotaz například ukazuje výraz dotazu, který se používá v příkazu SELECT k načtení výsledků operace seskupení.

[!code-csharp[csrefQueryExpBasics#63](~/samples/snippets/csharp/concepts/linq/query-expression-basics_19.cs)]

Další informace najdete v tématu věnovaném [provádění poddotazů u operace seskupení](perform-a-subquery-on-a-grouping-operation.md).

## <a name="see-also"></a>Viz také:

- [C#Průvodce programováním](../programming-guide/index.md)
- [ (LINQ)](index.md)
- [Klíčová slova dotazu (LINQ)](../language-reference/keywords/query-keywords.md)
- [Přehled standardních operátorů dotazů](../programming-guide/concepts/linq/standard-query-operators-overview.md)
