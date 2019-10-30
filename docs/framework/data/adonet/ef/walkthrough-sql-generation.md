---
title: 'Návod: generování SQL'
ms.date: 03/30/2017
ms.assetid: 16c38aaa-9927-4f3c-ab0f-81636cce57a3
ms.openlocfilehash: 2684acd39ae9651407023e8b5c73f02eadb97547
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040502"
---
# <a name="walkthrough-sql-generation"></a><span data-ttu-id="2e2cd-102">Návod: generování SQL</span><span class="sxs-lookup"><span data-stu-id="2e2cd-102">Walkthrough: SQL Generation</span></span>

<span data-ttu-id="2e2cd-103">Toto téma ukazuje, jak se ve [zprostředkovateli ukázky](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0)vyskytují generování SQL.</span><span class="sxs-lookup"><span data-stu-id="2e2cd-103">This topic illustrates how SQL generation occurs in the [Sample Provider](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0).</span></span> <span data-ttu-id="2e2cd-104">Následující Entity SQL dotaz používá model, který je součástí poskytovatele ukázkových:</span><span class="sxs-lookup"><span data-stu-id="2e2cd-104">The following Entity SQL query uses the model that is included with the sample provider:</span></span>

```sql
SELECT  j1.ProductId, j1.ProductName, j1.CategoryName, j2.ShipCountry, j2.ProductId
FROM (  SELECT P.ProductName, P.ProductId, P.Category.CategoryName
        FROM NorthwindEntities.Products AS P) as j1
INNER JOIN (SELECT OD.ProductId, OD.Order.ShipCountry as ShipCountry
            FROM NorthwindEntities.OrderDetails AS OD) as j2
            ON j1.ProductId == j2.ProductId
```

<span data-ttu-id="2e2cd-105">Dotaz vytvoří následující výstupní strom příkazů, který se předává poskytovateli:</span><span class="sxs-lookup"><span data-stu-id="2e2cd-105">The query produces the following output command tree that is passed to the provider:</span></span>

