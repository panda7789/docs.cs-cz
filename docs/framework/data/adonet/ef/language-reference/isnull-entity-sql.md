---
title: ISNULL (Entity SQL)
ms.date: 03/30/2017
ms.assetid: dc7a0173-3664-4c90-a57b-5cbb0a8ed7ee
ms.openlocfilehash: d54c350196ad1ef7cfafa6d931d9d1ad8f267177
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250561"
---
# <a name="isnull-entity-sql"></a><span data-ttu-id="de109-102">ISNULL (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="de109-102">ISNULL (Entity SQL)</span></span>
<span data-ttu-id="de109-103">Určuje, zda má výraz dotazu hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="de109-103">Determines if a query expression is null.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de109-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="de109-104">Syntax</span></span>  
  
```  
expression IS [ NOT ] NULL  
```  
  
## <a name="arguments"></a><span data-ttu-id="de109-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="de109-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="de109-106">Libovolný platný výraz dotazu.</span><span class="sxs-lookup"><span data-stu-id="de109-106">Any valid query expression.</span></span> <span data-ttu-id="de109-107">Nelze vytvořit kolekci, mít členy kolekce nebo typ záznamu s vlastnostmi typu kolekce.</span><span class="sxs-lookup"><span data-stu-id="de109-107">Cannot be a collection, have collection members, or a record type with collection type properties.</span></span>  
  
 <span data-ttu-id="de109-108">NOT</span><span class="sxs-lookup"><span data-stu-id="de109-108">NOT</span></span>  
 <span data-ttu-id="de109-109">Negace datového modelu EDM. Logický výsledek hodnoty je NULL.</span><span class="sxs-lookup"><span data-stu-id="de109-109">Negates the EDM.Boolean result of IS NULL.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="de109-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="de109-110">Return Value</span></span>  
 <span data-ttu-id="de109-111">`true`Pokud `expression` vrátí hodnotu null, `false`v opačném případě.</span><span class="sxs-lookup"><span data-stu-id="de109-111">`true` if `expression` returns null; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="de109-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="de109-112">Remarks</span></span>  
 <span data-ttu-id="de109-113">Použijte `IS NULL` k určení, zda je prvek vnějšího spojení null:</span><span class="sxs-lookup"><span data-stu-id="de109-113">Use `IS NULL` to determine if the element of an outer join is null:</span></span>  
  
```  
select c   
      from LOB.Customers as c left outer join LOB.Orders as o   
                              on c.ID = o.CustomerID    
      where o is not null and o.OrderQuantity = @x  
```  
  
 <span data-ttu-id="de109-114">Použijte `IS NULL` k určení, zda má člen skutečnou hodnotu:</span><span class="sxs-lookup"><span data-stu-id="de109-114">Use `IS NULL` to determine if a member has an actual value:</span></span>  
  
```  
select c from LOB.Customer as c where c.DOB is not null  
```  
  
 <span data-ttu-id="de109-115">Následující tabulka ukazuje chování `IS NULL` nad některými vzory.</span><span class="sxs-lookup"><span data-stu-id="de109-115">The following table shows the behavior of `IS NULL` over some patterns.</span></span> <span data-ttu-id="de109-116">Všechny výjimky jsou vyvolány na straně klienta před vyvoláním zprostředkovatele:</span><span class="sxs-lookup"><span data-stu-id="de109-116">All exceptions are thrown from the client side before the provider gets invoked:</span></span>  
  
|<span data-ttu-id="de109-117">Vzor</span><span class="sxs-lookup"><span data-stu-id="de109-117">Pattern</span></span>|<span data-ttu-id="de109-118">Chování</span><span class="sxs-lookup"><span data-stu-id="de109-118">Behavior</span></span>|  
|-------------|--------------|  
|<span data-ttu-id="de109-119">hodnota null je NULL.</span><span class="sxs-lookup"><span data-stu-id="de109-119">null IS NULL</span></span>|<span data-ttu-id="de109-120">Vrátí `true`.</span><span class="sxs-lookup"><span data-stu-id="de109-120">Returns `true`.</span></span>|  
|<span data-ttu-id="de109-121">ZPRACOVÁVÁ se (hodnota null jako EntityType) má hodnotu NULL.</span><span class="sxs-lookup"><span data-stu-id="de109-121">TREAT (null AS EntityType) IS NULL</span></span>|<span data-ttu-id="de109-122">Vrátí `true`.</span><span class="sxs-lookup"><span data-stu-id="de109-122">Returns `true`.</span></span>|  
|<span data-ttu-id="de109-123">Považovat za (null jako ComplexType) je NULL.</span><span class="sxs-lookup"><span data-stu-id="de109-123">TREAT (null AS ComplexType) IS NULL</span></span>|<span data-ttu-id="de109-124">Vyvolá chybu.</span><span class="sxs-lookup"><span data-stu-id="de109-124">Throws an error.</span></span>|  
|<span data-ttu-id="de109-125">ZPRACOVÁVÁ se (hodnota null jako RowType) je NULL.</span><span class="sxs-lookup"><span data-stu-id="de109-125">TREAT (null AS RowType) IS NULL</span></span>|<span data-ttu-id="de109-126">Vyvolá chybu.</span><span class="sxs-lookup"><span data-stu-id="de109-126">Throws an error.</span></span>|  
|<span data-ttu-id="de109-127">EntityType má hodnotu NULL.</span><span class="sxs-lookup"><span data-stu-id="de109-127">EntityType IS NULL</span></span>|<span data-ttu-id="de109-128">Vrátí `true` nebo `false`.</span><span class="sxs-lookup"><span data-stu-id="de109-128">Returns `true` or `false`.</span></span>|  
|<span data-ttu-id="de109-129">Typ ComplexType má hodnotu NULL.</span><span class="sxs-lookup"><span data-stu-id="de109-129">ComplexType IS NULL</span></span>|<span data-ttu-id="de109-130">Vyvolá chybu.</span><span class="sxs-lookup"><span data-stu-id="de109-130">Throws an error.</span></span>|  
|<span data-ttu-id="de109-131">RowType má hodnotu NULL.</span><span class="sxs-lookup"><span data-stu-id="de109-131">RowType IS NULL</span></span>|<span data-ttu-id="de109-132">Vyvolá chybu.</span><span class="sxs-lookup"><span data-stu-id="de109-132">Throws an error.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="de109-133">Příklad</span><span class="sxs-lookup"><span data-stu-id="de109-133">Example</span></span>  
 <span data-ttu-id="de109-134">Následující [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dotaz používá operátor is not null k určení, zda výraz dotazu není null.</span><span class="sxs-lookup"><span data-stu-id="de109-134">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the IS NOT NULL operator to determine if a query expression is not null.</span></span> <span data-ttu-id="de109-135">Dotaz je založen na modelu prodeje společnosti AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="de109-135">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="de109-136">Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="de109-136">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="de109-137">Postupujte podle pokynů v [tématu Postupy: Spustí dotaz, který vrátí výsledky](../how-to-execute-a-query-that-returns-structuraltype-results.md)StructuralType.</span><span class="sxs-lookup"><span data-stu-id="de109-137">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="de109-138">Předat následující dotaz jako argument `ExecuteStructuralTypeQuery` metodě:</span><span class="sxs-lookup"><span data-stu-id="de109-138">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#ISNULL](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#isnull)]  
  
## <a name="see-also"></a><span data-ttu-id="de109-139">Viz také:</span><span class="sxs-lookup"><span data-stu-id="de109-139">See also</span></span>

- [<span data-ttu-id="de109-140">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="de109-140">Entity SQL Reference</span></span>](entity-sql-reference.md)
