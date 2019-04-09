---
title: ISNULL (Entity SQL)
ms.date: 03/30/2017
ms.assetid: dc7a0173-3664-4c90-a57b-5cbb0a8ed7ee
ms.openlocfilehash: 894d3ab91623aa4246bf7735fb1b7d04e066825a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59072633"
---
# <a name="isnull-entity-sql"></a><span data-ttu-id="6ca00-102">ISNULL (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="6ca00-102">ISNULL (Entity SQL)</span></span>
<span data-ttu-id="6ca00-103">Určuje, zda výraz dotazu je null.</span><span class="sxs-lookup"><span data-stu-id="6ca00-103">Determines if a query expression is null.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ca00-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6ca00-104">Syntax</span></span>  
  
```  
expression IS [ NOT ] NULL  
```  
  
## <a name="arguments"></a><span data-ttu-id="6ca00-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="6ca00-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="6ca00-106">Libovolný výraz platný dotaz.</span><span class="sxs-lookup"><span data-stu-id="6ca00-106">Any valid query expression.</span></span> <span data-ttu-id="6ca00-107">Nemůže být kolekce, mají členy kolekce, nebo typ záznamu se shromažďováním dat pro vlastnosti typu.</span><span class="sxs-lookup"><span data-stu-id="6ca00-107">Cannot be a collection, have collection members, or a record type with collection type properties.</span></span>  
  
 <span data-ttu-id="6ca00-108">NOT</span><span class="sxs-lookup"><span data-stu-id="6ca00-108">NOT</span></span>  
 <span data-ttu-id="6ca00-109">Neguje modelu EDM. Výsledek logickou hodnotu je null.</span><span class="sxs-lookup"><span data-stu-id="6ca00-109">Negates the EDM.Boolean result of IS NULL.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6ca00-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="6ca00-110">Return Value</span></span>  
 `true` <span data-ttu-id="6ca00-111">Pokud `expression` vrátí hodnotu null; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="6ca00-111">if `expression` returns null; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6ca00-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6ca00-112">Remarks</span></span>  
 <span data-ttu-id="6ca00-113">Použití `IS NULL` k určení, zda elementu vnější spojení je null:</span><span class="sxs-lookup"><span data-stu-id="6ca00-113">Use `IS NULL` to determine if the element of an outer join is null:</span></span>  
  
```  
select c   
      from LOB.Customers as c left outer join LOB.Orders as o   
                              on c.ID = o.CustomerID    
      where o is not null and o.OrderQuantity = @x  
```  
  
 <span data-ttu-id="6ca00-114">Použití `IS NULL` k určení, zda člen má skutečná hodnota:</span><span class="sxs-lookup"><span data-stu-id="6ca00-114">Use `IS NULL` to determine if a member has an actual value:</span></span>  
  
```  
select c from LOB.Customer as c where c.DOB is not null  
```  
  
 <span data-ttu-id="6ca00-115">V následující tabulce jsou uvedeny chování `IS NULL` přes některé vzory.</span><span class="sxs-lookup"><span data-stu-id="6ca00-115">The following table shows the behavior of `IS NULL` over some patterns.</span></span> <span data-ttu-id="6ca00-116">Všechny výjimky jsou vyvolány ze strany klienta předtím, než je volán za zprostředkovatele:</span><span class="sxs-lookup"><span data-stu-id="6ca00-116">All exceptions are thrown from the client side before the provider gets invoked:</span></span>  
  
|<span data-ttu-id="6ca00-117">Vzor</span><span class="sxs-lookup"><span data-stu-id="6ca00-117">Pattern</span></span>|<span data-ttu-id="6ca00-118">Chování</span><span class="sxs-lookup"><span data-stu-id="6ca00-118">Behavior</span></span>|  
|-------------|--------------|  
|<span data-ttu-id="6ca00-119">NULL je NULL</span><span class="sxs-lookup"><span data-stu-id="6ca00-119">null IS NULL</span></span>|<span data-ttu-id="6ca00-120">Vrátí `true`.</span><span class="sxs-lookup"><span data-stu-id="6ca00-120">Returns `true`.</span></span>|  
|<span data-ttu-id="6ca00-121">POVAŽOVAT (třída EntityType hodnotu null jako) je NULL</span><span class="sxs-lookup"><span data-stu-id="6ca00-121">TREAT (null AS EntityType) IS NULL</span></span>|<span data-ttu-id="6ca00-122">Vrátí `true`.</span><span class="sxs-lookup"><span data-stu-id="6ca00-122">Returns `true`.</span></span>|  
|<span data-ttu-id="6ca00-123">POVAŽOVAT (null jako ComplexType) je NULL</span><span class="sxs-lookup"><span data-stu-id="6ca00-123">TREAT (null AS ComplexType) IS NULL</span></span>|<span data-ttu-id="6ca00-124">Vyvolá chybu.</span><span class="sxs-lookup"><span data-stu-id="6ca00-124">Throws an error.</span></span>|  
|<span data-ttu-id="6ca00-125">POVAŽOVAT (null jako RowType) je NULL</span><span class="sxs-lookup"><span data-stu-id="6ca00-125">TREAT (null AS RowType) IS NULL</span></span>|<span data-ttu-id="6ca00-126">Vyvolá chybu.</span><span class="sxs-lookup"><span data-stu-id="6ca00-126">Throws an error.</span></span>|  
|<span data-ttu-id="6ca00-127">Typ EntityType má hodnotu NULL.</span><span class="sxs-lookup"><span data-stu-id="6ca00-127">EntityType IS NULL</span></span>|<span data-ttu-id="6ca00-128">Vrátí `true` nebo `false`.</span><span class="sxs-lookup"><span data-stu-id="6ca00-128">Returns `true` or `false`.</span></span>|  
|<span data-ttu-id="6ca00-129">Typ ComplexType má hodnotu NULL.</span><span class="sxs-lookup"><span data-stu-id="6ca00-129">ComplexType IS NULL</span></span>|<span data-ttu-id="6ca00-130">Vyvolá chybu.</span><span class="sxs-lookup"><span data-stu-id="6ca00-130">Throws an error.</span></span>|  
|<span data-ttu-id="6ca00-131">RowType má hodnotu NULL.</span><span class="sxs-lookup"><span data-stu-id="6ca00-131">RowType IS NULL</span></span>|<span data-ttu-id="6ca00-132">Vyvolá chybu.</span><span class="sxs-lookup"><span data-stu-id="6ca00-132">Throws an error.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="6ca00-133">Příklad</span><span class="sxs-lookup"><span data-stu-id="6ca00-133">Example</span></span>  
 <span data-ttu-id="6ca00-134">Následující [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dotazu operátor IS NOT NULL, který se používá k určení, pokud výraz dotazu není null.</span><span class="sxs-lookup"><span data-stu-id="6ca00-134">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the IS NOT NULL operator to determine if a query expression is not null.</span></span> <span data-ttu-id="6ca00-135">Dotaz je založen na modelu Sales AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="6ca00-135">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="6ca00-136">Kompilace a spuštění tohoto dotazu, postupujte podle těchto kroků:</span><span class="sxs-lookup"><span data-stu-id="6ca00-136">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="6ca00-137">Postupujte podle pokynů v [jak: Spustit dotaz, který vrátí výsledky typu StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="6ca00-137">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="6ca00-138">Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="6ca00-138">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#ISNULL](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#isnull)]  
  
## <a name="see-also"></a><span data-ttu-id="6ca00-139">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6ca00-139">See also</span></span>

- [<span data-ttu-id="6ca00-140">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="6ca00-140">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
