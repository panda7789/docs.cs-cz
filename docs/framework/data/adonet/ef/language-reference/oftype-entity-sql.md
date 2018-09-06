---
title: OFTYPE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 6d259ca7-bbf0-40f8-a154-181d25c0d67e
ms.openlocfilehash: c90950e11cbfca7a49b505c1654d08be504990e1
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43803871"
---
# <a name="oftype-entity-sql"></a><span data-ttu-id="0be42-102">OFTYPE (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="0be42-102">OFTYPE (Entity SQL)</span></span>
<span data-ttu-id="0be42-103">Vrátí kolekci objektů z výrazu dotazu, který je určitého typu.</span><span class="sxs-lookup"><span data-stu-id="0be42-103">Returns a collection of objects from a query expression that is of a specific type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0be42-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0be42-104">Syntax</span></span>  
  
```  
OFTYPE ( expression, [ONLY] test_type )  
```  
  
## <a name="arguments"></a><span data-ttu-id="0be42-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="0be42-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="0be42-106">Libovolný výraz platný dotaz, který vrací kolekce objektů.</span><span class="sxs-lookup"><span data-stu-id="0be42-106">Any valid query expression that returns a collection of objects.</span></span>  
  
 `test_type`  
 <span data-ttu-id="0be42-107">Typ, který chcete otestovat každý objekt vrácený `expression` proti.</span><span class="sxs-lookup"><span data-stu-id="0be42-107">The type to test each object returned by `expression` against.</span></span> <span data-ttu-id="0be42-108">Typ musí být kvalifikován oborem názvů.</span><span class="sxs-lookup"><span data-stu-id="0be42-108">The type must be qualified by a namespace.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0be42-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="0be42-109">Return Value</span></span>  
 <span data-ttu-id="0be42-110">Kolekce objektů, které jsou typu `test_type`, nebo základního typu nebo odvozený typ `test_type`.</span><span class="sxs-lookup"><span data-stu-id="0be42-110">A collection of objects that are of type `test_type`, or a base type or derived type of `test_type`.</span></span> <span data-ttu-id="0be42-111">Pokud je zadána pouze, pouze instance aplikace `test_type` nebo vrátí prázdnou kolekci.</span><span class="sxs-lookup"><span data-stu-id="0be42-111">If ONLY is specified, only instances of the `test_type` or an empty collection will be returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0be42-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0be42-112">Remarks</span></span>  
 <span data-ttu-id="0be42-113">`OFTYPE` Výraz Určuje výraz typu, která je vydala pro typ testu pro každý prvek kolekce.</span><span class="sxs-lookup"><span data-stu-id="0be42-113">An `OFTYPE` expression specifies a type expression that is issued to perform a type test against each element of a collection.</span></span>  <span data-ttu-id="0be42-114">`OFTYPE` Výraz vytvoří novou kolekci obsahující pouze prvky, které byly buď zadaný typ odpovídá typu nebo dílčí typu.</span><span class="sxs-lookup"><span data-stu-id="0be42-114">The `OFTYPE` expression produces a new collection of the specified type containing only those elements that were either equivalent to that type or a sub-type of it.</span></span>  
  
 <span data-ttu-id="0be42-115">`OFTYPE` Výraz je zkratka pro následující výraz dotazu:</span><span class="sxs-lookup"><span data-stu-id="0be42-115">An `OFTYPE` expression is an abbreviation of the following query expression:</span></span>  
  
```  
select value treat(t as T) from ts as t where t is of (T)  
```  
  
 <span data-ttu-id="0be42-116">Vzhledem k tomu, že správce je podtypem typu zaměstnance, následující výraz vytvoří kolekci pouze správci z kolekce zaměstnanců:</span><span class="sxs-lookup"><span data-stu-id="0be42-116">Given that a Manager is a subtype of Employee, the following expression produces a collection of only managers from a collection of employees:</span></span>  
  
