---
title: 'Návod: Generování SQL'
ms.date: 03/30/2017
ms.assetid: 16c38aaa-9927-4f3c-ab0f-81636cce57a3
ms.openlocfilehash: 09b5a3c2dea5cd0483d617ee8064b41dc19c3374
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248292"
---
# <a name="walkthrough-sql-generation"></a>Návod: Generování SQL

Toto téma ukazuje, jak se ve [zprostředkovateli ukázky](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0)vyskytují generování SQL. Následující Entity SQL dotaz používá model, který je součástí poskytovatele ukázkových:

```sql
SELECT  j1.ProductId, j1.ProductName, j1.CategoryName, j2.ShipCountry, j2.ProductId
FROM (  SELECT P.ProductName, P.ProductId, P.Category.CategoryName
        FROM NorthwindEntities.Products AS P) as j1
INNER JOIN (SELECT OD.ProductId, OD.Order.ShipCountry as ShipCountry
            FROM NorthwindEntities.OrderDetails AS OD) as j2
            ON j1.ProductId == j2.ProductId
```

Dotaz vytvoří následující výstupní strom příkazů, který se předává poskytovateli:

```
DbQueryCommandTree
|_Parameters
|_Query : Collection{Record['C1'=Edm.Int32, 'ProductID'=Edm.Int32, 'ProductName'=Edm.String, 'CategoryName'=Edm.String, 'ShipCountry'=Edm.String, 'ProductID1'=Edm.Int32]}
  |_Project
    |_Input : 'Join4'
    | |_InnerJoin
    |   |_Left : 'Join1'
    |   | |_LeftOuterJoin
    |   |   |_Left : 'Extent1'
    |   |   | |_Scan : dbo.Products
    |   |   |_Right : 'Extent2'
    |   |   | |_Scan : dbo.Categories
    |   |   |_JoinCondition
    |   |     |_
    |   |       |_Var(Extent1).CategoryID
    |   |       |_=
    |   |       |_Var(Extent2).CategoryID
    |   |_Right : 'Join3'
    |   | |_LeftOuterJoin
    |   |   |_Left : 'Extent3'
    |   |   | |_Scan : dbo.OrderDetails
    |   |   |_Right : 'Join2'
    |   |   | |_LeftOuterJoin
    |   |   |   |_Left : 'Extent4'
    |   |   |   | |_Scan : dbo.Orders
    |   |   |   |_Right : 'Extent5'
    |   |   |   | |_Scan : dbo.InternationalOrders
    |   |   |   |_JoinCondition
    |   |   |     |_
    |   |   |       |_Var(Extent4).OrderID
    |   |   |       |_=
    |   |   |       |_Var(Extent5).OrderID
    |   |   |_JoinCondition
    |   |     |_
    |   |       |_Var(Extent3).OrderID
    |   |       |_=
    |   |       |_Var(Join2).Extent4.OrderID
    |   |_JoinCondition
    |     |_
    |       |_Var(Join1).Extent1.ProductID
    |       |_=
    |       |_Var(Join3).Extent3.ProductID
    |_Projection
      |_NewInstance : Record['C1'=Edm.Int32, 'ProductID'=Edm.Int32, 'ProductName'=Edm.String, 'CategoryName'=Edm.String, 'ShipCountry'=Edm.String, 'ProductID1'=Edm.Int32]
        |_Column : 'C1'
        | |_1
        |_Column : 'ProductID'
        | |_Var(Join4).Join1.Extent1.ProductID
        |_Column : 'ProductName'
        | |_Var(Join4).Join1.Extent1.ProductName
        |_Column : 'CategoryName'
        | |_Var(Join4).Join1.Extent2.CategoryName
        |_Column : 'ShipCountry'
        | |_Var(Join4).Join3.Join2.Extent4.ShipCountry
        |_Column : 'ProductID1'
          |_Var(Join4).Join3.Extent3.ProductID
```

 Toto téma popisuje, jak přeložit tento výstupní strom příkazů do následujících příkazů SQL.

