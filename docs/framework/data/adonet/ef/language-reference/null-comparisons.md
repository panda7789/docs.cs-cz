---
title: "Porovnávání s hodnotou Null"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: ef88af8c-8dfe-4556-8b56-81df960a900b
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: fefbd3894063c0298a7ad5110ed6867408869107
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="null-comparisons"></a><span data-ttu-id="8b839-102">Porovnávání s hodnotou Null</span><span class="sxs-lookup"><span data-stu-id="8b839-102">Null Comparisons</span></span>
<span data-ttu-id="8b839-103">A `null` hodnota ve zdroji dat znamená, že hodnota neznámý.</span><span class="sxs-lookup"><span data-stu-id="8b839-103">A `null` value in the data source indicates that the value is unknown.</span></span> <span data-ttu-id="8b839-104">V [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] dotazy, můžete zkontrolovat, že některé výpočty hodnoty null nebo porovnání se provádí pouze na řádky, které mají platný nebo jinou hodnotu než null, data.</span><span class="sxs-lookup"><span data-stu-id="8b839-104">In [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] queries, you can check for null values so that certain calculations or comparisons are only performed on rows that have valid, or non-null, data.</span></span> <span data-ttu-id="8b839-105">CLR sémantiku hodnotu null, ale může lišit od null sémantika zdroj dat.</span><span class="sxs-lookup"><span data-stu-id="8b839-105">CLR null semantics, however, may differ from the null semantics of the data source.</span></span> <span data-ttu-id="8b839-106">Většina databáze použijte verzi s hodnotou tři logiku pro zpracování porovnání null.</span><span class="sxs-lookup"><span data-stu-id="8b839-106">Most databases use a version of three-valued logic to handle null comparisons.</span></span> <span data-ttu-id="8b839-107">To znamená, porovnání s hodnotou null nejsou vyhodnocena `true` nebo `false`, se vyhodnotí jako `unknown`.</span><span class="sxs-lookup"><span data-stu-id="8b839-107">That is, a comparison against a null value does not evaluate to `true` or `false`, it evaluates to `unknown`.</span></span> <span data-ttu-id="8b839-108">Často je jím implementace ANSI hodnoty Null, ale není to vždy.</span><span class="sxs-lookup"><span data-stu-id="8b839-108">Often this is an implementation of ANSI nulls, but this is not always the case.</span></span>  
  
 <span data-ttu-id="8b839-109">Ve výchozím nastavení v systému SQL Server vrátí hodnotu null. rovná null porovnání hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="8b839-109">By default in SQL Server, the null-equals-null comparison returns a null value.</span></span> <span data-ttu-id="8b839-110">V následujícím příkladu, řádky kde `ShipDate` má hodnotu null budou vyloučeny ze sady výsledků a [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] příkaz by vrátit 0 řádků.</span><span class="sxs-lookup"><span data-stu-id="8b839-110">In the following example, the rows where `ShipDate` is null are excluded from the result set, and the [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] statement would return 0 rows.</span></span>  
  