```  
OfType(employees, NamespaceName.Manager)  
```  
  
 <span data-ttu-id="0be42-117">Je také možné provést až přetypování pomocí filtru, který typ kolekce:</span><span class="sxs-lookup"><span data-stu-id="0be42-117">It is also possible to up cast a collection using the type filter:</span></span>  
  
```  
OfType(executives, NamespaceName.Manager)  
```  
  
 <span data-ttu-id="0be42-118">Vzhledem k tomu, že všechny vedení manažery, výsledný kolekce stále obsahuje všechny původní vedení, i když kolekce je nyní zadán jako kolekce správci.</span><span class="sxs-lookup"><span data-stu-id="0be42-118">Since all executives are managers, the resulting collection still contains all the original executives, though the collection is now typed as a collection of managers.</span></span>  
  
 <span data-ttu-id="0be42-119">V následující tabulce jsou uvedeny chování `OFTYPE` operátor přes některé vzory.</span><span class="sxs-lookup"><span data-stu-id="0be42-119">The following table shows the behavior of the `OFTYPE` operator over some patterns.</span></span> <span data-ttu-id="0be42-120">Všechny výjimky jsou vyvolány ze strany klienta před vyvoláním zprostředkovatele:</span><span class="sxs-lookup"><span data-stu-id="0be42-120">All exceptions are thrown from the client side before the provider is invoked:</span></span>  
  
|<span data-ttu-id="0be42-121">Vzor</span><span class="sxs-lookup"><span data-stu-id="0be42-121">Pattern</span></span>|<span data-ttu-id="0be42-122">Chování</span><span class="sxs-lookup"><span data-stu-id="0be42-122">Behavior</span></span>|  
|-------------|--------------|  
|<span data-ttu-id="0be42-123">OFTYPE(Collection(EntityType), EntityType)</span><span class="sxs-lookup"><span data-stu-id="0be42-123">OFTYPE(Collection(EntityType), EntityType)</span></span>|<span data-ttu-id="0be42-124">Položku Collection(EntityType)</span><span class="sxs-lookup"><span data-stu-id="0be42-124">Collection(EntityType)</span></span>|  
|<span data-ttu-id="0be42-125">OFTYPE(Collection(complexType), ComplexType)</span><span class="sxs-lookup"><span data-stu-id="0be42-125">OFTYPE(Collection(ComplexType), ComplexType)</span></span>|<span data-ttu-id="0be42-126">Vyvolá výjimku</span><span class="sxs-lookup"><span data-stu-id="0be42-126">Throws</span></span>|  
|<span data-ttu-id="0be42-127">OFTYPE(Collection(RowType), RowType)</span><span class="sxs-lookup"><span data-stu-id="0be42-127">OFTYPE(Collection(RowType), RowType)</span></span>|<span data-ttu-id="0be42-128">Vyvolá výjimku</span><span class="sxs-lookup"><span data-stu-id="0be42-128">Throws</span></span>|  
  
## <a name="example"></a><span data-ttu-id="0be42-129">Příklad</span><span class="sxs-lookup"><span data-stu-id="0be42-129">Example</span></span>  
 <span data-ttu-id="0be42-130">Následující [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dotaz vrací kolekce objektů OnsiteCourse z kolekce samozřejmě objekty pomocí operátoru OFTYPE.</span><span class="sxs-lookup"><span data-stu-id="0be42-130">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the OFTYPE operator to return a collection of OnsiteCourse objects from a collection of Course objects.</span></span> <span data-ttu-id="0be42-131">Dotaz je založen na [školní modelu](https://msdn.microsoft.com/library/859a9587-81ea-4a45-9bc0-f8d330e1adac).</span><span class="sxs-lookup"><span data-stu-id="0be42-131">The query is based on the [School Model](https://msdn.microsoft.com/library/859a9587-81ea-4a45-9bc0-f8d330e1adac).</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#OFTYPE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#oftype)]  
  
## <a name="see-also"></a><span data-ttu-id="0be42-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="0be42-132">See Also</span></span>  
 [<span data-ttu-id="0be42-133">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="0be42-133">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
