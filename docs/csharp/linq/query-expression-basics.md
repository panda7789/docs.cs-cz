---
title: "Základy výrazů dotazů"
description: "Seznámíte se základními pojmy související s výrazy dotazů"
keywords: "Rozhraní .NET, rozhraní .NET core, C#"
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 11/30/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: 027db1f8-346f-44d2-a16e-043fcea3a4e0
ms.openlocfilehash: dbb77f57c7f3484930e1639da501ab828e1c2070
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="query-expression-basics"></a>Základy výrazů dotazů

## <a name="what-is-a-query-and-what-does-it-do"></a>Co je dotaz a co se dělá? 

 A *dotazu* je sada pokynů, které popisuje, jaká data načíst z do daného zdroje dat (nebo zdroje) a jaké tvar a organizace musí mít vrácená data. Dotaz se liší od výsledky, které vytváří.  
  
 Obecně platí zdrojová data jsou logicky uspořádána jako pořadí elementů stejného druhu. Například tabulce databáze SQL obsahuje posloupnost řádků. V souboru XML je "posloupnost" elementů XML (i když tyto jsou uspořádány hierarchicky ve stromové struktuře). Obsahuje kolekci v paměti pořadí objektů. 
  
 Z hlediska aplikace konkrétního typu a strukturu původního zdroje dat není důležité. Aplikace vždy zobrazí zdroj dat jako <xref:System.Collections.Generic.IEnumerable%601> nebo <xref:System.Linq.IQueryable%601> kolekce. Například v technologii LINQ to XML, zdrojová data jsou dostupná jako `IEnumerable` \< <xref:System.Xml.Linq.XElement>>.  
  
 Zadané pořadí tento zdroj, dotaz může proveďte jednu z tři věci:  
  