```output
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

 <span data-ttu-id="2e2cd-106">Toto téma popisuje, jak přeložit tento výstupní strom příkazů do následujících příkazů SQL.</span><span class="sxs-lookup"><span data-stu-id="2e2cd-106">This topic describes how to translate this output command tree into the following SQL statements.</span></span>

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

## <a name="first-phase-of-sql-generation-visiting-the-expression-tree"></a><span data-ttu-id="2e2cd-107">První fáze generování SQL: návštěvy stromu výrazů</span><span class="sxs-lookup"><span data-stu-id="2e2cd-107">First Phase of SQL Generation: Visiting the Expression Tree</span></span>

<span data-ttu-id="2e2cd-108">Následující obrázek znázorňuje počáteční prázdný stav návštěvníka.</span><span class="sxs-lookup"><span data-stu-id="2e2cd-108">The following figure illustrates the initial empty state of the visitor.</span></span>  <span data-ttu-id="2e2cd-109">V tomto tématu jsou zobrazeny pouze vlastnosti, které jsou relevantní pro vysvětlení návodu.</span><span class="sxs-lookup"><span data-stu-id="2e2cd-109">Throughout this topic, only the properties relevant to the walkthrough explanation are shown.</span></span>

<span data-ttu-id="2e2cd-110">![Znázorňuje](./media/430180f5-4fb9-4bc3-8589-d566512d9703.gif "430180f5-4fb9-4bc3-8589-d566512d9703")</span><span class="sxs-lookup"><span data-stu-id="2e2cd-110">![Diagram](./media/430180f5-4fb9-4bc3-8589-d566512d9703.gif "430180f5-4fb9-4bc3-8589-d566512d9703")</span></span>

<span data-ttu-id="2e2cd-111">Když je uzel projektu navštíven, VisitInputExpression se volá za jeho vstup (Join4), který spouští návštěvu Join4 metodou VisitJoinExpression.</span><span class="sxs-lookup"><span data-stu-id="2e2cd-111">When the Project  node is visited, VisitInputExpression is called over its input (Join4), which triggers the visit of Join4 by the method VisitJoinExpression.</span></span> <span data-ttu-id="2e2cd-112">Vzhledem k tomu, že se jedná o spojení na nejvyšší úrovni, IsParentAJoin vrátí hodnotu false a vytvoří se nový SqlSelectStatement (SelectStatement0) a vloží se do zásobníku příkazů SELECT.</span><span class="sxs-lookup"><span data-stu-id="2e2cd-112">Because this is a topmost join, IsParentAJoin returns false and a new SqlSelectStatement (SelectStatement0) is created and pushed on the SELECT statement stack.</span></span> <span data-ttu-id="2e2cd-113">V tabulce symbolů je také zadán nový obor (scope0).</span><span class="sxs-lookup"><span data-stu-id="2e2cd-113">Also, a new scope (scope0) is entered in the symbol table.</span></span> <span data-ttu-id="2e2cd-114">Po navštívení prvního (levého) vstupu spojení se v zásobníku IsParentAJoin vloží hodnota true.</span><span class="sxs-lookup"><span data-stu-id="2e2cd-114">Before the first (left) input of the join is visited, 'true' is pushed on the IsParentAJoin stack.</span></span> <span data-ttu-id="2e2cd-115">Stav návštěvníka, jak je znázorněno na následujícím obrázku, je uveden přímo před Join1, což je levý vstup Join4.</span><span class="sxs-lookup"><span data-stu-id="2e2cd-115">Right before Join1, which is the left input of Join4, is visited, the state of the visitor is as shown in the next figure.</span></span>

<span data-ttu-id="2e2cd-116">![Znázorňuje](./media/406d4f5f-6166-44ea-8e74-c5001d5d5d79.gif "406d4f5f-6166-44ea-8e74-c5001d5d5d79")</span><span class="sxs-lookup"><span data-stu-id="2e2cd-116">![Diagram](./media/406d4f5f-6166-44ea-8e74-c5001d5d5d79.gif "406d4f5f-6166-44ea-8e74-c5001d5d5d79")</span></span>

<span data-ttu-id="2e2cd-117">Když se metoda JOIN navštíví přes Join4, IsParentAJoin je true, takže znovu použije aktuální příkaz SELECT SelectStatement0.</span><span class="sxs-lookup"><span data-stu-id="2e2cd-117">When the join visit method is invoked over Join4, IsParentAJoin is true, thus it reuses the current select statement SelectStatement0.</span></span> <span data-ttu-id="2e2cd-118">Je zadán nový obor (OborContoso1).</span><span class="sxs-lookup"><span data-stu-id="2e2cd-118">A new scope is entered (scope1).</span></span> <span data-ttu-id="2e2cd-119">Než navštívíte jeho levou podřízenou položku, Extent1, bude do zásobníku IsParentAJoin vložena jiná hodnota true.</span><span class="sxs-lookup"><span data-stu-id="2e2cd-119">Before visiting its left child, Extent1, another true is pushed on the IsParentAJoin stack.</span></span>

<span data-ttu-id="2e2cd-120">Při navštívení Extent1, protože IsParentAJoin vrátí hodnotu true, vrátí SqlBuilder obsahující "[dbo]. [Products] ".</span><span class="sxs-lookup"><span data-stu-id="2e2cd-120">When Extent1 is visited, because IsParentAJoin returns true, it returns a SqlBuilder containing "[dbo].[Products]".</span></span> <span data-ttu-id="2e2cd-121">Ovládací prvek se vrátí do metody, která Join4 navštíví.</span><span class="sxs-lookup"><span data-stu-id="2e2cd-121">The control returns to the method visiting Join4.</span></span> <span data-ttu-id="2e2cd-122">Položka je vyjmuta z IsParentAJoin a je volána ProcessJoinInputResult, která připojuje výsledek návštěvy Extent1 do klauzule FROM v SelectStatement0.</span><span class="sxs-lookup"><span data-stu-id="2e2cd-122">An entry is popped from IsParentAJoin, and ProcessJoinInputResult is called, which appends the result of visiting Extent1 to the From clause of SelectStatement0.</span></span> <span data-ttu-id="2e2cd-123">Vytvoří se nový symbol z symbol_Extent1 pro název vstupní vazby "Extent1", přidá se do FromExtents SelectStatement0 a také "as" a symbol_Extent1 jsou připojeny k klauzuli FROM.</span><span class="sxs-lookup"><span data-stu-id="2e2cd-123">A new from symbol, symbol_Extent1, for the input binding name "Extent1" is created, added to the FromExtents of SelectStatement0, and also "As" and  symbol_Extent1 are appended to the from clause.</span></span> <span data-ttu-id="2e2cd-124">Do AllExtentNames pro "Extent1" se přidá nová položka s hodnotou 0.</span><span class="sxs-lookup"><span data-stu-id="2e2cd-124">A new entry is added to AllExtentNames for "Extent1" with the value of 0.</span></span> <span data-ttu-id="2e2cd-125">Do aktuálního oboru v tabulce symbolů se přidá nová položka, která přiřadí "Extent1" k jeho symbolu symbol_Extent1.</span><span class="sxs-lookup"><span data-stu-id="2e2cd-125">A new entry is added to the current scope in the symbol table to associate "Extent1" with its symbol symbol_Extent1.</span></span> <span data-ttu-id="2e2cd-126">Symbol_Extent1 je také přidáno do AllJoinExtentsu SqlSelectStatement.</span><span class="sxs-lookup"><span data-stu-id="2e2cd-126">Symbol_Extent1 is also added to the AllJoinExtents of the SqlSelectStatement.</span></span>

<span data-ttu-id="2e2cd-127">Před otevřením správného vstupu Join1 je do klauzule FROM v SelectStatement0 přidána levá vnější spojení.</span><span class="sxs-lookup"><span data-stu-id="2e2cd-127">Before the right input of Join1 is visited, "LEFT OUTER JOIN" is added to the From clause of SelectStatement0.</span></span> <span data-ttu-id="2e2cd-128">Vzhledem k tomu, že správný vstup je výraz skenování, je hodnota true znovu vložena do zásobníku IsParentAJoin.</span><span class="sxs-lookup"><span data-stu-id="2e2cd-128">Because the right input is a Scan expression, true is again pushed to the IsParentAJoin stack.</span></span> <span data-ttu-id="2e2cd-129">Stav před návštěvou správného vstupu, jak je znázorněno na následujícím obrázku.</span><span class="sxs-lookup"><span data-stu-id="2e2cd-129">The state before visiting the right input as shown in the next figure.</span></span>

<span data-ttu-id="2e2cd-130">![Znázorňuje](./media/ca62c31b-7ff6-4836-b209-e16166304fdc.gif "ca62c31b-7ff6-4836-b209-e16166304fdc")</span><span class="sxs-lookup"><span data-stu-id="2e2cd-130">![Diagram](./media/ca62c31b-7ff6-4836-b209-e16166304fdc.gif "ca62c31b-7ff6-4836-b209-e16166304fdc")</span></span>

<span data-ttu-id="2e2cd-131">Správný vstup je zpracován stejným způsobem jako levý vstup.</span><span class="sxs-lookup"><span data-stu-id="2e2cd-131">The right input is processed in the same way as the left input.</span></span> <span data-ttu-id="2e2cd-132">Stav po navštívení správného vstupu je zobrazen na následujícím obrázku.</span><span class="sxs-lookup"><span data-stu-id="2e2cd-132">The state after visiting the right input is shown in the next figure.</span></span>

<span data-ttu-id="2e2cd-133">![Znázorňuje](./media/cd2afa99-7256-4c63-aaa9-c2d13f18a3d8.gif "cd2afa99-7256-4c63-aaa9-c2d13f18a3d8")</span><span class="sxs-lookup"><span data-stu-id="2e2cd-133">![Diagram](./media/cd2afa99-7256-4c63-aaa9-c2d13f18a3d8.gif "cd2afa99-7256-4c63-aaa9-c2d13f18a3d8")</span></span>

<span data-ttu-id="2e2cd-134">Následující hodnota false se vloží do zásobníku IsParentAJoin a var podmínka Join (Extent1). KódKategorie = = var (Extent2). CategoryID je zpracována.</span><span class="sxs-lookup"><span data-stu-id="2e2cd-134">Next "false" is pushed on the IsParentAJoin stack and the join condition Var(Extent1).CategoryID == Var(Extent2).CategoryID is processed.</span></span> <span data-ttu-id="2e2cd-135">Var (Extent1) se přeloží na \<symbol_Extent1 > po hledání v tabulce symbolů.</span><span class="sxs-lookup"><span data-stu-id="2e2cd-135">Var(Extent1) is resolved to \<symbol_Extent1> after a look up in the symbol table.</span></span> <span data-ttu-id="2e2cd-136">Vzhledem k tomu, že instance je přeložena na jednoduchý symbol, jako výsledek zpracování var (Extent1). KódKategorie, SqlBuilder s \<symbol1 >. " KódKategorie – je vráceno.</span><span class="sxs-lookup"><span data-stu-id="2e2cd-136">Because the instance is resolved to a simple Symbol, as a result of processing Var(Extent1).CategoryID, a SqlBuilder with \<symbol1>."CategoryID" is returned.</span></span> <span data-ttu-id="2e2cd-137">Podobně je zpracována druhá strana porovnání a výsledek návštěvy podmínky spojení je připojen k klauzuli FROM SelectStatement1 a hodnota false je z zásobníku IsParentAJoin vyjmuta.</span><span class="sxs-lookup"><span data-stu-id="2e2cd-137">Similarly the other side of the comparison is processed, and the result of visiting the join condition is appended to the FROM clause of SelectStatement1 and the value "false" is popped from the IsParentAJoin stack.</span></span>

<span data-ttu-id="2e2cd-138">V důsledku toho bylo Join1 kompletně zpracováno a rozsah je odebrán z tabulky symbolů.</span><span class="sxs-lookup"><span data-stu-id="2e2cd-138">With this, Join1 has completely been processed, and a scope is popped from the symbol table.</span></span>

<span data-ttu-id="2e2cd-139">Řízení se vrátí ke zpracování Join4, nadřazenému objektu Join1.</span><span class="sxs-lookup"><span data-stu-id="2e2cd-139">Control returns to processing Join4, the parent of Join1.</span></span> <span data-ttu-id="2e2cd-140">Vzhledem k tomu, že podřízený znovu použil příkaz SELECT, jsou Join1 rozsahy nahrazeny jediným symbolem spojení \<joinSymbol_Join1 >.</span><span class="sxs-lookup"><span data-stu-id="2e2cd-140">Because the child reused the Select statement, the Join1 extents are replaced with a single Join symbol \<joinSymbol_Join1>.</span></span> <span data-ttu-id="2e2cd-141">Do tabulky symbolů je také přidána nová položka, která přidruží Join1 k > \<joinSymbol_Join1.</span><span class="sxs-lookup"><span data-stu-id="2e2cd-141">Also a new entry is added to the symbol table to associate Join1 with \<joinSymbol_Join1>.</span></span>

<span data-ttu-id="2e2cd-142">Další uzel, který se má zpracovat, je Join3, druhý podřízený člen Join4.</span><span class="sxs-lookup"><span data-stu-id="2e2cd-142">The next node to be processed is Join3, the second child of Join4.</span></span> <span data-ttu-id="2e2cd-143">V případě, že se jedná o pravou podřízenou položku, je do zásobníku IsParentAJoin vložena hodnota false.</span><span class="sxs-lookup"><span data-stu-id="2e2cd-143">As it is a right child, "false" is pushed to the IsParentAJoin stack.</span></span> <span data-ttu-id="2e2cd-144">Stav návštěvníka v tomto okamžiku je znázorněn na následujícím obrázku.</span><span class="sxs-lookup"><span data-stu-id="2e2cd-144">The state of the visitor at this point is illustrated in the next figure.</span></span>

<span data-ttu-id="2e2cd-145">![Znázorňuje](./media/1ec61ed3-fcdd-4649-9089-24385be7e423.gif "1ec61ed3-fcdd-4649-9089-24385be7e423")</span><span class="sxs-lookup"><span data-stu-id="2e2cd-145">![Diagram](./media/1ec61ed3-fcdd-4649-9089-24385be7e423.gif "1ec61ed3-fcdd-4649-9089-24385be7e423")</span></span>

<span data-ttu-id="2e2cd-146">Pro Join3 vrátí IsParentAJoin hodnotu false a musí spustit nový SqlSelectStatement (SelectStatement1) a vložit ho do zásobníku.</span><span class="sxs-lookup"><span data-stu-id="2e2cd-146">For Join3, IsParentAJoin returns false and needs to start a new SqlSelectStatement (SelectStatement1) and push it on the stack.</span></span> <span data-ttu-id="2e2cd-147">Zpracování pokračuje stejně jako v předchozích předchozích spojeních, nový obor je vložen do zásobníku a jsou zpracovány podřízené objekty.</span><span class="sxs-lookup"><span data-stu-id="2e2cd-147">Processing continues as it did with the previous the previous joins, a new scope is pushed on the stack and the children are processed.</span></span> <span data-ttu-id="2e2cd-148">Levý podřízený objekt je rozsah (Extent3) a pravá podřízená položka je Join (Join2), která také musí začít nový SqlSelectStatement: SelectStatement2.</span><span class="sxs-lookup"><span data-stu-id="2e2cd-148">The left child is an Extent (Extent3) and the right child is a join (Join2) which also needs to start a new SqlSelectStatement: SelectStatement2.</span></span> <span data-ttu-id="2e2cd-149">Podřízené položky v Join2 jsou také rozsahy a jsou shrnuty do SelectStatement2.</span><span class="sxs-lookup"><span data-stu-id="2e2cd-149">The children on Join2 are Extents as well and are aggregated into SelectStatement2.</span></span>

<span data-ttu-id="2e2cd-150">Stav návštěvníka hned po navštívení Join2, ale před jeho následným zpracováním (ProcessJoinInputResult) se zobrazí na následujícím obrázku:</span><span class="sxs-lookup"><span data-stu-id="2e2cd-150">The state of the visitor right after Join2 is visited, but before its post-processing (ProcessJoinInputResult) is done is shown in the next figure:</span></span>

<span data-ttu-id="2e2cd-151">![Znázorňuje](./media/7510346f-8b09-4c99-b411-40af239c3c4d.gif "7510346f-8b09-4c99-b411-40af239c3c4d")</span><span class="sxs-lookup"><span data-stu-id="2e2cd-151">![Diagram](./media/7510346f-8b09-4c99-b411-40af239c3c4d.gif "7510346f-8b09-4c99-b411-40af239c3c4d")</span></span>

<span data-ttu-id="2e2cd-152">Na předchozím obrázku je SelectStatement2 zobrazen jako volné plovoucí, protože byl odebrán ze zásobníku, ale nebyl dosud zpracován nadřazeným objektem.</span><span class="sxs-lookup"><span data-stu-id="2e2cd-152">In the previous figure, SelectStatement2 is shown as free floating because it was popped out of the stack, but not yet post processed by the parent.</span></span> <span data-ttu-id="2e2cd-153">Je nutné jej přidat do části z nadřazené položky, ale není to úplný příkaz SQL bez klauzule SELECT.</span><span class="sxs-lookup"><span data-stu-id="2e2cd-153">It needs to be added to the FROM part of the parent, but it is not a complete SQL statement without a SELECT clause.</span></span> <span data-ttu-id="2e2cd-154">Takže v tomto okamžiku jsou výchozí sloupce (všechny sloupce vytvářené jeho vstupy) přidány do seznamu Select metodou AddDefaultColumns.</span><span class="sxs-lookup"><span data-stu-id="2e2cd-154">So, at this point, the default columns (all the columns produced by its inputs) are added to the select list by the method AddDefaultColumns.</span></span> <span data-ttu-id="2e2cd-155">AddDefaultColumns iterovat symboly v FromExtents a pro každý symbol přidá všechny sloupce v rozsahu.</span><span class="sxs-lookup"><span data-stu-id="2e2cd-155">AddDefaultColumns iterates over the symbols in FromExtents and for each symbol adds all the columns brought in scope.</span></span> <span data-ttu-id="2e2cd-156">Pro jednoduchý symbol se vyhledá typ symbolu, který načte všechny jeho vlastnosti, které se mají přidat.</span><span class="sxs-lookup"><span data-stu-id="2e2cd-156">For a simple symbol, it looks at the symbol type to retrieve all its properties to be added.</span></span> <span data-ttu-id="2e2cd-157">Také naplní slovník AllColumnNames názvy sloupců.</span><span class="sxs-lookup"><span data-stu-id="2e2cd-157">It also populates the AllColumnNames dictionary with the column names.</span></span> <span data-ttu-id="2e2cd-158">Dokončený SelectStatement2 je připojen k klauzuli FROM SelectStatement1.</span><span class="sxs-lookup"><span data-stu-id="2e2cd-158">The completed SelectStatement2 is appended to the FROM clause of SelectStatement1.</span></span>

<span data-ttu-id="2e2cd-159">V dalším kroku je vytvořen nový symbol spojení, který představuje Join2, je označený jako vnořené spojení a přidáno do AllJoinExtentsu SelectStatement1 a přidal se do tabulky symbolů.</span><span class="sxs-lookup"><span data-stu-id="2e2cd-159">Next, a new join symbol is created to represent Join2, it is marked as a nested join and added to the AllJoinExtents of SelectStatement1 and added to the symbol table.</span></span>  <span data-ttu-id="2e2cd-160">Nyní je podmínka spojení Join3, var (Extent3). ČísloObjednávky = var (Join2). Extent4. ČísloObjednávky se musí zpracovat.</span><span class="sxs-lookup"><span data-stu-id="2e2cd-160">Now the join condition of Join3, Var(Extent3).OrderID =  Var(Join2).Extent4.OrderID, needs to be processed.</span></span> <span data-ttu-id="2e2cd-161">Zpracování levé strany je podobné podmínce spojení Join1.</span><span class="sxs-lookup"><span data-stu-id="2e2cd-161">Processing of the left hand side is similar to the join condition of Join1.</span></span> <span data-ttu-id="2e2cd-162">Nicméně zpracování pravého a vedlejšího "var (Join2). Extent4. ČísloObjednávky se liší, protože je vyžadováno sloučení spojení.</span><span class="sxs-lookup"><span data-stu-id="2e2cd-162">However, the processing of the right and side "Var(Join2).Extent4.OrderID" is different because join flattening is required.</span></span>

<span data-ttu-id="2e2cd-163">Následující obrázek ukazuje stav návštěvníka přímo před DbPropertyExpression "var (Join2). Extent4. ČísloObjednávky se zpracovává.</span><span class="sxs-lookup"><span data-stu-id="2e2cd-163">The next figure shows the state of the visitor right before the DbPropertyExpression "Var(Join2).Extent4.OrderID" is processed.</span></span>

<span data-ttu-id="2e2cd-164">Zvažte, jak "var (Join2). Extent4. ČísloObjednávky "se navštíví.</span><span class="sxs-lookup"><span data-stu-id="2e2cd-164">Consider how "Var(Join2).Extent4.OrderID" is visited.</span></span> <span data-ttu-id="2e2cd-165">Nejprve vlastnost instance "var (Join2). Extent4 "" se navštíví, což je další DbPropertyExpression, a první navštíví svou instanci "var (Join2)".</span><span class="sxs-lookup"><span data-stu-id="2e2cd-165">First, the instance property "Var(Join2).Extent4" is visited, which is another DbPropertyExpression and first visits its instance "Var(Join2)".</span></span> <span data-ttu-id="2e2cd-166">V nejvyšším oboru v tabulce symbolů "Join2" překládá na \<joinSymbol_join2 >.</span><span class="sxs-lookup"><span data-stu-id="2e2cd-166">In the top most scope in the symbol table, "Join2" resolves to \<joinSymbol_join2>.</span></span> <span data-ttu-id="2e2cd-167">V metodě návštěvy pro zpracování DbPropertyExpression "var (Join2). Extent4 "Všimněte si, že při návštěvě instance se vrátil symbol spojení, který je potřeba pro sloučení.</span><span class="sxs-lookup"><span data-stu-id="2e2cd-167">In the visit method for DbPropertyExpression processing "Var(Join2).Extent4" notice that a join symbol was returned when visiting the instance and flattening is required.</span></span>

<span data-ttu-id="2e2cd-168">Vzhledem k tomu, že se jedná o vnořené spojení, vyhledáme vlastnost "Extent4" ve slovníku NameToExtent symbolu JOIN, vyřešte ji \<symbol_Extent4 > a vrátíte novou SymbolPair (\<joinSymbol_join2 > \<symbol_Extent4 >).</span><span class="sxs-lookup"><span data-stu-id="2e2cd-168">Since it is a nested join, we look up the property "Extent4" in the NameToExtent dictionary of the join symbol, resolve it to \<symbol_Extent4> and return a new SymbolPair(\<joinSymbol_join2>, \<symbol_Extent4>).</span></span> <span data-ttu-id="2e2cd-169">Vzhledem k tomu, že dvojici symbolů je vráceno ze zpracování instance "var (Join2). Extent4. ČísloObjednávky ", vlastnost" ČísloObjednávky "je přeložena z ColumnPart páru symbolů (\<symbol_Extent4 >), který obsahuje seznam sloupců rozsahu, který představuje.</span><span class="sxs-lookup"><span data-stu-id="2e2cd-169">Since a symbol pair is returned from the processing of the instance of "Var(Join2).Extent4.OrderID",  the property "OrderID" is resolved from the ColumnPart of that symbol pair (\<symbol_Extent4>), which has a list of the columns of the extent it represents.</span></span> <span data-ttu-id="2e2cd-170">Tedy "var (Join2). Extent4. ČísloObjednávky se přeloží na {\<joinSymbol_Join2 >, ".", \<symbol_OrderID >}.</span><span class="sxs-lookup"><span data-stu-id="2e2cd-170">So, "Var(Join2).Extent4.OrderID" is resolved to { \<joinSymbol_Join2>, ".", \<symbol_OrderID>}.</span></span>

<span data-ttu-id="2e2cd-171">Podobně se zpracovává podmínka spojení Join4.</span><span class="sxs-lookup"><span data-stu-id="2e2cd-171">The join condition of Join4 is similarly processed.</span></span> <span data-ttu-id="2e2cd-172">Ovládací prvek se vrátí metodě VisitInputExpression, která zpracovala nejvyšší nejvíc projektu.</span><span class="sxs-lookup"><span data-stu-id="2e2cd-172">The control returns to the VisitInputExpression method that processed the top most project.</span></span> <span data-ttu-id="2e2cd-173">V FromExtentsi vráceného SelectStatement0 se vstup identifikuje jako Join a odstraní původní rozsahy a nahradí je novým rozsahem, a to pouze pomocí spojovacího symbolu.</span><span class="sxs-lookup"><span data-stu-id="2e2cd-173">Looking at the FromExtents of the returned SelectStatement0, the input is identified as a join, and removes the original extents and replaces them with a new extent with just the Join symbol.</span></span> <span data-ttu-id="2e2cd-174">Tabulka symbolů je také aktualizována a příště je zpracována část projekce projektu.</span><span class="sxs-lookup"><span data-stu-id="2e2cd-174">The symbol table is also updated and next the projection part of the Project is processed.</span></span> <span data-ttu-id="2e2cd-175">Řešení vlastností a sloučení rozsahů spojení je popsané výše.</span><span class="sxs-lookup"><span data-stu-id="2e2cd-175">The resolving of the properties and the flattening of the join extents is as described earlier.</span></span>

<span data-ttu-id="2e2cd-176">![Znázorňuje](./media/9456d6a9-ea2e-40ae-accc-a10e18e28b81.gif "9456d6a9-ea2e-40ae-accc-a10e18e28b81")</span><span class="sxs-lookup"><span data-stu-id="2e2cd-176">![Diagram](./media/9456d6a9-ea2e-40ae-accc-a10e18e28b81.gif "9456d6a9-ea2e-40ae-accc-a10e18e28b81")</span></span>

<span data-ttu-id="2e2cd-177">Nakonec se vytvoří následující SqlSelectStatement:</span><span class="sxs-lookup"><span data-stu-id="2e2cd-177">Finally, the following SqlSelectStatement is produced:</span></span>

```sql
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