```sql
SELECT
1 AS [C1],
[Extent1].[ProductID] AS [ProductID],
[Extent1].[ProductName] AS [ProductName],
[Extent2].[CategoryName] AS [CategoryName],
[Join3].[ShipCountry] AS [ShipCountry],
[Join3].[ProductID] AS [ProductID1]
FROM   [dbo].[Products] AS [Extent1]
LEFT OUTER JOIN [dbo].[Categories] AS [Extent2] ON [Extent1].[CategoryID] = [Extent2].[CategoryID]
INNER JOIN
(SELECT [Extent3].[OrderID] AS [OrderID1], [Extent3].[ProductID] AS [ProductID], [Extent3].[UnitPrice] AS [UnitPrice], [Extent3].[Quantity] AS [Quantity], [Extent3].[Discount] AS [Discount], [Join2].[OrderID2], [Join2].[CustomerID], [Join2].[EmployeeID], [Join2].[OrderDate], [Join2].[RequiredDate], [Join2].[ShippedDate], [Join2].[Freight], [Join2].[ShipName], [Join2].[ShipAddress], [Join2].[ShipCity], [Join2].[ShipRegion], [Join2].[ShipPostalCode], [Join2].[ShipCountry], [Join2].[OrderID3], [Join2].[CustomsDescription], [Join2].[ExciseTax]
FROM  [dbo].[OrderDetails] AS [Extent3]
LEFT OUTER JOIN
      (SELECT [Extent4].[OrderID] AS [OrderID2], [Extent4].[CustomerID] AS [CustomerID], [Extent4].[EmployeeID] AS [EmployeeID], [Extent4].[OrderDate] AS [OrderDate], [Extent4].[RequiredDate] AS [RequiredDate], [Extent4].[ShippedDate] AS [ShippedDate], [Extent4].[Freight] AS [Freight], [Extent4].[ShipName] AS [ShipName], [Extent4].[ShipAddress] AS [ShipAddress], [Extent4].[ShipCity] AS [ShipCity], [Extent4].[ShipRegion] AS [ShipRegion], [Extent4].[ShipPostalCode] AS [ShipPostalCode], [Extent4].[ShipCountry] AS [ShipCountry], [Extent5].[OrderID] AS [OrderID3], [Extent5].[CustomsDescription] AS [CustomsDescription], [Extent5].[ExciseTax] AS [ExciseTax]
FROM  [dbo].[Orders] AS [Extent4]
LEFT OUTER JOIN [dbo].[InternationalOrders] AS [Extent5] ON [Extent4].[OrderID] = [Extent5].[OrderID]
      ) AS [Join2] ON [Extent3].[OrderID] = [Join2].[OrderID2]
   ) AS [Join3] ON [Extent1].[ProductID] = [Join3].[ProductID]
```

## <a name="first-phase-of-sql-generation-visiting-the-expression-tree"></a>První fáze generování SQL: Návštěvy stromu výrazů

Následující obrázek znázorňuje počáteční prázdný stav návštěvníka.  V tomto tématu jsou zobrazeny pouze vlastnosti, které jsou relevantní pro vysvětlení návodu.

![Diagram](./media/430180f5-4fb9-4bc3-8589-d566512d9703.gif "430180f5-4fb9-4bc3-8589-d566512d9703")

Když je uzel projektu navštíven, VisitInputExpression se volá za jeho vstup (Join4), který spouští návštěvu Join4 metodou VisitJoinExpression. Vzhledem k tomu, že se jedná o spojení na nejvyšší úrovni, IsParentAJoin vrátí hodnotu false a vytvoří se nový SqlSelectStatement (SelectStatement0) a vloží se do zásobníku příkazů SELECT. V tabulce symbolů je také zadán nový obor (scope0). Po navštívení prvního (levého) vstupu spojení se v zásobníku IsParentAJoin vloží hodnota true. Stav návštěvníka, jak je znázorněno na následujícím obrázku, je uveden přímo před Join1, což je levý vstup Join4.

![Diagram](./media/406d4f5f-6166-44ea-8e74-c5001d5d5d79.gif "406d4f5f-6166-44ea-8e74-c5001d5d5d79")

Když se metoda JOIN navštíví přes Join4, IsParentAJoin je true, takže znovu použije aktuální příkaz SELECT SelectStatement0. Je zadán nový obor (OborContoso1). Než navštívíte jeho levou podřízenou položku, Extent1, bude do zásobníku IsParentAJoin vložena jiná hodnota true.

