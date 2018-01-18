---
title: OFTYPE (entita SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6d259ca7-bbf0-40f8-a154-181d25c0d67e
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: d85749d697094722930a72114a1b33249f684cf0
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="oftype-entity-sql"></a><span data-ttu-id="ba9c8-102">OFTYPE (entita SQL)</span><span class="sxs-lookup"><span data-stu-id="ba9c8-102">OFTYPE (Entity SQL)</span></span>
<span data-ttu-id="ba9c8-103">Vrátí kolekci objektů z výrazu dotazu, který je určitého typu.</span><span class="sxs-lookup"><span data-stu-id="ba9c8-103">Returns a collection of objects from a query expression that is of a specific type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba9c8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ba9c8-104">Syntax</span></span>  
  
```  
OFTYPE ( expression, [ONLY] test_type )  
```  
  
## <a name="arguments"></a><span data-ttu-id="ba9c8-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="ba9c8-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="ba9c8-106">Libovolný platný dotaz výraz, který vrátí kolekci objektů.</span><span class="sxs-lookup"><span data-stu-id="ba9c8-106">Any valid query expression that returns a collection of objects.</span></span>  
  
 `test_type`  
 <span data-ttu-id="ba9c8-107">Typ k otestování každý objekt vrácený `expression` proti.</span><span class="sxs-lookup"><span data-stu-id="ba9c8-107">The type to test each object returned by `expression` against.</span></span> <span data-ttu-id="ba9c8-108">Typ musí být kvalifikován obor názvů.</span><span class="sxs-lookup"><span data-stu-id="ba9c8-108">The type must be qualified by a namespace.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ba9c8-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="ba9c8-109">Return Value</span></span>  
 <span data-ttu-id="ba9c8-110">Kolekce objektů, které jsou typu `test_type`, nebo základní typ nebo typ odvozené `test_type`.</span><span class="sxs-lookup"><span data-stu-id="ba9c8-110">A collection of objects that are of type `test_type`, or a base type or derived type of `test_type`.</span></span> <span data-ttu-id="ba9c8-111">Pokud je zadána pouze, pouze instance služby `test_type` nebo vrátí prázdnou kolekci.</span><span class="sxs-lookup"><span data-stu-id="ba9c8-111">If ONLY is specified, only instances of the `test_type` or an empty collection will be returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ba9c8-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ba9c8-112">Remarks</span></span>  
 <span data-ttu-id="ba9c8-113">`OFTYPE` Výraz Určuje výraz typu, který je vydán Pokud chcete provést test typ proti každý prvek kolekce.</span><span class="sxs-lookup"><span data-stu-id="ba9c8-113">An `OFTYPE` expression specifies a type expression that is issued to perform a type test against each element of a collection.</span></span>  <span data-ttu-id="ba9c8-114">`OFTYPE` Výraz vytvoří novou kolekci obsahující pouze elementy, které byly buď zadaný typ odpovídá typu nebo dílčí typ ho.</span><span class="sxs-lookup"><span data-stu-id="ba9c8-114">The `OFTYPE` expression produces a new collection of the specified type containing only those elements that were either equivalent to that type or a sub-type of it.</span></span>  
  
 <span data-ttu-id="ba9c8-115">`OFTYPE` Výrazu je zkratkou následující výrazu dotazu:</span><span class="sxs-lookup"><span data-stu-id="ba9c8-115">An `OFTYPE` expression is an abbreviation of the following query expression:</span></span>  
  
```  
select value treat(t as T) from ts as t where t is of (T)  
```  
  
 <span data-ttu-id="ba9c8-116">Vzhledem k tomu, že správce je podtypem zaměstnanců, následující výraz vytvoří kolekci pouze správce z kolekce zaměstnanců:</span><span class="sxs-lookup"><span data-stu-id="ba9c8-116">Given that a Manager is a subtype of Employee, the following expression produces a collection of only managers from a collection of employees:</span></span>  
  
```  
OfType(employees, NamespaceName.Manager)  
```  
  
 <span data-ttu-id="ba9c8-117">Je také možné až přetypování kolekce pomocí filtru typu:</span><span class="sxs-lookup"><span data-stu-id="ba9c8-117">It is also possible to up cast a collection using the type filter:</span></span>  
  
```  
OfType(executives, NamespaceName.Manager)  
```  
  
 <span data-ttu-id="ba9c8-118">Vzhledem k tomu, že všechny vedení správci, výsledná kolekce stále obsahuje všechny původní vedení, i když kolekce je nyní zadán jako kolekce správce.</span><span class="sxs-lookup"><span data-stu-id="ba9c8-118">Since all executives are managers, the resulting collection still contains all the original executives, though the collection is now typed as a collection of managers.</span></span>  
  
 <span data-ttu-id="ba9c8-119">Následující tabulka uvádí chování `OFTYPE` operátor přes některé vzory.</span><span class="sxs-lookup"><span data-stu-id="ba9c8-119">The following table shows the behavior of the `OFTYPE` operator over some patterns.</span></span> <span data-ttu-id="ba9c8-120">Před vyvoláním zprostředkovatele, jsou všechny výjimky vyvolány ze strany klienta:</span><span class="sxs-lookup"><span data-stu-id="ba9c8-120">All exceptions are thrown from the client side before the provider is invoked:</span></span>  
  
|<span data-ttu-id="ba9c8-121">Vzor</span><span class="sxs-lookup"><span data-stu-id="ba9c8-121">Pattern</span></span>|<span data-ttu-id="ba9c8-122">Chování</span><span class="sxs-lookup"><span data-stu-id="ba9c8-122">Behavior</span></span>|  
|-------------|--------------|  
|<span data-ttu-id="ba9c8-123">OFTYPE(Collection(EntityType), EntityType)</span><span class="sxs-lookup"><span data-stu-id="ba9c8-123">OFTYPE(Collection(EntityType), EntityType)</span></span>|<span data-ttu-id="ba9c8-124">Položku Collection(EntityType)</span><span class="sxs-lookup"><span data-stu-id="ba9c8-124">Collection(EntityType)</span></span>|  
|<span data-ttu-id="ba9c8-125">OFTYPE(Collection(complexType), ComplexType)</span><span class="sxs-lookup"><span data-stu-id="ba9c8-125">OFTYPE(Collection(ComplexType), ComplexType)</span></span>|<span data-ttu-id="ba9c8-126">Vyvolá</span><span class="sxs-lookup"><span data-stu-id="ba9c8-126">Throws</span></span>|  
|<span data-ttu-id="ba9c8-127">OFTYPE(Collection(RowType), RowType)</span><span class="sxs-lookup"><span data-stu-id="ba9c8-127">OFTYPE(Collection(RowType), RowType)</span></span>|<span data-ttu-id="ba9c8-128">Vyvolá</span><span class="sxs-lookup"><span data-stu-id="ba9c8-128">Throws</span></span>|  
  
## <a name="example"></a><span data-ttu-id="ba9c8-129">Příklad</span><span class="sxs-lookup"><span data-stu-id="ba9c8-129">Example</span></span>  
 <span data-ttu-id="ba9c8-130">Následující [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dotazu pomocí operátoru OFTYPE vracet kolekci OnsiteCourse objekty z kolekce samozřejmě objekty.</span><span class="sxs-lookup"><span data-stu-id="ba9c8-130">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the OFTYPE operator to return a collection of OnsiteCourse objects from a collection of Course objects.</span></span> <span data-ttu-id="ba9c8-131">Dotaz je na základě [školní modelu](http://msdn.microsoft.com/en-us/859a9587-81ea-4a45-9bc0-f8d330e1adac).</span><span class="sxs-lookup"><span data-stu-id="ba9c8-131">The query is based on the [School Model](http://msdn.microsoft.com/en-us/859a9587-81ea-4a45-9bc0-f8d330e1adac).</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#OFTYPE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#oftype)]  
  
## <a name="see-also"></a><span data-ttu-id="ba9c8-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="ba9c8-132">See Also</span></span>  
 [<span data-ttu-id="ba9c8-133">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="ba9c8-133">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