### <a name="second-phase-of-sql-generation-generating-the-string-command"></a><span data-ttu-id="2e2cd-178">Druhá fáze generování SQL: vygenerování řetězcového příkazu</span><span class="sxs-lookup"><span data-stu-id="2e2cd-178">Second Phase of SQL Generation: Generating the String Command</span></span>

<span data-ttu-id="2e2cd-179">Druhá fáze vytvoří pro symboly skutečný název a zaměřuje se pouze na symboly představující sloupce s názvem "ČísloObjednávky", jako v tomto případě je třeba vyřešit konflikt.</span><span class="sxs-lookup"><span data-stu-id="2e2cd-179">The second phase produces actual names for the symbols, and we only focus on the symbols representing columns named "OrderID", as in this case a conflict needs to be resolved.</span></span> <span data-ttu-id="2e2cd-180">Ty jsou zvýrazněné v SqlSelectStatement.</span><span class="sxs-lookup"><span data-stu-id="2e2cd-180">These are highlighted in the SqlSelectStatement.</span></span> <span data-ttu-id="2e2cd-181">Všimněte si, že přípony používané na obrázku jsou určeny pouze k zdůraznění, že se jedná o různé instance, nikoli nové názvy, protože v této fázi se jejich konečné názvy (případně jiné pojmenování původních názvů) ještě nepřiřadily.</span><span class="sxs-lookup"><span data-stu-id="2e2cd-181">Note that the suffixes used in the figure are only to emphasize that these are different instances, not to represent any new names, as at this stage their final names (possibly different form the original names) have not been assigned yet.</span></span>

