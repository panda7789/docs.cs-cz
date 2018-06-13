---
title: 'Návod: Generování SQL'
ms.date: 03/30/2017
ms.assetid: 16c38aaa-9927-4f3c-ab0f-81636cce57a3
ms.openlocfilehash: ab08b404dc60483a39e5c6ae56d82b63932c3f3e
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32766319"
---
# <a name="walkthrough-sql-generation"></a>Návod: Generování SQL
Toto téma ukazuje, jak SQL generace dojde v [ukázka zprostředkovatele](http://go.microsoft.com/fwlink/?LinkId=180616). Následující dotaz Entity SQL používá model, který je součástí ukázkového zprostředkovatele:  
  
```  
SELECT  j1.ProductId, j1.ProductName, j1.CategoryName, j2.ShipCountry, j2.ProductId  
FROM (  SELECT P.ProductName, P.ProductId, P.Category.CategoryName  
        FROM NorthwindEntities.Products AS P) as j1  
INNER JOIN (SELECT OD.ProductId, OD.Order.ShipCountry as ShipCountry  
            FROM NorthwindEntities.OrderDetails AS OD) as j2  
            ON j1.ProductId == j2.ProductId   
```  
  
 Následující stromové struktury výstup příkazu, která je předána zprostředkovateli výsledkem dotazu:  
  
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
  
 Toto téma popisuje způsob převodu tohoto stromu příkazů výstup do následující příkazy SQL.  
  
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
  
## <a name="first-phase-of-sql-generation-visiting-the-expression-tree"></a>První fáze generování SQL: návštěvou strom výrazu  
 Následující obrázek ukazuje počáteční prázdný stav návštěvníka.  V tomto tématu jsou uvedeny pouze vlastnosti, které se týkají vysvětlení návod.  
  
 ![Diagram](../../../../../docs/framework/data/adonet/ef/media/430180f5-4fb9-4bc3-8589-d566512d9703.gif "430180f5-4fb9-4bc3-8589-d566512d9703")  
  
 Při návštěvě uzel projektu, se nazývá VisitInputExpression přes vstupní (Join4), která aktivuje návštěvu Join4 metodou VisitJoinExpression. Protože je to nejhornější spojení, IsParentAJoin vrací hodnotu false a nové SqlSelectStatement (SelectStatement0) je vytvořen a nabídnutých v zásobníku příkazu SELECT. Navíc nového oboru (scope0) je zadána v tabulce symbolu. Předtím, než je první (levém) vstup připojení k navštívili, hodnotu true' je nabídnutých v zásobníku IsParentAJoin. Těsně před Join1, který je levém vstup Join4, je navštívili, stav návštěvníka je, jak ukazuje následující obrázek.  
  
 ![Diagram](../../../../../docs/framework/data/adonet/ef/media/406d4f5f-6166-44ea-8e74-c5001d5d5d79.gif "406d4f5f-6166-44ea-8e74-c5001d5d5d79")  
  
 Když navštíví spojení metoda je volána přes Join4, IsParentAJoin má hodnotu true, proto ji znovu použije aktuální příkaz select SelectStatement0. Nový obor je zadané (scope1). Před jeho levé podřízené Extent1, kteří navštěvují se v zásobníku IsParentAJoin posune jinou hodnotu true.  
  
 Při návštěvě Extent1, protože IsParentAJoin vrací hodnotu true, vrátí SqlBuilder, obsahující "[dbo]. [Produkty] ". Vrátí ovládací prvek metodu návštěvou Join4. Položka je odebrány z IsParentAJoin a ProcessJoinInputResult je volána, který připojí výsledek hostujících Extent1 klauzuli From SelectStatement0. Nový z symbol, symbol_Extent1, pro vytvoření názvu Vstupní vazba "Extent1" přidány do FromExtents SelectStatement0 a také "Jako" a symbol_Extent1 se připojí k klauzuli from. Nový záznam se přidá do AllExtentNames pro "Extent1" s hodnotou 0. Nový záznam se přidá do aktuálního oboru v tabulce symbol "Extent1" přidružit jeho symbol_Extent1 symbol. Symbol_Extent1 je taky přidaný ke AllJoinExtents SqlSelectStatement.  
  
 Předtím, než je správný vstup Join1 navštívili, "LEFT OUTER JOIN" se přidá do klauzuli From SelectStatement0. Protože správný vstup je výraz kontroly, true znovu vložena do zásobníku IsParentAJoin. Stav před návštěvou správný vstup, jak ukazuje následující obrázek.  
  
 ![Diagram](../../../../../docs/framework/data/adonet/ef/media/ca62c31b-7ff6-4836-b209-e16166304fdc.gif "ca62c31b-7ff6-4836-b209-e16166304fdc")  
  
 Správný vstup se zpracovává stejně jako levý vstupní. Stav po přečtení informací správný vstup je ukazuje následující obrázek.  
  
 ![Diagram](../../../../../docs/framework/data/adonet/ef/media/cd2afa99-7256-4c63-aaa9-c2d13f18a3d8.gif "cd2afa99-7256-4c63-aaa9-c2d13f18a3d8")  
  
 V zásobníku IsParentAJoin a podmínku připojení Var(Extent1) se posune další "false". CategoryID == Var(Extent2). CategoryID, jsou zpracovávány. Var(Extenent1) je převést < symbol_Extent1 > po podívejte se nahoru v tabulky symbolů. Protože je přeložit na Symbol jednoduché jako výsledek zpracování Var(Extent1) instance. CategoryID, SqlBuilder s \<symbol1 >. " Vrátí se CategoryID". Podobně jako druhá strana porovnání zpracování a výsledek hostujících podmínku připojení je připojeno k SelectStatement1 a hodnota, kterou "false" odebrány ze zásobníku IsParentAJoin klauzule FROM.  
  
 S tím Join1 úplně byly zpracovány, a obor je odebrány z tabulky symbolů.  
  
 Vrátí ovládací prvek zpracování Join4 nadřazeného Join1. Vzhledem k tomu, že podřízená opakovaně příkaz Select, Join1 rozsahy jsou nahrazeny jeden symbol spojení < joinSymbol_Join1 >. Také je přidat novou položku do tabulky symbolů pro přidružení Join1 < joinSymbol_Join1 >.  
  
 Další uzel mají být zpracovány je Join3, druhý podřízeným Join4. Protože je správné podřízené, "Nepravda" vložena do zásobníku IsParentAJoin. Stav návštěvníka v tomto okamžiku je znázorněno v následující obrázek.  
  
 ![Diagram](../../../../../docs/framework/data/adonet/ef/media/1ec61ed3-fcdd-4649-9089-24385be7e423.gif "1ec61ed3-fcdd-4649-9089-24385be7e423")  
  
 Pro Join3 IsParentAJoin vrací hodnotu false a je potřeba spustit novou SqlSelectStatement (SelectStatement1) a poslat ho v zásobníku. Zpracování pokračuje podle nebyla s předchozí předchozí spojení, nový obor se posune do zásobníku a podřízené objekty jsou zpracovávány. Levé podřízená položka rozsah (Extent3) a správné podřízená položka spojení (Join2), který se taky musí spustit novou SqlSelectStatement: SelectStatement2. Podřízené objekty na Join2 rozsahy jsou také a jsou agregováni do SelectStatement2.  
  
 Stav právo návštěvníka po Join2 je navštívili, ale předtím, než se provádí jeho po zpracování (ProcessJoinInputResult) se zobrazí v následující obrázek:  
  
 ![Diagram](../../../../../docs/framework/data/adonet/ef/media/7510346f-8b09-4c99-b411-40af239c3c4d.gif "7510346f-8b09-4c99-b411-40af239c3c4d")  
  
 Na předchozím obrázku je zobrazena SelectStatement2 jako volné plovoucí protože byla mimo zásobníku odebrány, ale ještě nebyla post zpracovává nadřazený. Musí být přidán do části od nadřazeného objektu, ale není dokončení příkazu jazyka SQL bez klauzuli SELECT. Ano v tomto okamžiku výchozí sloupce (všechny sloupce vyprodukované vstupy) se přidají do seznamu příkazu select metodou AddDefaultColumns. AddDefaultColumns iteruje nad symboly v FromExtents a pro každý symbol přidá všechny sloupce v oboru. Pro jednoduché symbol vypadá na typ symbolu načíst všechny jeho vlastnosti, který se má přidat. Naplní také slovníku AllColumnNames s názvy sloupců. Dokončené SelectStatement2 se připojuje k klauzuli FROM SelectStatement1.  
  
 Další který představuje Join2 je vytvořen nový symbol spojení, je označena jako vnořené připojení a přidat do AllJoinExtents SelectStatement1 a přidat do tabulky symbolů.  Nyní podmínku spojení Join3, Var(Extent3). OrderID = Var(Join2). Extent4.OrderID, je potřeba zpracovat. Zpracování na levé straně je podobná podmínku spojení Join1. Ale zpracování práva a straně "Var(Join2). Extent4.OrderID"se liší, protože připojení k vyrovnání je vyžadován.  
  
 Následující obrázek ukazuje stav návštěvníka těsně před DbPropertyExpression "Var(Join2). Extent4.OrderID", jsou zpracovávány.  
  
 Vezměte v úvahu jak "Var(Join2). Je navštívené Extent4.OrderID". První, vlastnost instance "Var(Join2). Extent4 "je navštívili, který je jiný DbPropertyExpression a nejprve navštíví jeho instance"Var(Join2)". V horní většina oboru v tabulce symbol "Join2" přeloží na < joinSymbol_join2 >. V metodě návštěvu pro DbPropertyExpression zpracování "Var(Join2). Extent4 "Všimněte si, že při vyžádáním návštěvou instance a vyrovnání byla vrácena symbol spojení.  
  
 Vzhledem k tomu, že je vnořené spojení, jsme vyhledat vlastnost "Extent4" ve slovníku NameToExtent symbolu spojení, odkazující na < symbol_Extent4 > a vrátí nové SymbolPair (< joinSymbol_join2 >, < symbol_Extent4 >). Vzhledem k tomu pár symbol vrácená zpracování instance "Var(Join2). Extent4.OrderID","OrderID"vlastnost vyřešen z ColumnPart dvojic tento symbol (< symbol_Extent4 >), který má seznam sloupců v rozsahu, který představuje. Tedy "Var(Join2). Extent4.OrderID"je přeložen na {< joinSymbol_Join2 >". ", < symbol_OrderID >}.  
  
 Připojení k podmínku Join4 podobně zpracovává. Ovládací prvek vrátí metodu VisitInputExpression, který zpracovává horní většina projekt. Prohlížení FromExtents z vráceného SelectStatement0, vstup je označený jako spojení a původní rozsahy odebere a nahradí je nový rozsah symbolem právě spojení. Tabulky symbolů je rovněž aktualizováno a znovu zpracována projekce součástí projektu. Řešení vlastnosti a vyrovnání rozsahy spojení je, jak je popsáno výše.  
  
 ![Diagram](../../../../../docs/framework/data/adonet/ef/media/9456d6a9-ea2e-40ae-accc-a10e18e28b81.gif "9456d6a9-ea2e-40ae-accc-a10e18e28b81")  
  
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
  
### <a name="second-phase-of-sql-generation-generating-the-string-command"></a>Druhé fáze generování SQL: generování příkaz String  
 Druhé fáze vytváří skutečné názvy symbolů a pouze zaměříme na symboly představující sloupců jako v tomto případě musí být vyřešen konflikt s názvem "OrderID". Tyto jsou vyznačené na SqlSelectStatement. Všimněte si, že přípony použít na obrázku jsou jenom pro zdůraznit, že jsou různé instance nechcete v této představují nové názvy, Příprava jejich poslední názvy (by mohl mít jiný formuláři původní názvy) ještě nebyla přiřazena.  
  
 První symbol nalezen, který vyžaduje k přejmenování je < symbol_OrderID >. Jejím novým názvem je přiřazen jako "OrderID1", 1 je označena jako poslední používat příponu pro "OrderID" a symbol je označena jako není nutnosti přejmenování. V dalším kroku první použití < symbol_OrderID_2 > nachází. Je přejmenován na používají další dostupné příponu ("OrderID2") a znovu označena není potřebují přejmenování, tak, aby při příštím se používá ji není získat přejmenovat. To se provádí příliš pro < symbol_OrderID_3 >.  
  
 Na konci druhé fáze generuje se poslední příkaz jazyka SQL.  
  
## <a name="see-also"></a>Viz také  
 [Generování SQL ve zprostředkovateli ukázek](../../../../../docs/framework/data/adonet/ef/sql-generation-in-the-sample-provider.md)