Při navštívení Extent1, protože IsParentAJoin vrátí hodnotu true, vrátí SqlBuilder obsahující "[dbo]. [Products] ". Ovládací prvek se vrátí do metody, která Join4 navštíví. Položka je vyjmuta z IsParentAJoin a je volána ProcessJoinInputResult, která připojuje výsledek návštěvy Extent1 do klauzule FROM v SelectStatement0. Vytvoří se nový symbol z symbol_Extent1 pro název vstupní vazby "Extent1", přidá se do FromExtents SelectStatement0 a také "as" a symbol_Extent1 jsou připojeny k klauzuli FROM. Do AllExtentNames pro "Extent1" se přidá nová položka s hodnotou 0. Do aktuálního oboru v tabulce symbolů se přidá nová položka, která přiřadí "Extent1" k jeho symbolu symbol_Extent1. Symbol_Extent1 je také přidáno do AllJoinExtentsu SqlSelectStatement.

Před otevřením správného vstupu Join1 je do klauzule FROM v SelectStatement0 přidána levá vnější spojení. Vzhledem k tomu, že správný vstup je výraz skenování, je hodnota true znovu vložena do zásobníku IsParentAJoin. Stav před návštěvou správného vstupu, jak je znázorněno na následujícím obrázku.

![Diagram](./media/ca62c31b-7ff6-4836-b209-e16166304fdc.gif "ca62c31b-7ff6-4836-b209-e16166304fdc")

Správný vstup je zpracován stejným způsobem jako levý vstup. Stav po navštívení správného vstupu je zobrazen na následujícím obrázku.

![Diagram](./media/cd2afa99-7256-4c63-aaa9-c2d13f18a3d8.gif "cd2afa99-7256-4c63-aaa9-c2d13f18a3d8")

Následující hodnota false se vloží do zásobníku IsParentAJoin a var podmínka Join (Extent1). KódKategorie = = var (Extent2). CategoryID je zpracována. Var (Extent1) se přeloží \<na symbol_Extent1 > po hledání v tabulce symbolů. Vzhledem k tomu, že instance je přeložena na jednoduchý symbol, jako výsledek zpracování var (Extent1). KódKategorie, SqlBuilder s \<symbol1 >. " KódKategorie – je vráceno. Podobně je zpracována druhá strana porovnání a výsledek návštěvy podmínky spojení je připojen k klauzuli FROM SelectStatement1 a hodnota false je z zásobníku IsParentAJoin vyjmuta.

V důsledku toho bylo Join1 kompletně zpracováno a rozsah je odebrán z tabulky symbolů.

Řízení se vrátí ke zpracování Join4, nadřazenému objektu Join1. Vzhledem k tomu, že podřízený znovu použil příkaz SELECT, jsou Join1 rozsahy nahrazeny jedním spojovacím \<symbolem joinSymbol_Join1 >. Do tabulky symbolů je také přidána nová položka pro přidružení Join1 k \<joinSymbol_Join1 >.

Další uzel, který se má zpracovat, je Join3, druhý podřízený člen Join4. V případě, že se jedná o pravou podřízenou položku, je do zásobníku IsParentAJoin vložena hodnota false. Stav návštěvníka v tomto okamžiku je znázorněn na následujícím obrázku.

![Diagram](./media/1ec61ed3-fcdd-4649-9089-24385be7e423.gif "1ec61ed3-fcdd-4649-9089-24385be7e423")

Pro Join3 vrátí IsParentAJoin hodnotu false a musí spustit nový SqlSelectStatement (SelectStatement1) a vložit ho do zásobníku. Zpracování pokračuje stejně jako v předchozích předchozích spojeních, nový obor je vložen do zásobníku a jsou zpracovány podřízené objekty. Levý podřízený objekt je rozsah (Extent3) a pravá podřízená položka je Join (Join2), která také musí začít nový SqlSelectStatement: SelectStatement2. Podřízené položky v Join2 jsou také rozsahy a jsou shrnuty do SelectStatement2.

Stav návštěvníka hned po navštívení Join2, ale před jeho následným zpracováním (ProcessJoinInputResult) se zobrazí na následujícím obrázku:

![Diagram](./media/7510346f-8b09-4c99-b411-40af239c3c4d.gif "7510346f-8b09-4c99-b411-40af239c3c4d")

Na předchozím obrázku je SelectStatement2 zobrazen jako volné plovoucí, protože byl odebrán ze zásobníku, ale nebyl dosud zpracován nadřazeným objektem. Je nutné jej přidat do části z nadřazené položky, ale není to úplný příkaz SQL bez klauzule SELECT. Takže v tomto okamžiku jsou výchozí sloupce (všechny sloupce vytvářené jeho vstupy) přidány do seznamu Select metodou AddDefaultColumns. AddDefaultColumns iterovat symboly v FromExtents a pro každý symbol přidá všechny sloupce v rozsahu. Pro jednoduchý symbol se vyhledá typ symbolu, který načte všechny jeho vlastnosti, které se mají přidat. Také naplní slovník AllColumnNames názvy sloupců. Dokončený SelectStatement2 je připojen k klauzuli FROM SelectStatement1.

V dalším kroku je vytvořen nový symbol spojení, který představuje Join2, je označený jako vnořené spojení a přidáno do AllJoinExtentsu SelectStatement1 a přidal se do tabulky symbolů.  Nyní je podmínka spojení Join3, var (Extent3). ČísloObjednávky = var (Join2). Extent4. ČísloObjednávky se musí zpracovat. Zpracování levé strany je podobné podmínce spojení Join1. Nicméně zpracování pravého a vedlejšího "var (Join2). Extent4. ČísloObjednávky se liší, protože je vyžadováno sloučení spojení.

Následující obrázek ukazuje stav návštěvníka přímo před DbPropertyExpression "var (Join2). Extent4. ČísloObjednávky se zpracovává.

Zvažte, jak "var (Join2). Extent4. ČísloObjednávky "se navštíví. Nejprve vlastnost instance "var (Join2). Extent4 "" se navštíví, což je další DbPropertyExpression, a první navštíví svou instanci "var (Join2)". V nejvyšším oboru v tabulce symbolů "Join2" překládá na \<joinSymbol_join2 >. V metodě návštěvy pro zpracování DbPropertyExpression "var (Join2). Extent4 "Všimněte si, že při návštěvě instance se vrátil symbol spojení, který je potřeba pro sloučení.

Vzhledem k tomu, že se jedná o vnořené spojení, vyhledáme vlastnost "Extent4" ve slovníku NameToExtent symbolu JOIN, vyřešte ji \<na symbol_Extent4 > a vrátíte novou SymbolPair\<(joinSymbol_join2 > \<, symbol_Extent4 >). Vzhledem k tomu, že dvojici symbolů je vráceno ze zpracování instance "var (Join2). Extent4. ČísloObjednávky ", vlastnost" ČísloObjednávky "je přeložena z ColumnPart páru symbolů (\<symbol_Extent4 >), který obsahuje seznam sloupců rozsahu, který představuje. Tedy "var (Join2). Extent4. ČísloObjednávky se přeloží na { \<joinSymbol_Join2 >, ".", \<symbol_OrderID >}.

Podobně se zpracovává podmínka spojení Join4. Ovládací prvek se vrátí metodě VisitInputExpression, která zpracovala nejvyšší nejvíc projektu. V FromExtentsi vráceného SelectStatement0 se vstup identifikuje jako Join a odstraní původní rozsahy a nahradí je novým rozsahem, a to pouze pomocí spojovacího symbolu. Tabulka symbolů je také aktualizována a příště je zpracována část projekce projektu. Řešení vlastností a sloučení rozsahů spojení je popsané výše.

![Diagram](./media/9456d6a9-ea2e-40ae-accc-a10e18e28b81.gif "9456d6a9-ea2e-40ae-accc-a10e18e28b81")

Nakonec se vytvoří následující SqlSelectStatement:

