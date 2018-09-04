---
title: 'Návod: Generování SQL'
ms.date: 03/30/2017
ms.assetid: 16c38aaa-9927-4f3c-ab0f-81636cce57a3
ms.openlocfilehash: 5551eb4088e7529c61d5c517fed6877c23ae12f2
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43510497"
---
# <a name="walkthrough-sql-generation"></a><span data-ttu-id="1423d-102">Návod: Generování SQL</span><span class="sxs-lookup"><span data-stu-id="1423d-102">Walkthrough: SQL Generation</span></span>
<span data-ttu-id="1423d-103">Toto téma ukazuje, jak probíhá generování SQL [zprostředkovateli ukázek](https://go.microsoft.com/fwlink/?LinkId=180616).</span><span class="sxs-lookup"><span data-stu-id="1423d-103">This topic illustrates how SQL generation occurs in the [Sample Provider](https://go.microsoft.com/fwlink/?LinkId=180616).</span></span> <span data-ttu-id="1423d-104">Následující dotaz Entity SQL používá model, který je součástí ukázkového zprostředkovatele:</span><span class="sxs-lookup"><span data-stu-id="1423d-104">The following Entity SQL query uses the model that is included with the sample provider:</span></span>  
  
```  
SELECT  j1.ProductId, j1.ProductName, j1.CategoryName, j2.ShipCountry, j2.ProductId  
FROM (  SELECT P.ProductName, P.ProductId, P.Category.CategoryName  
        FROM NorthwindEntities.Products AS P) as j1  
INNER JOIN (SELECT OD.ProductId, OD.Order.ShipCountry as ShipCountry  
            FROM NorthwindEntities.OrderDetails AS OD) as j2  
            ON j1.ProductId == j2.ProductId   
```  
  
 <span data-ttu-id="1423d-105">Dotaz vytvoří následující výstup příkazu stromu, který je předán do zprostředkovatele:</span><span class="sxs-lookup"><span data-stu-id="1423d-105">The query produces the following output command tree that is passed to the provider:</span></span>  
  
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
  
 <span data-ttu-id="1423d-106">Toto téma popisuje, jak převést tohoto stromu příkazů výstup do těchto příkazů SQL.</span><span class="sxs-lookup"><span data-stu-id="1423d-106">This topic describes how to translate this output command tree into the following SQL statements.</span></span>  
  
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
  
## <a name="first-phase-of-sql-generation-visiting-the-expression-tree"></a><span data-ttu-id="1423d-107">První fázi generování SQL: na strom výrazu</span><span class="sxs-lookup"><span data-stu-id="1423d-107">First Phase of SQL Generation: Visiting the Expression Tree</span></span>  
 <span data-ttu-id="1423d-108">Následující obrázek znázorňuje prázdný počáteční stav návštěvníka.</span><span class="sxs-lookup"><span data-stu-id="1423d-108">The following figure illustrates the initial empty state of the visitor.</span></span>  <span data-ttu-id="1423d-109">V tomto tématu jsou uvedeny pouze vlastnosti, které se týkají vysvětlení návod.</span><span class="sxs-lookup"><span data-stu-id="1423d-109">Throughout this topic, only the properties relevant to the walkthrough explanation are shown.</span></span>  
  
 <span data-ttu-id="1423d-110">![Diagram](../../../../../docs/framework/data/adonet/ef/media/430180f5-4fb9-4bc3-8589-d566512d9703.gif "430180f5-4fb9-4bc3-8589-d566512d9703")</span><span class="sxs-lookup"><span data-stu-id="1423d-110">![Diagram](../../../../../docs/framework/data/adonet/ef/media/430180f5-4fb9-4bc3-8589-d566512d9703.gif "430180f5-4fb9-4bc3-8589-d566512d9703")</span></span>  
  
 <span data-ttu-id="1423d-111">Když je uživatel na uzel projektu, se nazývá VisitInputExpression přes vstup (Join4), která aktivuje návštěvu Join4 metodou VisitJoinExpression.</span><span class="sxs-lookup"><span data-stu-id="1423d-111">When the Project  node is visited, VisitInputExpression is called over its input (Join4), which triggers the visit of Join4 by the method VisitJoinExpression.</span></span> <span data-ttu-id="1423d-112">Protože to je nejvyšší spojení, IsParentAJoin vrátí hodnotu false a nové SqlSelectStatement (SelectStatement0) se vytvoří a posunuto v zásobníku příkazu SELECT.</span><span class="sxs-lookup"><span data-stu-id="1423d-112">Because this is a topmost join, IsParentAJoin returns false and a new SqlSelectStatement (SelectStatement0) is created and pushed on the SELECT statement stack.</span></span> <span data-ttu-id="1423d-113">Navíc nového oboru (scope0) je zadána v tabulce symbolů.</span><span class="sxs-lookup"><span data-stu-id="1423d-113">Also, a new scope (scope0) is entered in the symbol table.</span></span> <span data-ttu-id="1423d-114">Předtím, než je zobrazeny prvního vstupu (vlevo) spojení, 'true' je posunuto v zásobníku IsParentAJoin.</span><span class="sxs-lookup"><span data-stu-id="1423d-114">Before the first (left) input of the join is visited, 'true' is pushed on the IsParentAJoin stack.</span></span> <span data-ttu-id="1423d-115">Těsně před Join1, což je levým vstupem Join4, je navštívili, je stav návštěvníka jak je znázorněno na následujícím obrázku.</span><span class="sxs-lookup"><span data-stu-id="1423d-115">Right before Join1, which is the left input of Join4, is visited, the state of the visitor is as shown in the next figure.</span></span>  
  
 <span data-ttu-id="1423d-116">![Diagram](../../../../../docs/framework/data/adonet/ef/media/406d4f5f-6166-44ea-8e74-c5001d5d5d79.gif "406d4f5f-6166-44ea-8e74-c5001d5d5d79")</span><span class="sxs-lookup"><span data-stu-id="1423d-116">![Diagram](../../../../../docs/framework/data/adonet/ef/media/406d4f5f-6166-44ea-8e74-c5001d5d5d79.gif "406d4f5f-6166-44ea-8e74-c5001d5d5d79")</span></span>  
  
 <span data-ttu-id="1423d-117">Když navštíví spojení přes Join4 je vyvolána metoda, IsParentAJoin má hodnotu true, proto ji znovu použije aktuální příkaz select SelectStatement0.</span><span class="sxs-lookup"><span data-stu-id="1423d-117">When the join visit method is invoked over Join4, IsParentAJoin is true, thus it reuses the current select statement SelectStatement0.</span></span> <span data-ttu-id="1423d-118">Nový obor je zadané (scope1).</span><span class="sxs-lookup"><span data-stu-id="1423d-118">A new scope is entered (scope1).</span></span> <span data-ttu-id="1423d-119">Před jeho levého podřízené Extent1, jiné true je vloženo do zásobníku IsParentAJoin.</span><span class="sxs-lookup"><span data-stu-id="1423d-119">Before visiting its left child, Extent1, another true is pushed on the IsParentAJoin stack.</span></span>  
  
 <span data-ttu-id="1423d-120">Když je uživatel Extent1, protože IsParentAJoin vrací hodnotu true, vrátí SqlBuilder obsahující "[dbo]. [Products] ".</span><span class="sxs-lookup"><span data-stu-id="1423d-120">When Extent1 is visited, because IsParentAJoin returns true, it returns a SqlBuilder containing "[dbo].[Products]".</span></span> <span data-ttu-id="1423d-121">Ovládací prvek vrátí metoda Join4 navštívit.</span><span class="sxs-lookup"><span data-stu-id="1423d-121">The control returns to the method visiting Join4.</span></span> <span data-ttu-id="1423d-122">Záznam je odebrán z IsParentAJoin a ProcessJoinInputResult je volána, která připojí výsledek hostujících Extent1 klauzule From SelectStatement0.</span><span class="sxs-lookup"><span data-stu-id="1423d-122">An entry is popped from IsParentAJoin, and ProcessJoinInputResult is called, which appends the result of visiting Extent1 to the From clause of SelectStatement0.</span></span> <span data-ttu-id="1423d-123">Nový z symbol symbol_Extent1, pro vytvoření názvu Vstupní vazba "Extent1" přidány do FromExtents SelectStatement0 a také "Jak" a symbol_Extent1 jsou připojeny k klauzuli from.</span><span class="sxs-lookup"><span data-stu-id="1423d-123">A new from symbol, symbol_Extent1, for the input binding name "Extent1" is created, added to the FromExtents of SelectStatement0, and also "As" and  symbol_Extent1 are appended to the from clause.</span></span> <span data-ttu-id="1423d-124">Nový záznam se přidá do AllExtentNames pro "Extent1" s hodnotou 0.</span><span class="sxs-lookup"><span data-stu-id="1423d-124">A new entry is added to AllExtentNames for "Extent1" with the value of 0.</span></span> <span data-ttu-id="1423d-125">Přidá nový záznam do aktuálního oboru v tabulce symbolů, které chcete přidružit k její symbol_Extent1 symbol "Extent1".</span><span class="sxs-lookup"><span data-stu-id="1423d-125">A new entry is added to the current scope in the symbol table to associate "Extent1" with its symbol symbol_Extent1.</span></span> <span data-ttu-id="1423d-126">Symbol_Extent1 je taky přidaný ke AllJoinExtents SqlSelectStatement.</span><span class="sxs-lookup"><span data-stu-id="1423d-126">Symbol_Extent1 is also added to the AllJoinExtents of the SqlSelectStatement.</span></span>  
  
 <span data-ttu-id="1423d-127">Předtím, než je pravým vstupem modulu Join1 navštívili, "LEFT OUTER JOIN" je přidána do klauzule From SelectStatement0.</span><span class="sxs-lookup"><span data-stu-id="1423d-127">Before the right input of Join1 is visited, "LEFT OUTER JOIN" is added to the From clause of SelectStatement0.</span></span> <span data-ttu-id="1423d-128">Protože pravým vstupem je výraz kontroly, převede se true znovu IsParentAJoin zásobníku.</span><span class="sxs-lookup"><span data-stu-id="1423d-128">Because the right input is a Scan expression, true is again pushed to the IsParentAJoin stack.</span></span> <span data-ttu-id="1423d-129">Stav, který se před návštěvou pravým vstupem, jak je znázorněno na následujícím obrázku.</span><span class="sxs-lookup"><span data-stu-id="1423d-129">The state before visiting the right input as shown in the next figure.</span></span>  
  
 <span data-ttu-id="1423d-130">![Diagram](../../../../../docs/framework/data/adonet/ef/media/ca62c31b-7ff6-4836-b209-e16166304fdc.gif "ca62c31b-7ff6-4836-b209-e16166304fdc")</span><span class="sxs-lookup"><span data-stu-id="1423d-130">![Diagram](../../../../../docs/framework/data/adonet/ef/media/ca62c31b-7ff6-4836-b209-e16166304fdc.gif "ca62c31b-7ff6-4836-b209-e16166304fdc")</span></span>  
  
 <span data-ttu-id="1423d-131">Správný vstup se zpracovává stejně jako s levým vstupem.</span><span class="sxs-lookup"><span data-stu-id="1423d-131">The right input is processed in the same way as the left input.</span></span> <span data-ttu-id="1423d-132">Stav po přečtení informací pravým vstupem je zobrazen na dalším obrázku.</span><span class="sxs-lookup"><span data-stu-id="1423d-132">The state after visiting the right input is shown in the next figure.</span></span>  
  
 <span data-ttu-id="1423d-133">![Diagram](../../../../../docs/framework/data/adonet/ef/media/cd2afa99-7256-4c63-aaa9-c2d13f18a3d8.gif "cd2afa99-7256-4c63-aaa9-c2d13f18a3d8")</span><span class="sxs-lookup"><span data-stu-id="1423d-133">![Diagram](../../../../../docs/framework/data/adonet/ef/media/cd2afa99-7256-4c63-aaa9-c2d13f18a3d8.gif "cd2afa99-7256-4c63-aaa9-c2d13f18a3d8")</span></span>  
  
 <span data-ttu-id="1423d-134">Další "false" je posunuto v zásobníku IsParentAJoin a podmínky spojení Var(Extent1). ID kategorie == Var(Extent2). ID kategorie se zpracovává.</span><span class="sxs-lookup"><span data-stu-id="1423d-134">Next "false" is pushed on the IsParentAJoin stack and the join condition Var(Extent1).CategoryID == Var(Extent2).CategoryID is processed.</span></span> <span data-ttu-id="1423d-135">Var(Extenent1) je přeložen na < symbol_Extent1 > po pohled nahoru v tabulce symbolů.</span><span class="sxs-lookup"><span data-stu-id="1423d-135">Var(Extenent1) is resolved to <symbol_Extent1> after a look up in the symbol table.</span></span> <span data-ttu-id="1423d-136">Protože instance je přeložit na jednoduché Symbol, jako výsledek zpracování Var(Extent1). ID kategorie, SqlBuilder s \<symbol1 >. " ID kategorie"je vrácena.</span><span class="sxs-lookup"><span data-stu-id="1423d-136">Because the instance is resolved to a simple Symbol, as a result of processing Var(Extent1).CategoryID, a SqlBuilder with \<symbol1>."CategoryID" is returned.</span></span> <span data-ttu-id="1423d-137">Podobně se zpracovává druhé straně porovnání a výsledek hostujících podmínka spojení je připojena k SelectStatement1 a hodnota, kterou "false" je odebrán ze zásobníku IsParentAJoin klauzule FROM.</span><span class="sxs-lookup"><span data-stu-id="1423d-137">Similarly the other side of the comparison is processed, and the result of visiting the join condition is appended to the FROM clause of SelectStatement1 and the value "false" is popped from the IsParentAJoin stack.</span></span>  
  
 <span data-ttu-id="1423d-138">Díky tomu Join1 zcela byla zpracována a obor je odebrán z tabulky symbolů.</span><span class="sxs-lookup"><span data-stu-id="1423d-138">With this, Join1 has completely been processed, and a scope is popped from the symbol table.</span></span>  
  
 <span data-ttu-id="1423d-139">Ovládací prvek vrátí na zpracování Join4 nadřazené Join1.</span><span class="sxs-lookup"><span data-stu-id="1423d-139">Control returns to processing Join4, the parent of Join1.</span></span> <span data-ttu-id="1423d-140">Protože podřízený znovu použít příkaz Select, Join1 rozsahy jsou nahrazeny jednoho symbol Join < joinSymbol_Join1 >.</span><span class="sxs-lookup"><span data-stu-id="1423d-140">Because the child reused the Select statement, the Join1 extents are replaced with a single Join symbol <joinSymbol_Join1>.</span></span> <span data-ttu-id="1423d-141">Také se přidá nový záznam do tabulky symbolů Join1 přidružit < joinSymbol_Join1 >.</span><span class="sxs-lookup"><span data-stu-id="1423d-141">Also a new entry is added to the symbol table to associate Join1 with <joinSymbol_Join1>.</span></span>  
  
 <span data-ttu-id="1423d-142">Další uzel ke zpracování je Join3, druhý podřízený Join4.</span><span class="sxs-lookup"><span data-stu-id="1423d-142">The next node to be processed is Join3, the second child of Join4.</span></span> <span data-ttu-id="1423d-143">Je to správné podřízené, "false" se vloží do zásobníku IsParentAJoin.</span><span class="sxs-lookup"><span data-stu-id="1423d-143">As it is a right child, "false" is pushed to the IsParentAJoin stack.</span></span> <span data-ttu-id="1423d-144">Stav návštěvníka v tomto okamžiku je znázorněno v následující obrázek.</span><span class="sxs-lookup"><span data-stu-id="1423d-144">The state of the visitor at this point is illustrated in the next figure.</span></span>  
  
 <span data-ttu-id="1423d-145">![Diagram](../../../../../docs/framework/data/adonet/ef/media/1ec61ed3-fcdd-4649-9089-24385be7e423.gif "1ec61ed3-fcdd-4649-9089-24385be7e423")</span><span class="sxs-lookup"><span data-stu-id="1423d-145">![Diagram](../../../../../docs/framework/data/adonet/ef/media/1ec61ed3-fcdd-4649-9089-24385be7e423.gif "1ec61ed3-fcdd-4649-9089-24385be7e423")</span></span>  
  
 <span data-ttu-id="1423d-146">IsParentAJoin Join3, vrátí hodnotu false a je potřeba spustit nový SqlSelectStatement (SelectStatement1) a pak ji nasdílet do zásobníku.</span><span class="sxs-lookup"><span data-stu-id="1423d-146">For Join3, IsParentAJoin returns false and needs to start a new SqlSelectStatement (SelectStatement1) and push it on the stack.</span></span> <span data-ttu-id="1423d-147">Zpracování pokračuje podle udělal s předchozím předchozí spojení, nový obor je vloženo do zásobníku a jsou zpracovány podřízené objekty.</span><span class="sxs-lookup"><span data-stu-id="1423d-147">Processing continues as it did with the previous the previous joins, a new scope is pushed on the stack and the children are processed.</span></span> <span data-ttu-id="1423d-148">Levé podřízený člen je v rozsahu (Extent3) a správné podřízená položka spojení (Join2), takže bude také potřeba spustit nový SqlSelectStatement: SelectStatement2.</span><span class="sxs-lookup"><span data-stu-id="1423d-148">The left child is an Extent (Extent3) and the right child is a join (Join2) which also needs to start a new SqlSelectStatement: SelectStatement2.</span></span> <span data-ttu-id="1423d-149">Podřízené položky na Join2 rozsahy jsou také a souhrnně započítávají do SelectStatement2.</span><span class="sxs-lookup"><span data-stu-id="1423d-149">The children on Join2 are Extents as well and are aggregated into SelectStatement2.</span></span>  
  
 <span data-ttu-id="1423d-150">Stav vpravo návštěvníka po Join2 je zobrazeny, ale před jeho po zpracování (ProcessJoinInputResult) se provádí je zobrazen v na následujícím obrázku:</span><span class="sxs-lookup"><span data-stu-id="1423d-150">The state of the visitor right after Join2 is visited, but before its post-processing (ProcessJoinInputResult) is done is shown in the next figure:</span></span>  
  
 <span data-ttu-id="1423d-151">![Diagram](../../../../../docs/framework/data/adonet/ef/media/7510346f-8b09-4c99-b411-40af239c3c4d.gif "7510346f-8b09-4c99-b411-40af239c3c4d")</span><span class="sxs-lookup"><span data-stu-id="1423d-151">![Diagram](../../../../../docs/framework/data/adonet/ef/media/7510346f-8b09-4c99-b411-40af239c3c4d.gif "7510346f-8b09-4c99-b411-40af239c3c4d")</span></span>  
  
 <span data-ttu-id="1423d-152">Na předchozím obrázku se zobrazí SelectStatement2 zdarma s plovoucí desetinnou čárkou protože byl odebrán ze zásobníku, ale dosud příspěvek zpracování nadřazenou položkou.</span><span class="sxs-lookup"><span data-stu-id="1423d-152">In the previous figure, SelectStatement2 is shown as free floating because it was popped out of the stack, but not yet post processed by the parent.</span></span> <span data-ttu-id="1423d-153">Je potřeba přidat do části od nadřazené položky, ale není úplným příkazem SQL bez klauzule SELECT.</span><span class="sxs-lookup"><span data-stu-id="1423d-153">It needs to be added to the FROM part of the parent, but it is not a complete SQL statement without a SELECT clause.</span></span> <span data-ttu-id="1423d-154">Ano v tomto okamžiku výchozích sloupců (všechny sloupce produkované jeho vstupů) jsou přidány do seznamu příkazu select metodou AddDefaultColumns.</span><span class="sxs-lookup"><span data-stu-id="1423d-154">So, at this point, the default columns (all the columns produced by its inputs) are added to the select list by the method AddDefaultColumns.</span></span> <span data-ttu-id="1423d-155">AddDefaultColumns Iteruje přes symboly v FromExtents a pro každý symbol přidá všechny sloupce v oboru.</span><span class="sxs-lookup"><span data-stu-id="1423d-155">AddDefaultColumns iterates over the symbols in FromExtents and for each symbol adds all the columns brought in scope.</span></span> <span data-ttu-id="1423d-156">Pro jednoduché symbol dohlíží na typ symbolu, který pro načtení všech vlastností přidat.</span><span class="sxs-lookup"><span data-stu-id="1423d-156">For a simple symbol, it looks at the symbol type to retrieve all its properties to be added.</span></span> <span data-ttu-id="1423d-157">Naplní také AllColumnNames slovník s názvy sloupců.</span><span class="sxs-lookup"><span data-stu-id="1423d-157">It also populates the AllColumnNames dictionary with the column names.</span></span> <span data-ttu-id="1423d-158">Dokončené SelectStatement2 se připojí k klauzule FROM SelectStatement1.</span><span class="sxs-lookup"><span data-stu-id="1423d-158">The completed SelectStatement2 is appended to the FROM clause of SelectStatement1.</span></span>  
  
 <span data-ttu-id="1423d-159">V dalším kroku se vytvoří nový symbol spojení k reprezentaci Join2, se označí jako vnořené spojení a přidán do AllJoinExtents SelectStatement1 a přidá do tabulky symbolů.</span><span class="sxs-lookup"><span data-stu-id="1423d-159">Next, a new join symbol is created to represent Join2, it is marked as a nested join and added to the AllJoinExtents of SelectStatement1 and added to the symbol table.</span></span>  <span data-ttu-id="1423d-160">Nyní podmínka spojení Join3 Var(Extent3). OrderID = Var(Join2). Extent4.OrderID, je potřeba zpracovat.</span><span class="sxs-lookup"><span data-stu-id="1423d-160">Now the join condition of Join3, Var(Extent3).OrderID =  Var(Join2).Extent4.OrderID, needs to be processed.</span></span> <span data-ttu-id="1423d-161">Zpracování na levé straně je podobný podmínka spojení Join1.</span><span class="sxs-lookup"><span data-stu-id="1423d-161">Processing of the left hand side is similar to the join condition of Join1.</span></span> <span data-ttu-id="1423d-162">Nicméně zpracování doprava a na straně "Var(Join2). Extent4.OrderID"se liší, protože spojení sloučení je povinný.</span><span class="sxs-lookup"><span data-stu-id="1423d-162">However, the processing of the right and side "Var(Join2).Extent4.OrderID" is different because join flattening is required.</span></span>  
  
 <span data-ttu-id="1423d-163">Následující obrázek ukazuje stav návštěvníka těsně před DbPropertyExpression "Var(Join2). Extent4.OrderID", jsou zpracovávána.</span><span class="sxs-lookup"><span data-stu-id="1423d-163">The next figure shows the state of the visitor right before the DbPropertyExpression "Var(Join2).Extent4.OrderID" is processed.</span></span>  
  
 <span data-ttu-id="1423d-164">Vezměte v úvahu jak "Var(Join2). Je-li zobrazeny Extent4.OrderID".</span><span class="sxs-lookup"><span data-stu-id="1423d-164">Consider how "Var(Join2).Extent4.OrderID" is visited.</span></span> <span data-ttu-id="1423d-165">První, vlastnost instance "Var(Join2). Extent4 "je navštívili, což je jiný DbPropertyExpression a první návštěvy své instance"Var(Join2)".</span><span class="sxs-lookup"><span data-stu-id="1423d-165">First, the instance property "Var(Join2).Extent4" is visited, which is another DbPropertyExpression and first visits its instance "Var(Join2)".</span></span> <span data-ttu-id="1423d-166">V oboru nejvyšší většina v tabulce symbolů "Join2" přeloží na < joinSymbol_join2 >.</span><span class="sxs-lookup"><span data-stu-id="1423d-166">In the top most scope in the symbol table, "Join2" resolves to <joinSymbol_join2>.</span></span> <span data-ttu-id="1423d-167">V metodě návštěvu pro DbPropertyExpression zpracování "Var(Join2). Extent4 "Všimněte si, že symbol spojení byla vrácena při návštěvě instance a sloučení.</span><span class="sxs-lookup"><span data-stu-id="1423d-167">In the visit method for DbPropertyExpression processing "Var(Join2).Extent4" notice that a join symbol was returned when visiting the instance and flattening is required.</span></span>  
  
 <span data-ttu-id="1423d-168">Protože je vnořené spojení, jsme vyhledat vlastnost "Extent4" ve slovníku NameToExtent symbolu spojení, ho vyřešit < symbol_Extent4 > a vrátí nový SymbolPair (< joinSymbol_join2 >, < symbol_Extent4 >).</span><span class="sxs-lookup"><span data-stu-id="1423d-168">Since it is a nested join, we look up the property "Extent4" in the NameToExtent dictionary of the join symbol, resolve it to <symbol_Extent4> and return a new SymbolPair(<joinSymbol_join2>, <symbol_Extent4>).</span></span> <span data-ttu-id="1423d-169">Protože dvojice symbol je vrácen z zpracování instance "Var(Join2). Vyřešeno z ColumnPart tento symbol pár (< symbol_Extent4 >), který má seznam sloupců v rozsahu, který představuje Extent4.OrderID", je vlastnost"OrderID".</span><span class="sxs-lookup"><span data-stu-id="1423d-169">Since a symbol pair is returned from the processing of the instance of "Var(Join2).Extent4.OrderID",  the property "OrderID" is resolved from the ColumnPart of that symbol pair (<symbol_Extent4>), which has a list of the columns of the extent it represents.</span></span> <span data-ttu-id="1423d-170">Tedy "Var(Join2). Extent4.OrderID"je přeložen na {< joinSymbol_Join2 >". ", < symbol_OrderID >}.</span><span class="sxs-lookup"><span data-stu-id="1423d-170">So, "Var(Join2).Extent4.OrderID" is resolved to { <joinSymbol_Join2>, ".", <symbol_OrderID>}.</span></span>  
  
 <span data-ttu-id="1423d-171">Podmínka spojení Join4 podobně zpracování.</span><span class="sxs-lookup"><span data-stu-id="1423d-171">The join condition of Join4 is similarly processed.</span></span> <span data-ttu-id="1423d-172">Ovládací prvek vrátí VisitInputExpression metody, který zpracovává horní části většiny projektů.</span><span class="sxs-lookup"><span data-stu-id="1423d-172">The control returns to the VisitInputExpression method that processed the top most project.</span></span> <span data-ttu-id="1423d-173">Prohlížení FromExtents vrácené SelectStatement0, vstup je identifikován jako spojení a odstraní původní mezí a nahradí je nový rozsah se právě symbol spojení.</span><span class="sxs-lookup"><span data-stu-id="1423d-173">Looking at the FromExtents of the returned SelectStatement0, the input is identified as a join, and removes the original extents and replaces them with a new extent with just the Join symbol.</span></span> <span data-ttu-id="1423d-174">Tabulky symbolů je rovněž aktualizováno a další zpracování projekce součástí projektu.</span><span class="sxs-lookup"><span data-stu-id="1423d-174">The symbol table is also updated and next the projection part of the Project is processed.</span></span> <span data-ttu-id="1423d-175">Řešení vlastností a sloučení rozsahy spojení je popsáno výše.</span><span class="sxs-lookup"><span data-stu-id="1423d-175">The resolving of the properties and the flattening of the join extents is as described earlier.</span></span>  
  
 <span data-ttu-id="1423d-176">![Diagram](../../../../../docs/framework/data/adonet/ef/media/9456d6a9-ea2e-40ae-accc-a10e18e28b81.gif "9456d6a9-ea2e-40ae-accc-a10e18e28b81")</span><span class="sxs-lookup"><span data-stu-id="1423d-176">![Diagram](../../../../../docs/framework/data/adonet/ef/media/9456d6a9-ea2e-40ae-accc-a10e18e28b81.gif "9456d6a9-ea2e-40ae-accc-a10e18e28b81")</span></span>  
  
 <span data-ttu-id="1423d-177">Nakonec je vytvořen SqlSelectStatement následující:</span><span class="sxs-lookup"><span data-stu-id="1423d-177">Finally, the following SqlSelectStatement is produced:</span></span>  
  
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
  
### <a name="second-phase-of-sql-generation-generating-the-string-command"></a><span data-ttu-id="1423d-178">Druhá fáze generování SQL: generování příkaz String</span><span class="sxs-lookup"><span data-stu-id="1423d-178">Second Phase of SQL Generation: Generating the String Command</span></span>  
 <span data-ttu-id="1423d-179">Druhá fáze vytvoří skutečné názvy symbolů a zaměříme jenom na symboly představující sloupce s názvem "OrderID", stejně jako v tomto případě ke konfliktu se musí přeložit.</span><span class="sxs-lookup"><span data-stu-id="1423d-179">The second phase produces actual names for the symbols, and we only focus on the symbols representing columns named "OrderID", as in this case a conflict needs to be resolved.</span></span> <span data-ttu-id="1423d-180">Tyto jsou zvýrazněné SqlSelectStatement.</span><span class="sxs-lookup"><span data-stu-id="1423d-180">These are highlighted in the SqlSelectStatement.</span></span> <span data-ttu-id="1423d-181">Všimněte si, že přípony použita na obrázku jsou pouze pro zdůraznit, že jsou různé instance, není k reprezentaci žádné nové názvy v této fáze jejich poslední názvů (by mohly mít odlišné formuláře původní názvy) dosud nebyla přiřazena.</span><span class="sxs-lookup"><span data-stu-id="1423d-181">Note that the suffixes used in the figure are only to emphasize that these are different instances, not to represent any new names, as at this stage their final names (possibly different form the original names) have not been assigned yet.</span></span>  
  
 <span data-ttu-id="1423d-182">První symbol nalezen, které je nutné přejmenovat je < symbol_OrderID >.</span><span class="sxs-lookup"><span data-stu-id="1423d-182">The first symbol found that needs to be renamed is <symbol_OrderID>.</span></span> <span data-ttu-id="1423d-183">Jejím novým názvem je přiřazen jako "OrderID1", 1 je označen jako poslední použitá přípona pro "OrderID" a symbol je označen jako není nutnosti přejmenování.</span><span class="sxs-lookup"><span data-stu-id="1423d-183">Its new name is assigned as "OrderID1", 1 is marked as the last used suffix for "OrderID" and the symbol is marked as not needing renaming.</span></span> <span data-ttu-id="1423d-184">V dalším kroku první využití < symbol_OrderID_2 > nebyl nalezen.</span><span class="sxs-lookup"><span data-stu-id="1423d-184">Next, the first usage of <symbol_OrderID_2> is found.</span></span> <span data-ttu-id="1423d-185">Je přejmenován na tuto příponu použít, další k dispozici ("OrderID2") a znovu se označilo jako vyžadující není přejmenování, tak, aby při příštím se používá ji není přejmenují.</span><span class="sxs-lookup"><span data-stu-id="1423d-185">It is renamed to use the next available suffix ("OrderID2") and again marked as not needing renaming, so that next time it is used it does not get renamed.</span></span> <span data-ttu-id="1423d-186">To se provádí příliš pro < symbol_OrderID_3 >.</span><span class="sxs-lookup"><span data-stu-id="1423d-186">This is done for <symbol_OrderID_3> too.</span></span>  
  
 <span data-ttu-id="1423d-187">Na konci druhé fáze je generována poslední příkaz jazyka SQL.</span><span class="sxs-lookup"><span data-stu-id="1423d-187">At the end of the second phase, the final SQL statement is generated.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1423d-188">Viz také</span><span class="sxs-lookup"><span data-stu-id="1423d-188">See Also</span></span>  
 [<span data-ttu-id="1423d-189">Generování SQL ve zprostředkovateli ukázek</span><span class="sxs-lookup"><span data-stu-id="1423d-189">SQL Generation in the Sample Provider</span></span>](../../../../../docs/framework/data/adonet/ef/sql-generation-in-the-sample-provider.md)
