---
title: ISNULL (Entita SQL)
ms.date: 03/30/2017
ms.assetid: dc7a0173-3664-4c90-a57b-5cbb0a8ed7ee
ms.openlocfilehash: b3fc2484e80b637ed5841375985f7bae476bbbf7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150197"
---
# <a name="isnull-entity-sql"></a><span data-ttu-id="837ef-102">ISNULL (Entita SQL)</span><span class="sxs-lookup"><span data-stu-id="837ef-102">ISNULL (Entity SQL)</span></span>
<span data-ttu-id="837ef-103">Určuje, zda je výraz dotazu null.</span><span class="sxs-lookup"><span data-stu-id="837ef-103">Determines if a query expression is null.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="837ef-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="837ef-104">Syntax</span></span>  
  
```sql  
expression IS [ NOT ] NULL  
```  
  
## <a name="arguments"></a><span data-ttu-id="837ef-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="837ef-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="837ef-106">Libovolný platný výraz dotazu.</span><span class="sxs-lookup"><span data-stu-id="837ef-106">Any valid query expression.</span></span> <span data-ttu-id="837ef-107">Nemůže být kolekce, mají členy kolekce nebo typ záznamu s vlastnostmi typu kolekce.</span><span class="sxs-lookup"><span data-stu-id="837ef-107">Cannot be a collection, have collection members, or a record type with collection type properties.</span></span>  
  
 <span data-ttu-id="837ef-108">NOT</span><span class="sxs-lookup"><span data-stu-id="837ef-108">NOT</span></span>  
 <span data-ttu-id="837ef-109">Neguje EDM. Logický výsledek hodnoty IS NULL.</span><span class="sxs-lookup"><span data-stu-id="837ef-109">Negates the EDM.Boolean result of IS NULL.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="837ef-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="837ef-110">Return Value</span></span>  
 <span data-ttu-id="837ef-111">`true`pokud `expression` vrátí hodnotu null; v `false`opačném případě .</span><span class="sxs-lookup"><span data-stu-id="837ef-111">`true` if `expression` returns null; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="837ef-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="837ef-112">Remarks</span></span>  
 <span data-ttu-id="837ef-113">Slouží `IS NULL` k určení, zda je prvek vnějšího spojení null:</span><span class="sxs-lookup"><span data-stu-id="837ef-113">Use `IS NULL` to determine if the element of an outer join is null:</span></span>  
  
```sql  
select c
      from LOB.Customers as c left outer join LOB.Orders as o
                              on c.ID = o.CustomerID
      where o is not null and o.OrderQuantity = @x  
```  
  
 <span data-ttu-id="837ef-114">Slouží `IS NULL` k určení, zda má člen skutečnou hodnotu:</span><span class="sxs-lookup"><span data-stu-id="837ef-114">Use `IS NULL` to determine if a member has an actual value:</span></span>  
  
```sql  
select c from LOB.Customer as c where c.DOB is not null  
```  
  
 <span data-ttu-id="837ef-115">V následující tabulce je `IS NULL` uvedeno chování nad některými vzory.</span><span class="sxs-lookup"><span data-stu-id="837ef-115">The following table shows the behavior of `IS NULL` over some patterns.</span></span> <span data-ttu-id="837ef-116">Všechny výjimky jsou vyvolány ze strany klienta před zprostředkovatel získá vyvolána:</span><span class="sxs-lookup"><span data-stu-id="837ef-116">All exceptions are thrown from the client side before the provider gets invoked:</span></span>  
  
|<span data-ttu-id="837ef-117">Vzor</span><span class="sxs-lookup"><span data-stu-id="837ef-117">Pattern</span></span>|<span data-ttu-id="837ef-118">Chování</span><span class="sxs-lookup"><span data-stu-id="837ef-118">Behavior</span></span>|  
|-------------|--------------|  
|<span data-ttu-id="837ef-119">null je null</span><span class="sxs-lookup"><span data-stu-id="837ef-119">null IS NULL</span></span>|<span data-ttu-id="837ef-120">Vrací objekt `true`.</span><span class="sxs-lookup"><span data-stu-id="837ef-120">Returns `true`.</span></span>|  
|<span data-ttu-id="837ef-121">TREAT (null AS EntityType) JE NULL</span><span class="sxs-lookup"><span data-stu-id="837ef-121">TREAT (null AS EntityType) IS NULL</span></span>|<span data-ttu-id="837ef-122">Vrací objekt `true`.</span><span class="sxs-lookup"><span data-stu-id="837ef-122">Returns `true`.</span></span>|  
|<span data-ttu-id="837ef-123">TREAT (null AS ComplexType) JE NULL</span><span class="sxs-lookup"><span data-stu-id="837ef-123">TREAT (null AS ComplexType) IS NULL</span></span>|<span data-ttu-id="837ef-124">Vyvolá chybu.</span><span class="sxs-lookup"><span data-stu-id="837ef-124">Throws an error.</span></span>|  
|<span data-ttu-id="837ef-125">TREAT (null AS Type RowType) JE NULL</span><span class="sxs-lookup"><span data-stu-id="837ef-125">TREAT (null AS RowType) IS NULL</span></span>|<span data-ttu-id="837ef-126">Vyvolá chybu.</span><span class="sxs-lookup"><span data-stu-id="837ef-126">Throws an error.</span></span>|  
|<span data-ttu-id="837ef-127">Typ entity IS NULL</span><span class="sxs-lookup"><span data-stu-id="837ef-127">EntityType IS NULL</span></span>|<span data-ttu-id="837ef-128">Vrátí `true` `false`nebo .</span><span class="sxs-lookup"><span data-stu-id="837ef-128">Returns `true` or `false`.</span></span>|  
|<span data-ttu-id="837ef-129">ComplexType IS NULL</span><span class="sxs-lookup"><span data-stu-id="837ef-129">ComplexType IS NULL</span></span>|<span data-ttu-id="837ef-130">Vyvolá chybu.</span><span class="sxs-lookup"><span data-stu-id="837ef-130">Throws an error.</span></span>|  
|<span data-ttu-id="837ef-131">Typ řádku JE NULL</span><span class="sxs-lookup"><span data-stu-id="837ef-131">RowType IS NULL</span></span>|<span data-ttu-id="837ef-132">Vyvolá chybu.</span><span class="sxs-lookup"><span data-stu-id="837ef-132">Throws an error.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="837ef-133">Příklad</span><span class="sxs-lookup"><span data-stu-id="837ef-133">Example</span></span>  
 <span data-ttu-id="837ef-134">Následující [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dotaz používá operátor IS NOT NULL k určení, zda výraz dotazu není null.</span><span class="sxs-lookup"><span data-stu-id="837ef-134">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the IS NOT NULL operator to determine if a query expression is not null.</span></span> <span data-ttu-id="837ef-135">Dotaz je založen na adventureworks prodejní model.</span><span class="sxs-lookup"><span data-stu-id="837ef-135">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="837ef-136">Chcete-li tento dotaz zkompilovat a spustit, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="837ef-136">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="837ef-137">Postupujte podle postupu v [části Postup: Spusťte dotaz, který vrací výsledky typu StructuralType](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="837ef-137">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="837ef-138">Předat následující dotaz jako argument `ExecuteStructuralTypeQuery` metodě:</span><span class="sxs-lookup"><span data-stu-id="837ef-138">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#ISNULL](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#isnull)]  
  
## <a name="see-also"></a><span data-ttu-id="837ef-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="837ef-139">See also</span></span>

- [<span data-ttu-id="837ef-140">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="837ef-140">Entity SQL Reference</span></span>](entity-sql-reference.md)
