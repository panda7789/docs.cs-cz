---
title: ISNULL (Entity SQL)
ms.date: 03/30/2017
ms.assetid: dc7a0173-3664-4c90-a57b-5cbb0a8ed7ee
ms.openlocfilehash: 9066f9fb68ce2c50e9523881cfa0dd930cd0b52e
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319735"
---
# <a name="isnull-entity-sql"></a><span data-ttu-id="eca90-102">ISNULL (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="eca90-102">ISNULL (Entity SQL)</span></span>
<span data-ttu-id="eca90-103">Určuje, zda má výraz dotazu hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="eca90-103">Determines if a query expression is null.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eca90-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eca90-104">Syntax</span></span>  
  
```sql  
expression IS [ NOT ] NULL  
```  
  
## <a name="arguments"></a><span data-ttu-id="eca90-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="eca90-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="eca90-106">Libovolný platný výraz dotazu.</span><span class="sxs-lookup"><span data-stu-id="eca90-106">Any valid query expression.</span></span> <span data-ttu-id="eca90-107">Nelze vytvořit kolekci, mít členy kolekce nebo typ záznamu s vlastnostmi typu kolekce.</span><span class="sxs-lookup"><span data-stu-id="eca90-107">Cannot be a collection, have collection members, or a record type with collection type properties.</span></span>  
  
 <span data-ttu-id="eca90-108">MĚNÍ</span><span class="sxs-lookup"><span data-stu-id="eca90-108">NOT</span></span>  
 <span data-ttu-id="eca90-109">Negace datového modelu EDM. Logický výsledek hodnoty je NULL.</span><span class="sxs-lookup"><span data-stu-id="eca90-109">Negates the EDM.Boolean result of IS NULL.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="eca90-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="eca90-110">Return Value</span></span>  
 <span data-ttu-id="eca90-111">`true`, pokud `expression` vrátí hodnotu null; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="eca90-111">`true` if `expression` returns null; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eca90-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="eca90-112">Remarks</span></span>  
 <span data-ttu-id="eca90-113">Chcete-li zjistit, zda je element vnějšího spojení null, použijte `IS NULL`:</span><span class="sxs-lookup"><span data-stu-id="eca90-113">Use `IS NULL` to determine if the element of an outer join is null:</span></span>  
  
```sql  
select c   
      from LOB.Customers as c left outer join LOB.Orders as o   
                              on c.ID = o.CustomerID    
      where o is not null and o.OrderQuantity = @x  
```  
  
 <span data-ttu-id="eca90-114">Chcete-li zjistit, zda má člen skutečnou hodnotu, použijte `IS NULL`:</span><span class="sxs-lookup"><span data-stu-id="eca90-114">Use `IS NULL` to determine if a member has an actual value:</span></span>  
  
```sql  
select c from LOB.Customer as c where c.DOB is not null  
```  
  
 <span data-ttu-id="eca90-115">Následující tabulka ukazuje chování `IS NULL` v některých vzorcích.</span><span class="sxs-lookup"><span data-stu-id="eca90-115">The following table shows the behavior of `IS NULL` over some patterns.</span></span> <span data-ttu-id="eca90-116">Všechny výjimky jsou vyvolány na straně klienta před vyvoláním zprostředkovatele:</span><span class="sxs-lookup"><span data-stu-id="eca90-116">All exceptions are thrown from the client side before the provider gets invoked:</span></span>  
  
|<span data-ttu-id="eca90-117">Vzor</span><span class="sxs-lookup"><span data-stu-id="eca90-117">Pattern</span></span>|<span data-ttu-id="eca90-118">Předvídatelně</span><span class="sxs-lookup"><span data-stu-id="eca90-118">Behavior</span></span>|  
|-------------|--------------|  
|<span data-ttu-id="eca90-119">hodnota null je NULL.</span><span class="sxs-lookup"><span data-stu-id="eca90-119">null IS NULL</span></span>|<span data-ttu-id="eca90-120">Vrátí `true`.</span><span class="sxs-lookup"><span data-stu-id="eca90-120">Returns `true`.</span></span>|  
|<span data-ttu-id="eca90-121">ZPRACOVÁVÁ se (hodnota null jako EntityType) má hodnotu NULL.</span><span class="sxs-lookup"><span data-stu-id="eca90-121">TREAT (null AS EntityType) IS NULL</span></span>|<span data-ttu-id="eca90-122">Vrátí `true`.</span><span class="sxs-lookup"><span data-stu-id="eca90-122">Returns `true`.</span></span>|  
|<span data-ttu-id="eca90-123">Považovat za (null jako ComplexType) je NULL.</span><span class="sxs-lookup"><span data-stu-id="eca90-123">TREAT (null AS ComplexType) IS NULL</span></span>|<span data-ttu-id="eca90-124">Vyvolá chybu.</span><span class="sxs-lookup"><span data-stu-id="eca90-124">Throws an error.</span></span>|  
|<span data-ttu-id="eca90-125">ZPRACOVÁVÁ se (hodnota null jako RowType) je NULL.</span><span class="sxs-lookup"><span data-stu-id="eca90-125">TREAT (null AS RowType) IS NULL</span></span>|<span data-ttu-id="eca90-126">Vyvolá chybu.</span><span class="sxs-lookup"><span data-stu-id="eca90-126">Throws an error.</span></span>|  
|<span data-ttu-id="eca90-127">EntityType má hodnotu NULL.</span><span class="sxs-lookup"><span data-stu-id="eca90-127">EntityType IS NULL</span></span>|<span data-ttu-id="eca90-128">Vrátí `true` nebo `false`.</span><span class="sxs-lookup"><span data-stu-id="eca90-128">Returns `true` or `false`.</span></span>|  
|<span data-ttu-id="eca90-129">Typ ComplexType má hodnotu NULL.</span><span class="sxs-lookup"><span data-stu-id="eca90-129">ComplexType IS NULL</span></span>|<span data-ttu-id="eca90-130">Vyvolá chybu.</span><span class="sxs-lookup"><span data-stu-id="eca90-130">Throws an error.</span></span>|  
|<span data-ttu-id="eca90-131">RowType má hodnotu NULL.</span><span class="sxs-lookup"><span data-stu-id="eca90-131">RowType IS NULL</span></span>|<span data-ttu-id="eca90-132">Vyvolá chybu.</span><span class="sxs-lookup"><span data-stu-id="eca90-132">Throws an error.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="eca90-133">Příklad</span><span class="sxs-lookup"><span data-stu-id="eca90-133">Example</span></span>  
 <span data-ttu-id="eca90-134">Následující dotaz [!INCLUDE[esql](../../../../../../includes/esql-md.md)] používá operátor IS NOT NULL k určení, zda výraz dotazu není null.</span><span class="sxs-lookup"><span data-stu-id="eca90-134">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the IS NOT NULL operator to determine if a query expression is not null.</span></span> <span data-ttu-id="eca90-135">Dotaz je založen na modelu prodeje společnosti AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="eca90-135">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="eca90-136">Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="eca90-136">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="eca90-137">Použijte postup v tématu [Postup: provedení dotazu, který vrátí výsledky StructuralType](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="eca90-137">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="eca90-138">Předat následující dotaz jako argument metodě `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="eca90-138">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#ISNULL](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#isnull)]  
  
## <a name="see-also"></a><span data-ttu-id="eca90-139">Viz také:</span><span class="sxs-lookup"><span data-stu-id="eca90-139">See also</span></span>

- [<span data-ttu-id="eca90-140">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="eca90-140">Entity SQL Reference</span></span>](entity-sql-reference.md)