<span data-ttu-id="2e2cd-182">První nalezený symbol, který je třeba přejmenovat, je \<symbol_OrderID >.</span><span class="sxs-lookup"><span data-stu-id="2e2cd-182">The first symbol found that needs to be renamed is \<symbol_OrderID>.</span></span> <span data-ttu-id="2e2cd-183">Jeho nový název je přiřazen jako "OrderID1", 1 je označen jako poslední použitá přípona "KódObjednávky" a symbol je označen jako nepotřebuje se přejmenovat.</span><span class="sxs-lookup"><span data-stu-id="2e2cd-183">Its new name is assigned as "OrderID1", 1 is marked as the last used suffix for "OrderID" and the symbol is marked as not needing renaming.</span></span> <span data-ttu-id="2e2cd-184">V dalším kroku se najde první použití \<symbol_OrderID_2 >.</span><span class="sxs-lookup"><span data-stu-id="2e2cd-184">Next, the first usage of \<symbol_OrderID_2> is found.</span></span> <span data-ttu-id="2e2cd-185">Je přejmenována na použití další dostupné přípony ("OrderID2") a znovu označena jako nepotřebná přejmenování, aby se při příštím použití nepřejmenovala.</span><span class="sxs-lookup"><span data-stu-id="2e2cd-185">It is renamed to use the next available suffix ("OrderID2") and again marked as not needing renaming, so that next time it is used it does not get renamed.</span></span> <span data-ttu-id="2e2cd-186">To se provádí \<symbol_OrderID_3 >.</span><span class="sxs-lookup"><span data-stu-id="2e2cd-186">This is done for \<symbol_OrderID_3> too.</span></span>

<span data-ttu-id="2e2cd-187">Na konci druhé fáze je vygenerován konečný příkaz SQL.</span><span class="sxs-lookup"><span data-stu-id="2e2cd-187">At the end of the second phase, the final SQL statement is generated.</span></span>

## <a name="see-also"></a><span data-ttu-id="2e2cd-188">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2e2cd-188">See also</span></span>

- [<span data-ttu-id="2e2cd-189">Generování SQL ve zprostředkovateli ukázek</span><span class="sxs-lookup"><span data-stu-id="2e2cd-189">SQL Generation in the Sample Provider</span></span>](sql-generation-in-the-sample-provider.md)
