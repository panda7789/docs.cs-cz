---
title: 'Návod: Generování SQL'
ms.date: 03/30/2017
ms.assetid: 16c38aaa-9927-4f3c-ab0f-81636cce57a3
ms.openlocfilehash: 5551eb4088e7529c61d5c517fed6877c23ae12f2
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2018
ms.locfileid: "43472069"
---
# <a name="walkthrough-sql-generation"></a>Návod: Generování SQL
Toto téma ukazuje, jak probíhá generování SQL [zprostředkovateli ukázek](https://go.microsoft.com/fwlink/?LinkId=180616). Následující dotaz Entity SQL používá model, který je součástí ukázkového zprostředkovatele:  
  
```  
SELECT  j1.ProductId, j1.ProductName, j1.CategoryName, j2.ShipCountry, j2.ProductId  
FROM (  SELECT P.ProductName, P.ProductId, P.Category.CategoryName  
        FROM NorthwindEntities.Products AS P) as j1  
INNER JOIN (SELECT OD.ProductId, OD.Order.ShipCountry as ShipCountry  
            FROM NorthwindEntities.OrderDetails AS OD) as j2  
            ON j1.ProductId == j2.ProductId   
```  
  
 Dotaz vytvoří následující výstup příkazu stromu, který je předán do zprostředkovatele:  
  
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
  
 Toto téma popisuje, jak převést tohoto stromu příkazů výstup do těchto příkazů SQL.  
  
```  
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
  
## <a name="first-phase-of-sql-generation-visiting-the-expression-tree"></a>První fázi generování SQL: na strom výrazu  
 Následující obrázek znázorňuje prázdný počáteční stav návštěvníka.  V tomto tématu jsou uvedeny pouze vlastnosti, které se týkají vysvětlení návod.  
  
 ![Diagram](../../../../../docs/framework/data/adonet/ef/media/430180f5-4fb9-4bc3-8589-d566512d9703.gif "430180f5-4fb9-4bc3-8589-d566512d9703")  
  
 Když je uživatel na uzel projektu, se nazývá VisitInputExpression přes vstup (Join4), která aktivuje návštěvu Join4 metodou VisitJoinExpression. Protože to je nejvyšší spojení, IsParentAJoin vrátí hodnotu false a nové SqlSelectStatement (SelectStatement0) se vytvoří a posunuto v zásobníku příkazu SELECT. Navíc nového oboru (scope0) je zadána v tabulce symbolů. Předtím, než je zobrazeny prvního vstupu (vlevo) spojení, 'true' je posunuto v zásobníku IsParentAJoin. Těsně před Join1, což je levým vstupem Join4, je navštívili, je stav návštěvníka jak je znázorněno na následujícím obrázku.  
  
 ![Diagram](../../../../../docs/framework/data/adonet/ef/media/406d4f5f-6166-44ea-8e74-c5001d5d5d79.gif "406d4f5f-6166-44ea-8e74-c5001d5d5d79")  
  
 Když navštíví spojení přes Join4 je vyvolána metoda, IsParentAJoin má hodnotu true, proto ji znovu použije aktuální příkaz select SelectStatement0. Nový obor je zadané (scope1). Před jeho levého podřízené Extent1, jiné true je vloženo do zásobníku IsParentAJoin.  
  
 Když je uživatel Extent1, protože IsParentAJoin vrací hodnotu true, vrátí SqlBuilder obsahující "[dbo]. [Products] ". Ovládací prvek vrátí metoda Join4 navštívit. Záznam je odebrán z IsParentAJoin a ProcessJoinInputResult je volána, která připojí výsledek hostujících Extent1 klauzule From SelectStatement0. Nový z symbol symbol_Extent1, pro vytvoření názvu Vstupní vazba "Extent1" přidány do FromExtents SelectStatement0 a také "Jak" a symbol_Extent1 jsou připojeny k klauzuli from. Nový záznam se přidá do AllExtentNames pro "Extent1" s hodnotou 0. Přidá nový záznam do aktuálního oboru v tabulce symbolů, které chcete přidružit k její symbol_Extent1 symbol "Extent1". Symbol_Extent1 je taky přidaný ke AllJoinExtents SqlSelectStatement.  
  
 Předtím, než je pravým vstupem modulu Join1 navštívili, "LEFT OUTER JOIN" je přidána do klauzule From SelectStatement0. Protože pravým vstupem je výraz kontroly, převede se true znovu IsParentAJoin zásobníku. Stav, který se před návštěvou pravým vstupem, jak je znázorněno na následujícím obrázku.  
  
 ![Diagram](../../../../../docs/framework/data/adonet/ef/media/ca62c31b-7ff6-4836-b209-e16166304fdc.gif "ca62c31b-7ff6-4836-b209-e16166304fdc")  
  
 Správný vstup se zpracovává stejně jako s levým vstupem. Stav po přečtení informací pravým vstupem je zobrazen na dalším obrázku.  
  
 ![Diagram](../../../../../docs/framework/data/adonet/ef/media/cd2afa99-7256-4c63-aaa9-c2d13f18a3d8.gif "cd2afa99-7256-4c63-aaa9-c2d13f18a3d8")  
  
 Další "false" je posunuto v zásobníku IsParentAJoin a podmínky spojení Var(Extent1). ID kategorie == Var(Extent2). ID kategorie se zpracovává. Var(Extenent1) je přeložen na < symbol_Extent1 > po pohled nahoru v tabulce symbolů. Protože instance je přeložit na jednoduché Symbol, jako výsledek zpracování Var(Extent1). ID kategorie, SqlBuilder s \<symbol1 >. " ID kategorie"je vrácena. Podobně se zpracovává druhé straně porovnání a výsledek hostujících podmínka spojení je připojena k SelectStatement1 a hodnota, kterou "false" je odebrán ze zásobníku IsParentAJoin klauzule FROM.  
  
 Díky tomu Join1 zcela byla zpracována a obor je odebrán z tabulky symbolů.  
  
 Ovládací prvek vrátí na zpracování Join4 nadřazené Join1. Protože podřízený znovu použít příkaz Select, Join1 rozsahy jsou nahrazeny jednoho symbol Join < joinSymbol_Join1 >. Také se přidá nový záznam do tabulky symbolů Join1 přidružit < joinSymbol_Join1 >.  
  
 Další uzel ke zpracování je Join3, druhý podřízený Join4. Je to správné podřízené, "false" se vloží do zásobníku IsParentAJoin. Stav návštěvníka v tomto okamžiku je znázorněno v následující obrázek.  
  
 ![Diagram](../../../../../docs/framework/data/adonet/ef/media/1ec61ed3-fcdd-4649-9089-24385be7e423.gif "1ec61ed3-fcdd-4649-9089-24385be7e423")  
  
 IsParentAJoin Join3, vrátí hodnotu false a je potřeba spustit nový SqlSelectStatement (SelectStatement1) a pak ji nasdílet do zásobníku. Zpracování pokračuje podle udělal s předchozím předchozí spojení, nový obor je vloženo do zásobníku a jsou zpracovány podřízené objekty. Levé podřízený člen je v rozsahu (Extent3) a správné podřízená položka spojení (Join2), takže bude také potřeba spustit nový SqlSelectStatement: SelectStatement2. Podřízené položky na Join2 rozsahy jsou také a souhrnně započítávají do SelectStatement2.  
  
 Stav vpravo návštěvníka po Join2 je zobrazeny, ale před jeho po zpracování (ProcessJoinInputResult) se provádí je zobrazen v na následujícím obrázku:  
  
 ![Diagram](../../../../../docs/framework/data/adonet/ef/media/7510346f-8b09-4c99-b411-40af239c3c4d.gif "7510346f-8b09-4c99-b411-40af239c3c4d")  
  
 Na předchozím obrázku se zobrazí SelectStatement2 zdarma s plovoucí desetinnou čárkou protože byl odebrán ze zásobníku, ale dosud příspěvek zpracování nadřazenou položkou. Je potřeba přidat do části od nadřazené položky, ale není úplným příkazem SQL bez klauzule SELECT. Ano v tomto okamžiku výchozích sloupců (všechny sloupce produkované jeho vstupů) jsou přidány do seznamu příkazu select metodou AddDefaultColumns. AddDefaultColumns Iteruje přes symboly v FromExtents a pro každý symbol přidá všechny sloupce v oboru. Pro jednoduché symbol dohlíží na typ symbolu, který pro načtení všech vlastností přidat. Naplní také AllColumnNames slovník s názvy sloupců. Dokončené SelectStatement2 se připojí k klauzule FROM SelectStatement1.  
  
 V dalším kroku se vytvoří nový symbol spojení k reprezentaci Join2, se označí jako vnořené spojení a přidán do AllJoinExtents SelectStatement1 a přidá do tabulky symbolů.  Nyní podmínka spojení Join3 Var(Extent3). OrderID = Var(Join2). Extent4.OrderID, je potřeba zpracovat. Zpracování na levé straně je podobný podmínka spojení Join1. Nicméně zpracování doprava a na straně "Var(Join2). Extent4.OrderID"se liší, protože spojení sloučení je povinný.  
  
 Následující obrázek ukazuje stav návštěvníka těsně před DbPropertyExpression "Var(Join2). Extent4.OrderID", jsou zpracovávána.  
  
 Vezměte v úvahu jak "Var(Join2). Je-li zobrazeny Extent4.OrderID". První, vlastnost instance "Var(Join2). Extent4 "je navštívili, což je jiný DbPropertyExpression a první návštěvy své instance"Var(Join2)". V oboru nejvyšší většina v tabulce symbolů "Join2" přeloží na < joinSymbol_join2 >. V metodě návštěvu pro DbPropertyExpression zpracování "Var(Join2). Extent4 "Všimněte si, že symbol spojení byla vrácena při návštěvě instance a sloučení.  
  
 Protože je vnořené spojení, jsme vyhledat vlastnost "Extent4" ve slovníku NameToExtent symbolu spojení, ho vyřešit < symbol_Extent4 > a vrátí nový SymbolPair (< joinSymbol_join2 >, < symbol_Extent4 >). Protože dvojice symbol je vrácen z zpracování instance "Var(Join2). Vyřešeno z ColumnPart tento symbol pár (< symbol_Extent4 >), který má seznam sloupců v rozsahu, který představuje Extent4.OrderID", je vlastnost"OrderID". Tedy "Var(Join2). Extent4.OrderID"je přeložen na {< joinSymbol_Join2 >". ", < symbol_OrderID >}.  
  
 Podmínka spojení Join4 podobně zpracování. Ovládací prvek vrátí VisitInputExpression metody, který zpracovává horní části většiny projektů. Prohlížení FromExtents vrácené SelectStatement0, vstup je identifikován jako spojení a odstraní původní mezí a nahradí je nový rozsah se právě symbol spojení. Tabulky symbolů je rovněž aktualizováno a další zpracování projekce součástí projektu. Řešení vlastností a sloučení rozsahy spojení je popsáno výše.  
  
 ![Diagram](../../../../../docs/framework/data/adonet/ef/media/9456d6a9-ea2e-40ae-accc-a10e18e28b81.gif "9456d6a9-ea2e-40ae-accc-a10e18e28b81")  
  
 Nakonec je vytvořen SqlSelectStatement následující:  
  
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
  
### <a name="second-phase-of-sql-generation-generating-the-string-command"></a>Druhá fáze generování SQL: generování příkaz String  
 Druhá fáze vytvoří skutečné názvy symbolů a zaměříme jenom na symboly představující sloupce s názvem "OrderID", stejně jako v tomto případě ke konfliktu se musí přeložit. Tyto jsou zvýrazněné SqlSelectStatement. Všimněte si, že přípony použita na obrázku jsou pouze pro zdůraznit, že jsou různé instance, není k reprezentaci žádné nové názvy v této fáze jejich poslední názvů (by mohly mít odlišné formuláře původní názvy) dosud nebyla přiřazena.  
  
 První symbol nalezen, které je nutné přejmenovat je < symbol_OrderID >. Jejím novým názvem je přiřazen jako "OrderID1", 1 je označen jako poslední použitá přípona pro "OrderID" a symbol je označen jako není nutnosti přejmenování. V dalším kroku první využití < symbol_OrderID_2 > nebyl nalezen. Je přejmenován na tuto příponu použít, další k dispozici ("OrderID2") a znovu se označilo jako vyžadující není přejmenování, tak, aby při příštím se používá ji není přejmenují. To se provádí příliš pro < symbol_OrderID_3 >.  
  
 Na konci druhé fáze je generována poslední příkaz jazyka SQL.  
  
## <a name="see-also"></a>Viz také  
 [Generování SQL ve zprostředkovateli ukázek](../../../../../docs/framework/data/adonet/ef/sql-generation-in-the-sample-provider.md)
