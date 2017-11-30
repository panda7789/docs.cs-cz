---
title: ISNULL (entita SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dc7a0173-3664-4c90-a57b-5cbb0a8ed7ee
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 31e0b77e397bd4f190119a01719da185211f7715
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="isnull-entity-sql"></a><span data-ttu-id="d5043-102">ISNULL (entita SQL)</span><span class="sxs-lookup"><span data-stu-id="d5043-102">ISNULL (Entity SQL)</span></span>
<span data-ttu-id="d5043-103">Určuje, pokud má hodnotu null výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="d5043-103">Determines if a query expression is null.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5043-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d5043-104">Syntax</span></span>  
  
```  
expression IS [ NOT ] NULL  
```  
  
## <a name="arguments"></a><span data-ttu-id="d5043-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="d5043-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="d5043-106">Jakýkoli platný dotaz výraz.</span><span class="sxs-lookup"><span data-stu-id="d5043-106">Any valid query expression.</span></span> <span data-ttu-id="d5043-107">Nemůže být kolekce, mít členy kolekce, nebo typ záznamu s kolekcí vlastnosti typu.</span><span class="sxs-lookup"><span data-stu-id="d5043-107">Cannot be a collection, have collection members, or a record type with collection type properties.</span></span>  
  
 <span data-ttu-id="d5043-108">NENÍ</span><span class="sxs-lookup"><span data-stu-id="d5043-108">NOT</span></span>  
 <span data-ttu-id="d5043-109">Neguje EDM. Logická hodnota výsledek je NULL.</span><span class="sxs-lookup"><span data-stu-id="d5043-109">Negates the EDM.Boolean result of IS NULL.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d5043-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="d5043-110">Return Value</span></span>  
 <span data-ttu-id="d5043-111">`true`Pokud `expression` vrátí hodnotu null; jinak hodnota `false`.</span><span class="sxs-lookup"><span data-stu-id="d5043-111">`true` if `expression` returns null; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d5043-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d5043-112">Remarks</span></span>  
 <span data-ttu-id="d5043-113">Použití `IS NULL` k určení, pokud element vnějšího spojení je null:</span><span class="sxs-lookup"><span data-stu-id="d5043-113">Use `IS NULL` to determine if the element of an outer join is null:</span></span>  
  
```  
select c   
      from LOB.Customers as c left outer join LOB.Orders as o   
                              on c.ID = o.CustomerID    
      where o is not null and o.OrderQuantity = @x  
```  
  
 <span data-ttu-id="d5043-114">Použití `IS NULL` k určení, zda člen má skutečnou hodnotu:</span><span class="sxs-lookup"><span data-stu-id="d5043-114">Use `IS NULL` to determine if a member has an actual value:</span></span>  
  
```  
select c from LOB.Customer as c where c.DOB is not null  
```  
  
 <span data-ttu-id="d5043-115">Následující tabulka uvádí chování `IS NULL` přes některé vzory.</span><span class="sxs-lookup"><span data-stu-id="d5043-115">The following table shows the behavior of `IS NULL` over some patterns.</span></span> <span data-ttu-id="d5043-116">Všechny výjimky jsou vyvolány ze strany klienta předtím, než získá volá zprostředkovatele:</span><span class="sxs-lookup"><span data-stu-id="d5043-116">All exceptions are thrown from the client side before the provider gets invoked:</span></span>  
  
|<span data-ttu-id="d5043-117">Vzor</span><span class="sxs-lookup"><span data-stu-id="d5043-117">Pattern</span></span>|<span data-ttu-id="d5043-118">Chování</span><span class="sxs-lookup"><span data-stu-id="d5043-118">Behavior</span></span>|  
|-------------|--------------|  
|<span data-ttu-id="d5043-119">NULL je NULL.</span><span class="sxs-lookup"><span data-stu-id="d5043-119">null IS NULL</span></span>|<span data-ttu-id="d5043-120">Vrátí `true`.</span><span class="sxs-lookup"><span data-stu-id="d5043-120">Returns `true`.</span></span>|  
|<span data-ttu-id="d5043-121">ZPRACOVÁVAT (null AS EntityType) je NULL</span><span class="sxs-lookup"><span data-stu-id="d5043-121">TREAT (null AS EntityType) IS NULL</span></span>|<span data-ttu-id="d5043-122">Vrátí `true`.</span><span class="sxs-lookup"><span data-stu-id="d5043-122">Returns `true`.</span></span>|  
|<span data-ttu-id="d5043-123">ZPRACOVÁVAT (null AS ComplexType) je NULL</span><span class="sxs-lookup"><span data-stu-id="d5043-123">TREAT (null AS ComplexType) IS NULL</span></span>|<span data-ttu-id="d5043-124">Vrátí chybu.</span><span class="sxs-lookup"><span data-stu-id="d5043-124">Throws an error.</span></span>|  
|<span data-ttu-id="d5043-125">ZPRACOVÁVAT (null AS RowType) je NULL</span><span class="sxs-lookup"><span data-stu-id="d5043-125">TREAT (null AS RowType) IS NULL</span></span>|<span data-ttu-id="d5043-126">Vrátí chybu.</span><span class="sxs-lookup"><span data-stu-id="d5043-126">Throws an error.</span></span>|  
|<span data-ttu-id="d5043-127">Typ EntityType má hodnotu NULL.</span><span class="sxs-lookup"><span data-stu-id="d5043-127">EntityType IS NULL</span></span>|<span data-ttu-id="d5043-128">Vrátí `true` nebo `false`.</span><span class="sxs-lookup"><span data-stu-id="d5043-128">Returns `true` or `false`.</span></span>|  
|<span data-ttu-id="d5043-129">Typ ComplexType má hodnotu NULL.</span><span class="sxs-lookup"><span data-stu-id="d5043-129">ComplexType IS NULL</span></span>|<span data-ttu-id="d5043-130">Vrátí chybu.</span><span class="sxs-lookup"><span data-stu-id="d5043-130">Throws an error.</span></span>|  
|<span data-ttu-id="d5043-131">RowType má hodnotu NULL.</span><span class="sxs-lookup"><span data-stu-id="d5043-131">RowType IS NULL</span></span>|<span data-ttu-id="d5043-132">Vrátí chybu.</span><span class="sxs-lookup"><span data-stu-id="d5043-132">Throws an error.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="d5043-133">Příklad</span><span class="sxs-lookup"><span data-stu-id="d5043-133">Example</span></span>  
 <span data-ttu-id="d5043-134">Následující [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dotazu pomocí operátoru IS NOT NULL k určení, pokud výraz dotazu není null.</span><span class="sxs-lookup"><span data-stu-id="d5043-134">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the IS NOT NULL operator to determine if a query expression is not null.</span></span> <span data-ttu-id="d5043-135">Dotaz je založen na modelu prodej AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="d5043-135">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="d5043-136">Pro zkompilování a spuštění tohoto dotazu, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="d5043-136">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="d5043-137">Postupujte podle pokynů v [postup: provedení dotazu tohoto vrátí výsledky StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="d5043-137">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="d5043-138">Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metoda:</span><span class="sxs-lookup"><span data-stu-id="d5043-138">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#ISNULL](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#isnull)]  
  
## <a name="see-also"></a><span data-ttu-id="d5043-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="d5043-139">See Also</span></span>  
 [<span data-ttu-id="d5043-140">Odkaz na entitu SQL</span><span class="sxs-lookup"><span data-stu-id="d5043-140">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