```  
-- Find order details and orders with no ship date.  
SELECT h.SalesOrderID  
FROM Sales.SalesOrderHeader h  
JOIN Sales.SalesOrderDetail o ON o.SalesOrderID = h.SalesOrderID  
WHERE h.ShipDate IS Null  
```  
  
 <span data-ttu-id="8b839-111">Toto je příliš neliší od CLR null sémantikou, kde porovnání null. rovná null, vrátí hodnotu true.</span><span class="sxs-lookup"><span data-stu-id="8b839-111">This is very different from the CLR null semantics, where the null-equals-null comparison returns true.</span></span>  
  
 <span data-ttu-id="8b839-112">Následující dotaz LINQ vyjádřeného v modulu CLR, ale je provést v datovém zdroji.</span><span class="sxs-lookup"><span data-stu-id="8b839-112">The following LINQ query is expressed in the CLR, but it is executed in the data source.</span></span> <span data-ttu-id="8b839-113">Vzhledem k tomu, že neexistuje žádná záruka, že bude CLR sémantiku uplatněn ve zdroji dat, je očekávané chování neurčitou.</span><span class="sxs-lookup"><span data-stu-id="8b839-113">Because there is no guarantee that CLR semantics will be honored at the data source, the expected behavior is indeterminate.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#JoinOnNull](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#joinonnull)]
 [!code-vb[DP L2E Conceptual Examples#JoinOnNull](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#joinonnull)]  
  
## <a name="key-selectors"></a><span data-ttu-id="8b839-114">Selektorů klíče</span><span class="sxs-lookup"><span data-stu-id="8b839-114">Key Selectors</span></span>  
 <span data-ttu-id="8b839-115">A *selektoru klíče* je funkce použité v standardní operátory dotazu extrahovat klíč z elementu.</span><span class="sxs-lookup"><span data-stu-id="8b839-115">A *key selector* is a function used in the standard query operators to extract a key from an element.</span></span> <span data-ttu-id="8b839-116">Ve funkci selektoru klíče je možné porovnávat s konstantní výraz.</span><span class="sxs-lookup"><span data-stu-id="8b839-116">In the key selector function, an expression can be compared with a constant.</span></span> <span data-ttu-id="8b839-117">Null sémantiku CLR jsou vystavených, pokud výraz se porovnává se konstanta null, nebo pokud jsou porovnávány dvě konstanty hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="8b839-117">CLR null semantics are exhibited if an expression is compared to a null constant or if two null constants are compared.</span></span> <span data-ttu-id="8b839-118">Null sémantiky Store jsou vystavených, pokud dva sloupce s hodnotami null ve zdroji dat jsou porovnávány.</span><span class="sxs-lookup"><span data-stu-id="8b839-118">Store null semantics are exhibited if two columns with null values in the data source are compared.</span></span> <span data-ttu-id="8b839-119">Selektorů klíče se nacházejí v mnoha seskupení a řazení standardní operátory dotazu, jako například <xref:System.Linq.Queryable.GroupBy%2A>a slouží k výběru klíče podle kterého k seřazení nebo seskupení výsledků dotazu.</span><span class="sxs-lookup"><span data-stu-id="8b839-119">Key selectors are found in many of the grouping and ordering standard query operators, such as <xref:System.Linq.Queryable.GroupBy%2A>, and are used to select keys by which to order or group the query results.</span></span>  
  
## <a name="null-property-on-a-null-object"></a><span data-ttu-id="8b839-120">Vlastnosti NULL u objektu hodnotu Null.</span><span class="sxs-lookup"><span data-stu-id="8b839-120">Null Property on a Null Object</span></span>  
 <span data-ttu-id="8b839-121">V [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)], vlastnosti na hodnotu null. objekt má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="8b839-121">In the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)], the properties of a null object are null.</span></span> <span data-ttu-id="8b839-122">Když zkusíte odkazovat na vlastnost objektu null v modulu CLR, zobrazí se <xref:System.NullReferenceException>.</span><span class="sxs-lookup"><span data-stu-id="8b839-122">When you attempt to reference a property of a null object in the CLR, you will receive a <xref:System.NullReferenceException>.</span></span> <span data-ttu-id="8b839-123">Pokud dotaz LINQ zahrnuje vlastnost objektu null, to může způsobit nekonzistentní chování.</span><span class="sxs-lookup"><span data-stu-id="8b839-123">When a LINQ query involves a property of a null object, this can result in inconsistent behavior.</span></span>  
  
 <span data-ttu-id="8b839-124">Například v následujícím dotazu, přetypování na `NewProduct` se provádí v vrstvě stromu příkaz, který může mít za následek `Introduced` vlastnost je null.</span><span class="sxs-lookup"><span data-stu-id="8b839-124">For example, in the following query, the cast to `NewProduct` is done in the command tree layer, which might result in the `Introduced` property being null.</span></span> <span data-ttu-id="8b839-125">Pokud databázi definované null porovnání tak, aby <xref:System.DateTime> porovnání se vyhodnotí jako true, budou zahrnuty řádek.</span><span class="sxs-lookup"><span data-stu-id="8b839-125">If the database defined null comparisons such that the <xref:System.DateTime> comparison evaluates to true, the row will be included.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#CastResultsIsNull](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#castresultsisnull)]
 [!code-vb[DP L2E Conceptual Examples#CastResultsIsNull](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#castresultsisnull)]  
  
## <a name="passing-null-collections-to-aggregate-functions"></a><span data-ttu-id="8b839-126">Předání hodnotou Null kolekcí pro agregační funkce</span><span class="sxs-lookup"><span data-stu-id="8b839-126">Passing Null Collections to Aggregate Functions</span></span>  
 <span data-ttu-id="8b839-127">V [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)], při předání kolekce, která podporuje `IQueryable` agregační funkce, agregační operací v databázi.</span><span class="sxs-lookup"><span data-stu-id="8b839-127">In [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)], when you pass a collection that supports `IQueryable` to an aggregate function, aggregate operations are performed at the database.</span></span> <span data-ttu-id="8b839-128">Může docházet k rozdílům ve výsledcích dotazu, který se provádí v paměti a dotaz, který byl proveden v databázi.</span><span class="sxs-lookup"><span data-stu-id="8b839-128">There might be differences in the results of a query that was performed in-memory and a query that was performed at the database.</span></span> <span data-ttu-id="8b839-129">Pomocí dotazu v paměti Pokud nejsou nalezeny žádné shody, dotaz vrátí hodnotu 0.</span><span class="sxs-lookup"><span data-stu-id="8b839-129">With an in-memory query, if there are no matches, the query returns zero.</span></span> <span data-ttu-id="8b839-130">V databázi, stejný dotaz vrací `null`.</span><span class="sxs-lookup"><span data-stu-id="8b839-130">At the database, the same query returns `null`.</span></span> <span data-ttu-id="8b839-131">Pokud `null` LINQ agregační funkci je předána hodnota, bude vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="8b839-131">If a `null` value is passed to a LINQ aggregate function, an exception will be thrown.</span></span> <span data-ttu-id="8b839-132">Tak, aby přijímal možné `null` přetypovat hodnoty, typy a vlastnosti typy, které zobrazí výsledky dotazu a typy podporující hodnoty Null.</span><span class="sxs-lookup"><span data-stu-id="8b839-132">To accept possible `null` values, cast the types and the properties of the types that receive query results to nullable types.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b839-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="8b839-133">See Also</span></span>  
 [<span data-ttu-id="8b839-134">Výrazy v technologii LINQ to Entities dotazy</span><span class="sxs-lookup"><span data-stu-id="8b839-134">Expressions in LINQ to Entities Queries</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/expressions-in-linq-to-entities-queries.md)