-   Načtěte podmnožinu elementy k vytvoření nového pořadí beze změny jednotlivé prvky. Dotaz může pak seřaďte nebo skupiny vrácený pořadí různými způsoby, jak je znázorněno v následujícím příkladu (předpokládá `scores` je `int[]`):  
  
     [!code-csharp[csrefQueryExpBasics#45](../../../samples/snippets/csharp/concepts/linq/query-expression-basics_1.cs)]  
  
-   Načtení pořadí elementů jako v předchozím příkladu ale transformují je na nový typ objektu. Například může načíst dotaz pouze poslední názvy z určité záznamy o zákaznících ve zdroji dat. Nebo může načíst úplný záznam a pak použít při vytváření jiný typ objektu v paměti nebo dokonce data XML před vygenerováním pořadí konečný výsledek. Následující příklad ukazuje projekce z `int` k `string`. Všimněte si, nový typ `highScoresQuery`.  
  
     [!code-csharp[csrefQueryExpBasics#46](../../../samples/snippets/csharp/concepts/linq/query-expression-basics_2.cs)]  
  
-   Načtěte hodnotu singleton o zdrojová data, jako například:  
  
    -   Počet elementů, které splňují určité podmínky.  
  
    -   Element, který má nejvyšší nebo nejnižší hodnotu.  
  
    -   První prvek, který odpovídá podmínce nebo součet konkrétní hodnoty v zadané sadě elementů. Například následující dotaz vrátí počet skóre větší než 80 z `scores` celé číslo pole:  
  
     [!code-csharp[csrefQueryExpBasics#47](../../../samples/snippets/csharp/concepts/linq/query-expression-basics_3.cs)]  
  
     V předchozím příkladu, Všimněte si použití v závorkách výrazu dotazu před volání `Count` metoda. To lze vyjádřit pomocí novou proměnnou pro uložení konkrétní výsledek. Tento postup je lépe čitelný, protože udržuje odděleně od dotaz, který ukládá výsledek proměnné, která ukládá dotazu.  
  
     [!code-csharp[csrefQueryExpBasics#48](../../../samples/snippets/csharp/concepts/linq/query-expression-basics_4.cs)]  
  
 V předchozím příkladu je spustit dotaz ve volání `Count`, protože `Count` musí iterace v výsledky, aby bylo možné zjistit počet elementů vrácený `highScoresQuery`.  
  
## <a name="what-is-a-query-expression"></a>Co je výrazu dotazu?  

 A *dotaz výraz* je dotaz vyjádřené v syntaxi dotazu. Výraz dotazu je první třídy jazyka konstrukce. Je stejně jako libovolný jiný výraz a mohou být používány jakýkoliv kontext, ve kterém je platný výraz jazyka C#. Výraz dotazu se skládá z sadu klauzule napsané v deklarativní syntaxi podobně jako SQL nebo XQuery. Každý klauzule obsahuje jeden nebo více C# výrazy a těchto výrazů může sami výrazu dotazu nebo obsahovat výrazu dotazu.  
  
 Výraz dotazu musí začínat [z](../language-reference/keywords/from-clause.md) klauzule a musí končit [vyberte](../language-reference/keywords/select-clause.md) nebo [skupiny](../language-reference/keywords/group-clause.md) klauzule. Mezi první `from` klauzule a poslední `select` nebo `group` klauzule, může obsahovat jednu nebo více těchto volitelné klauzule: [kde](../language-reference/keywords/where-clause.md), [orderby](../language-reference/keywords/orderby-clause.md), [spojení ](../language-reference/keywords/join-clause.md), [umožní](../language-reference/keywords/let-clause.md) a i další [z](../language-reference/keywords/from-clause.md) klauzule. Můžete také [do](../language-reference/keywords/into.md) – klíčové slovo povolit výsledek `join` nebo `group` klauzuli, která bude sloužit jako zdroj pro další dotaz klauzule ve stejném výrazu dotazu.  
  
### <a name="query-variable"></a>Proměnné dotazu  
 
 V technologii LINQ, je proměnná dotazu všechny proměnné, která ukládá *dotazu* místo *výsledky* dotazu. Přesněji řečeno, proměnné dotazu je vždy vyčíslitelná typ, který vytvoří pořadí prvků, když ho je vstupní přes `foreach` příkaz nebo přímé volání jeho `IEnumerator.MoveNext` metoda.  
  
 Následující příklad kódu ukazuje výraz jednoduchý dotaz s jedním zdrojem dat, jednu klauzuli filtrování, řazení jednu klauzuli a žádná transformace zdrojové elementy. `select` Klauzule končí dotazu.  
  
 [!code-csharp[csrefQueryExpBasics#49](../../../samples/snippets/csharp/concepts/linq/query-expression-basics_5.cs)]  
  
 V předchozím příkladu `scoreQuery` je *proměnné dotazu* které se někdy označuje jako právě *dotazu*. Proměnná dotazu ukládá žádný skutečný výsledek data, která se vytvářejí v `foreach` smyčky. A kdy `foreach` vykonávání příkazu pomocí proměnné dotazu nebudou zobrazeny výsledky dotazu `scoreQuery`. Místo toho jsou vráceny prostřednictvím proměnné iterace `testScore`. `scoreQuery` Proměnná může být vstupní druhý `foreach` smyčky. Stejné výsledky vytvoří tak dlouho, dokud ho ani zdroj dat byla změněna.  
  
 Proměnné dotazu uložit dotaz, který je vyjádřena v syntaxi dotazu nebo syntaxe využívající metody nebo kombinaci obojího. Následující příklady jak `queryMajorCities` a `queryMajorCities2` jsou proměnné dotazu:  
  
 [!code-csharp[csrefQueryExpBasics#50](../../../samples/snippets/csharp/concepts/linq/query-expression-basics_6.cs)]  
  
 Na druhé straně následující dva příklady ukazují, proměnné, které nejsou proměnné dotazu i prostřednictvím každý inicializován s dotazem. Nejsou se proměnné dotazu, protože ukládají výsledky:  
  
 [!code-csharp[csrefQueryExpBasics#51](../../../samples/snippets/csharp/concepts/linq/query-expression-basics_7.cs)]  
  
 Další informace o různé způsoby, jak expresní dotazů najdete v tématu [syntaxe využívající dotazy a syntaxe využívající metody v technologii LINQ](../programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md).  
  
#### <a name="explicit-and-implicit-typing-of-query-variables"></a>Explicitní a implicitní zadáním proměnných dotazu  
 
 Tato dokumentace obvykle poskytuje explicitní typ proměnné dotazu chcete-li zobrazit typ vztah mezi proměnnou dotazu a [klauzuli select](../language-reference/keywords/select-clause.md). Ale můžete také použít [var](../language-reference/keywords/var.md) – klíčové slovo kompilátoru k odvození typu proměnné dotazu (nebo jiné místní proměnné) v čase kompilace. Například příklad dotazu, který je uvedený výše v tomto tématu lze také vyjádřit pomocí implicitní zadáním:  
  
 [!code-csharp[csrefQueryExpBasics#52](../../../samples/snippets/csharp/concepts/linq/query-expression-basics_8.cs)]  
  
 Další informace najdete v tématu [implicitně typované lokální proměnné](../programming-guide/classes-and-structs/implicitly-typed-local-variables.md) a [vztahy typů v LINQ dotazu operations](../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).  
  
### <a name="starting-a-query-expression"></a>Spouštění výrazu dotazu  
 
 Výraz dotazu musí začínat `from` klauzule. Určuje zdroj dat společně s proměnnou rozsahu. Proměnná rozsahu představuje všechny následné prvky ve zdrojové sekvence je právě provázán zdrojové sekvence. Proměnná rozsahu je silného typu na základě typu elementů v datovém zdroji. V následujícím příkladu protože `countries` je pole `Country` objekty, proměnná rozsahu je také zadán jako `Country`. Vzhledem k tomu, že proměnná rozsahu je silného typu, můžete pro přístup k žádné dostupné členy typu operátor tečky.  
  
 [!code-csharp[csrefQueryExpBasics#53](../../../samples/snippets/csharp/concepts/linq/query-expression-basics_9.cs)]  
  
 Proměnná rozsahu je v oboru, dokud dotazu je byl ukončen s středníkem nebo s *pokračování* klauzule.  
  
 Výraz dotazu může obsahovat více `from` klauzule. Použití další `from` klauzule při každý prvek v zdrojové sekvence je samotný soubor nebo obsahuje kolekci. Předpokládejme například, že máte kolekci `Country` objekty, z nichž každý obsahuje kolekci `City` objektů s názvem `Cities`. Dotaz `City` objektů v každé `Country`, použijte dva `from` klauzule, jak je vidět tady:  
  
 [!code-csharp[csrefQueryExpBasics#54](../../../samples/snippets/csharp/concepts/linq/query-expression-basics_10.cs)]  
  
 Další informace najdete v tématu [klauzule from](../language-reference/keywords/from-clause.md).  
  
### <a name="ending-a-query-expression"></a>Koncová výrazu dotazu  
 
 Buď musí končit výrazu dotazu `group` klauzule nebo `select` klauzule.  
  
#### <a name="group-clause"></a>group – klauzule  
 
 Použití `group` klauzule k vytvoření pořadí skupin uspořádané podle klíče, který zadáte. Klíč může být jakéhokoli datového typu. Například následující dotaz vytvoří posloupnost skupiny, která obsahuje jeden nebo více `Country` objekty a jehož klíč je `char` hodnotu.  
  
 [!code-csharp[csrefQueryExpBasics#55](../../../samples/snippets/csharp/concepts/linq/query-expression-basics_11.cs)]  
  
 Další informace o seskupení najdete v tématu [group – klauzule](../language-reference/keywords/group-clause.md).  
  
#### <a name="select-clause"></a>select – klauzule (C#)  
 Použití `select` klauzule k vytvoření všechny ostatní typy pořadí. Jednoduchý `select` klauzule právě vytváří pořadí stejného typu objektů jako objekty, které jsou obsaženy v datovém zdroji. V tomto příkladu obsahuje zdroj dat `Country` objekty. `orderby` Klauzule právě seřadí elementy do nové pořadí a `select` klauzule vytváří posloupnost uspořádaný `Country` objekty.  
  
 [!code-csharp[csrefQueryExpBasics#56](../../../samples/snippets/csharp/concepts/linq/query-expression-basics_12.cs)]  
  
 `select` Klauzuli lze použít k transformaci zdrojová data do pořadí nových typů. Tato transformace se také s názvem *projekce*. V následujícím příkladu `select` klauzule *projekty* pořadí anonymní typy, který obsahuje pouze podmnožinu pole v původní elementu. Všimněte si, že nové objekty jsou inicializovány pomocí inicializátoru objektu.  
  
 [!code-csharp[csrefQueryExpBasics#57](../../../samples/snippets/csharp/concepts/linq/query-expression-basics_13.cs)]  
  
 Další informace o tom, jak, `select` klauzuli lze použít transformace zdrojová data, najdete v článku [klauzuli select](../language-reference/keywords/select-clause.md).  
  
#### <a name="continuations-with-into"></a>Pokračování s "do"  
 
 Můžete použít `into` – klíčové slovo v `select` nebo `group` klauzule vytvořit dočasný identifikátor, který ukládá dotazu. To provést, když je nutné provést operace další dotazů na dotazu po seskupení nebo vybrat operaci. V následujícím příkladu `countries` se seskupí podle naplnění v oblastech 10 milionů. Jakmile tyto skupiny jsou vytvořené, další klauzule filtru se některé skupiny a pak na řazení skupiny ve vzestupném pořadí. K provedení těchto dalších operací, o pokračování reprezentována `countryGroup` je vyžadován.  
  
 [!code-csharp[csrefQueryExpBasics#58](../../../samples/snippets/csharp/concepts/linq/query-expression-basics_14.cs)]  
  
 Další informace najdete v tématu [do](../language-reference/keywords/into.md).  
  
### <a name="filtering-ordering-and-joining"></a>Filtrování, řazení a připojení

 Mezi počáteční `from` klauzule a koncové `select` nebo `group` klauzule, všechny ostatní klauzule (`where`, `join`, `orderby`, `from`, `let`) jsou volitelné. Všechny volitelné klauzule lze časy nula nebo více než jednou. v textu dotazu.  
  
#### <a name="where-clause"></a>where – klauzule  

 Použití `where` klauzule filtrovat prvky ze zdrojových dat podle jednoho nebo více výrazů predikátem. `where` Klauzule v následujícím příkladu má jeden predikát s dvě podmínky.  
  
 [!code-csharp[csrefQueryExpBasics#59](../../../samples/snippets/csharp/concepts/linq/query-expression-basics_15.cs)]  
  
 Další informace najdete v tématu [kde klauzule](../language-reference/keywords/where-clause.md).  
  
#### <a name="orderby-clause"></a>orderby – klauzule

 Použití `orderby` klauzule k řazení výsledků ve vzestupném nebo sestupném pořadí. Můžete také zadat sekundární pořadí řazení. Následující příklad provede primární řazení `country` objekty pomocí `Area` vlastnost. Potom provede sekundární řazení pomocí `Population` vlastnost.  
  
 [!code-csharp[csrefQueryExpBasics#60](../../../samples/snippets/csharp/concepts/linq/query-expression-basics_16.cs)]  
  
 `ascending` – Klíčové slovo je volitelná; Pokud je zadáno žádné pořadí je výchozí pořadí řazení. Další informace najdete v tématu [klauzule orderby](../language-reference/keywords/orderby-clause.md).  
  
#### <a name="join-clause"></a>join – klauzule

 Použití `join` klauzule přidružit nebo zkombinovat elementy z jeden zdroj dat s elementy z jiného zdroje dat podle porovnání rovnosti mezi zadanými klíči v jednotlivých prvků. V technologii LINQ jsou operace spojení provést v pořadí, jehož elementy jsou různé typy objektů. Po připojení dvě pořadí, je nutné použít `select` nebo `group` lze zadat které elementu, který chcete uložit výstupní sekvenci. Anonymní typ můžete také kombinovat vlastnosti ze všech sad přidružených elementů do nový typ pro výstupní sekvenci. V následujícím příkladu `prod` objekty, jehož `Category` vlastnost odpovídá jednomu z kategorií v `categories` pole řetězců. Produkty jejichž `Category` neodpovídá žádné řetězec v `categories` jsou odfiltrována. `select` Příkaz projekty nový typ, jehož vlastnosti jsou převzaty z obou `cat` a `prod`.  
  
 [!code-csharp[csrefQueryExpBasics#61](../../../samples/snippets/csharp/concepts/linq/query-expression-basics_17.cs)]  
  
 Můžete také provést připojení k skupiny uložením výsledky `join` operace do dočasné proměnné pomocí [do](../language-reference/keywords/into.md) – klíčové slovo. Další informace najdete v tématu [klauzuli join](../language-reference/keywords/join-clause.md).  
  
#### <a name="let-clause"></a>let – klauzule 

 Použití `let` klauzule a uložit výsledek výrazu, jako je například volání metody, v nové proměnné rozsahu. V následujícím příkladu, proměnnou rozsahu `firstName` ukládá první prvek pole řetězce, které se vrátí po `Split`.  
  
 [!code-csharp[csrefQueryExpBasics#62](../../../samples/snippets/csharp/concepts/linq/query-expression-basics_18.cs)]  
  
 Další informace najdete v tématu [let – klauzule](../language-reference/keywords/let-clause.md).  
  
### <a name="subqueries-in-a-query-expression"></a>Poddotazy ve výrazu dotazu  

 Samotný dotaz klauzule může obsahovat výrazu dotazu, které se někdy označuje jako *poddotazu*. Každý poddotazu začíná vlastní `from` klauzule, který není nutně cesta ke zdroji dat v prvním `from` klauzule. Například následující dotaz zobrazí výrazu dotazu, který se používá v příkazu select se načíst výsledky operace seskupení.  
  
 [!code-csharp[csrefQueryExpBasics#63](../../../samples/snippets/csharp/concepts/linq/query-expression-basics_19.cs)]  
  
 Další informace najdete v tématu [postupy: provádění poddotazů na skupinách](perform-a-subquery-on-a-grouping-operation.md).  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním C#](../programming-guide/index.md)  
 [LINQ – výrazy dotazů](index.md)  
 [Klíčová slova dotazu (LINQ)](../language-reference/keywords/query-keywords.md)  
 [Přehled standardních operátorů dotazu](../programming-guide/concepts/linq/standard-query-operators-overview.md)
