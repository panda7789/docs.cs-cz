---
title: ISOF (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 5b2b0d34-d0a7-4bcd-baf2-58aa8456d00b
ms.openlocfilehash: 3b746a82f72fc7f42f9d91ddd0a7d6f4f86ac0bb
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250579"
---
# <a name="isof-entity-sql"></a><span data-ttu-id="fc8f8-102">ISOF (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="fc8f8-102">ISOF (Entity SQL)</span></span>
<span data-ttu-id="fc8f8-103">Určuje, zda je typ výrazu zadaného typu nebo některého z jeho podtypů.</span><span class="sxs-lookup"><span data-stu-id="fc8f8-103">Determines whether the type of an expression is of the specified type or one of its subtypes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc8f8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fc8f8-104">Syntax</span></span>  
  
```  
expression IS [ NOT ] OF ( [ ONLY ] type )  
```  
  
## <a name="arguments"></a><span data-ttu-id="fc8f8-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="fc8f8-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="fc8f8-106">Libovolný platný výraz dotazu pro určení typu.</span><span class="sxs-lookup"><span data-stu-id="fc8f8-106">Any valid query expression to determine the type of.</span></span>  
  
 <span data-ttu-id="fc8f8-107">NOT</span><span class="sxs-lookup"><span data-stu-id="fc8f8-107">NOT</span></span>  
 <span data-ttu-id="fc8f8-108">Negace datového modelu EDM. Logický výsledek pro je.</span><span class="sxs-lookup"><span data-stu-id="fc8f8-108">Negates the EDM.Boolean result of IS OF.</span></span>  
  
 <span data-ttu-id="fc8f8-109">POUZE</span><span class="sxs-lookup"><span data-stu-id="fc8f8-109">ONLY</span></span>  
 <span data-ttu-id="fc8f8-110">Určuje, že se vrátí `true` pouze v `expression` případě, že `type` je typu, a ne některého z jeho podtypů.</span><span class="sxs-lookup"><span data-stu-id="fc8f8-110">Specifies that IS OF returns `true` only if `expression` is of type `type` and not any of one its subtypes.</span></span>  
  
 `type`  
 <span data-ttu-id="fc8f8-111">Typ, pro který `expression` se má testovat.</span><span class="sxs-lookup"><span data-stu-id="fc8f8-111">The type to test `expression` against.</span></span> <span data-ttu-id="fc8f8-112">Typ musí být kvalifikovaný v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="fc8f8-112">The type must be namespace-qualified.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fc8f8-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="fc8f8-113">Return Value</span></span>  
 <span data-ttu-id="fc8f8-114">`true`Pokud `expression` je typu t a T je buď základní typ, nebo odvozený `type`typ; null, pokud `expression` má hodnotu null za běhu, jinak `false`.</span><span class="sxs-lookup"><span data-stu-id="fc8f8-114">`true` if `expression` is of type T and T is either a base type, or a derived type of `type`; null if `expression` is null at runtime; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fc8f8-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fc8f8-115">Remarks</span></span>  
 <span data-ttu-id="fc8f8-116">Výrazy `expression IS NOT OF (type)` a `expression IS NOT OF (ONLY type)` `NOT (expression IS OF (ONLY type))`jsousyntaktickyekvivalentní a v uvedeném pořadí. `NOT (expression IS OF (type))`</span><span class="sxs-lookup"><span data-stu-id="fc8f8-116">The expressions `expression IS NOT OF (type)` and `expression IS NOT OF (ONLY type)` are syntactically equivalent to `NOT (expression IS OF (type))` and `NOT (expression IS OF (ONLY type))`, respectively.</span></span>  
  
 <span data-ttu-id="fc8f8-117">Následující tabulka ukazuje chování `IS OF` operátora v některých typických a rohových vzorcích.</span><span class="sxs-lookup"><span data-stu-id="fc8f8-117">The following table shows the behavior of `IS OF` operator over some typical- and corner patterns.</span></span> <span data-ttu-id="fc8f8-118">Všechny výjimky jsou vyvolány na straně klienta před vyvoláním zprostředkovatele:</span><span class="sxs-lookup"><span data-stu-id="fc8f8-118">All exceptions are thrown from the client side before the provider gets invoked:</span></span>  
  
|<span data-ttu-id="fc8f8-119">Vzor</span><span class="sxs-lookup"><span data-stu-id="fc8f8-119">Pattern</span></span>|<span data-ttu-id="fc8f8-120">Chování</span><span class="sxs-lookup"><span data-stu-id="fc8f8-120">Behavior</span></span>|  
|-------------|--------------|  
|<span data-ttu-id="fc8f8-121">hodnota null je typu (EntityType).</span><span class="sxs-lookup"><span data-stu-id="fc8f8-121">null IS OF (EntityType)</span></span>|<span data-ttu-id="fc8f8-122">Vyvolá</span><span class="sxs-lookup"><span data-stu-id="fc8f8-122">Throws</span></span>|  
|<span data-ttu-id="fc8f8-123">hodnota null je (ComplexType).</span><span class="sxs-lookup"><span data-stu-id="fc8f8-123">null IS OF (ComplexType)</span></span>|<span data-ttu-id="fc8f8-124">Vyvolá</span><span class="sxs-lookup"><span data-stu-id="fc8f8-124">Throws</span></span>|  
|<span data-ttu-id="fc8f8-125">hodnota null je (RowType).</span><span class="sxs-lookup"><span data-stu-id="fc8f8-125">null IS OF (RowType)</span></span>|<span data-ttu-id="fc8f8-126">Vyvolá</span><span class="sxs-lookup"><span data-stu-id="fc8f8-126">Throws</span></span>|  
|<span data-ttu-id="fc8f8-127">ZPRACOVÁVÁ se (hodnota null jako EntityType) je typu (EntityType).</span><span class="sxs-lookup"><span data-stu-id="fc8f8-127">TREAT (null AS EntityType) IS OF (EntityType)</span></span>|<span data-ttu-id="fc8f8-128">Vrátí hodnotu DBNull.</span><span class="sxs-lookup"><span data-stu-id="fc8f8-128">Returns DBNull</span></span>|  
|<span data-ttu-id="fc8f8-129">ZPRACOVÁVÁ se (hodnota null jako ComplexType) je (ComplexType).</span><span class="sxs-lookup"><span data-stu-id="fc8f8-129">TREAT (null AS ComplexType) IS OF (ComplexType)</span></span>|<span data-ttu-id="fc8f8-130">Vyvolá</span><span class="sxs-lookup"><span data-stu-id="fc8f8-130">Throws</span></span>|  
|<span data-ttu-id="fc8f8-131">ZPRACOVÁVÁ se (hodnota null jako RowType) je (RowType).</span><span class="sxs-lookup"><span data-stu-id="fc8f8-131">TREAT (null AS RowType) IS OF (RowType)</span></span>|<span data-ttu-id="fc8f8-132">Vyvolá</span><span class="sxs-lookup"><span data-stu-id="fc8f8-132">Throws</span></span>|  
|<span data-ttu-id="fc8f8-133">EntityType je typu (EntityType).</span><span class="sxs-lookup"><span data-stu-id="fc8f8-133">EntityType IS OF (EntityType)</span></span>|<span data-ttu-id="fc8f8-134">Vrátí hodnotu true nebo false.</span><span class="sxs-lookup"><span data-stu-id="fc8f8-134">Returns true/false</span></span>|  
|<span data-ttu-id="fc8f8-135">ComplexType je typu (ComplexType).</span><span class="sxs-lookup"><span data-stu-id="fc8f8-135">ComplexType IS OF (ComplexType)</span></span>|<span data-ttu-id="fc8f8-136">Vyvolá</span><span class="sxs-lookup"><span data-stu-id="fc8f8-136">Throws</span></span>|  
|<span data-ttu-id="fc8f8-137">RowType je (RowType)</span><span class="sxs-lookup"><span data-stu-id="fc8f8-137">RowType IS OF (RowType)</span></span>|<span data-ttu-id="fc8f8-138">Vyvolá</span><span class="sxs-lookup"><span data-stu-id="fc8f8-138">Throws</span></span>|  
  
## <a name="example"></a><span data-ttu-id="fc8f8-139">Příklad</span><span class="sxs-lookup"><span data-stu-id="fc8f8-139">Example</span></span>  
 <span data-ttu-id="fc8f8-140">Následující [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dotaz používá operátor is of k určení typu výrazu dotazu a poté pomocí operátoru "považovat" převést objekt typu kurz na kolekci objektů typu OnsiteCourse.</span><span class="sxs-lookup"><span data-stu-id="fc8f8-140">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the IS OF operator to determine the type of a query expression, and then uses the TREAT operator to convert an object of the type Course to a collection of objects of the type OnsiteCourse.</span></span> <span data-ttu-id="fc8f8-141">Dotaz je založen na [školním modelu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="fc8f8-141">The query is based on the [School Model](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)).</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#TREAT_ISOF](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#treat_isof)]  
  
## <a name="see-also"></a><span data-ttu-id="fc8f8-142">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fc8f8-142">See also</span></span>

- [<span data-ttu-id="fc8f8-143">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="fc8f8-143">Entity SQL Reference</span></span>](entity-sql-reference.md)