```
SELECT:
  "1", " AS ", "[C1]",
  <symbol_Extent1>, ".", "[ProductID]", " AS ", "[ProductID]",
  <symbol_Extent1>, ".", "[ProductName]", " AS ", "[ProductName]",
  <symbol_Extent2>, ".", "[CategoryName]", " AS ", "[CategoryName]",
  <joinSymbol_Join3>, ".", <symbol_ShipCountry>, " AS ", "[ShipCountry]",
  <joinSymbol_Join3>, ".", <symbol_ProductID>, " AS ", "[ProductID1]"
FROM: "[dbo].[Products]", " AS ", <symbol_Extent1>,
        "LEFT OUTER JOIN ""[dbo].[Categories]", " AS ", <symbol_Extent2>, " ON ", <symbol_Extent1>, ".", "[CategoryID]", " = ", <symbol_Extent2>, ".", "[CategoryID]",
        "INNER JOIN ",
        " (", SELECT:
           <symbol_Extent3>, ".", "[OrderID]", " AS ", <symbol_OrderID>, ",
              <symbol_Extent3>, ".", "[ProductID]", " AS ", <symbol_ProductID>, ...,
         <joinSymbol_Join2>, ".", <symbol_OrderID_2>, ", ",
           <joinSymbol_Join2>, ".", <symbol_CustomerID>, ....,
        <joinSymbol_Join2>, ".", <symbol_OrderID_3>,
<joinSymbol_Join2>, ".", <symbol_CustomsDescription>,
<joinSymbol_Join2>, ".", <symbol_ExciseTax>
FROM: "[dbo].[OrderDetails]", " AS ", <symbol_Extent3>,
"LEFT OUTER JOIN ",
" (", SELECT:
<symbol_Extent4>, ".", "[OrderID]", " AS ", <symbol_OrderID_2>,
<symbol_Extent4>, ".", "[CustomerID]", " AS ", <symbol_CustomerID>, ...
<symbol_Extent5>, ".", "[OrderID]", " AS ", <symbol_OrderID_3>,
<symbol_Extent5>, ".", "[CustomsDescription]", " AS ", <symbol_CustomsDescription>,
<symbol_Extent5>, ".", "[ExciseTax]", " AS ", <symbol_ExciseTax>
FROM: "[dbo].[Orders]", " AS ", <symbol_Extent4>,
"LEFT OUTER JOIN ", , "[dbo].[InternationalOrders]", " AS ", <symbol_Extent5>,
" ON ", <symbol_Extent4>, ".", "[OrderID]", " = ", , <symbol_Extent5>, ".", "[OrderID]"
" )", " AS ", <joinSymbol_Join2>, " ON ", , , <symbol_Extent3>, ".", "[OrderID]", " = ", , <joinSymbol_Join2>, ".", <symbol_OrderID_2>
" )", " AS ", <joinSymbol_Join3>, " ON ", , , <symbol_Extent1>, ".", "[ProductID]", " = ", , <joinSymbol_Join3>, ".", <symbol_ProductID>
```

### <a name="second-phase-of-sql-generation-generating-the-string-command"></a>Druhá fáze generování SQL: Generování řetězcového příkazu

Druhá fáze vytvoří pro symboly skutečný název a zaměřuje se pouze na symboly představující sloupce s názvem "ČísloObjednávky", jako v tomto případě je třeba vyřešit konflikt. Ty jsou zvýrazněné v SqlSelectStatement. Všimněte si, že přípony používané na obrázku jsou určeny pouze k zdůraznění, že se jedná o různé instance, nikoli nové názvy, protože v této fázi se jejich konečné názvy (případně jiné pojmenování původních názvů) ještě nepřiřadily.

První nalezený symbol, který je třeba přejmenovat, \<je symbol_OrderID >. Jeho nový název je přiřazen jako "OrderID1", 1 je označen jako poslední použitá přípona "KódObjednávky" a symbol je označen jako nepotřebuje se přejmenovat. V dalším kroku se najde první \<použití > symbol_OrderID_2. Je přejmenována na použití další dostupné přípony ("OrderID2") a znovu označena jako nepotřebná přejmenování, aby se při příštím použití nepřejmenovala. To se provádí i \<pro symbol_OrderID_3 >.

Na konci druhé fáze je vygenerován konečný příkaz SQL.

## <a name="see-also"></a>Viz také:

- [Generování SQL ve zprostředkovateli ukázek](sql-generation-in-the-sample-provider.md)
