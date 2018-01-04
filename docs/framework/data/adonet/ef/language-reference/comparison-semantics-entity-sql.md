---
title: "Porovnání sémantiku (entita SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b36ce28a-2fe4-4236-b782-e5f7c054deae
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 2835d2064f1845b55dd3a33abb086c5af0fb9e6c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="comparison-semantics-entity-sql"></a><span data-ttu-id="df9ae-102">Porovnání sémantiku (entita SQL)</span><span class="sxs-lookup"><span data-stu-id="df9ae-102">Comparison Semantics (Entity SQL)</span></span>
<span data-ttu-id="df9ae-103">Provádění některý z těchto [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operátory zahrnuje porovnání instance typu:</span><span class="sxs-lookup"><span data-stu-id="df9ae-103">Performing any of the following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operators involves comparison of type instances:</span></span>  
  
## <a name="explicit-comparison"></a><span data-ttu-id="df9ae-104">Explicitní porovnání</span><span class="sxs-lookup"><span data-stu-id="df9ae-104">Explicit comparison</span></span>  
 <span data-ttu-id="df9ae-105">Operace rovnosti:</span><span class="sxs-lookup"><span data-stu-id="df9ae-105">Equality operations:</span></span>  
  
-   =  
  
-   <span data-ttu-id="df9ae-106">!=</span><span class="sxs-lookup"><span data-stu-id="df9ae-106">!=</span></span>  
  
 <span data-ttu-id="df9ae-107">Řazení operace:</span><span class="sxs-lookup"><span data-stu-id="df9ae-107">Ordering operations:</span></span>  
  
-   <  
  
-   \<=  
  
-   >  
  
-   \>=  
  
 <span data-ttu-id="df9ae-108">Možnost použití hodnoty Null operace:</span><span class="sxs-lookup"><span data-stu-id="df9ae-108">Nullability operations:</span></span>  
  
-   <span data-ttu-id="df9ae-109">MÁ HODNOTU NULL.</span><span class="sxs-lookup"><span data-stu-id="df9ae-109">IS NULL</span></span>  
  
-   <span data-ttu-id="df9ae-110">NEMÁ HODNOTU NULL</span><span class="sxs-lookup"><span data-stu-id="df9ae-110">IS NOT NULL</span></span>  
  
## <a name="explicit-distinction"></a><span data-ttu-id="df9ae-111">Explicitní rozdíl</span><span class="sxs-lookup"><span data-stu-id="df9ae-111">Explicit distinction</span></span>  
 <span data-ttu-id="df9ae-112">Rovnost rozdíl:</span><span class="sxs-lookup"><span data-stu-id="df9ae-112">Equality distinction:</span></span>  
  
-   <span data-ttu-id="df9ae-113">ODLIŠNÉ</span><span class="sxs-lookup"><span data-stu-id="df9ae-113">DISTINCT</span></span>  
  
-   <span data-ttu-id="df9ae-114">SESKUPIT PODLE</span><span class="sxs-lookup"><span data-stu-id="df9ae-114">GROUP BY</span></span>  
  
 <span data-ttu-id="df9ae-115">Řazení rozdíl:</span><span class="sxs-lookup"><span data-stu-id="df9ae-115">Ordering distinction:</span></span>  
  
-   <span data-ttu-id="df9ae-116">ŘADIT PODLE</span><span class="sxs-lookup"><span data-stu-id="df9ae-116">ORDER BY</span></span>  
  
## <a name="implicit-distinction"></a><span data-ttu-id="df9ae-117">Implicitní rozdíl</span><span class="sxs-lookup"><span data-stu-id="df9ae-117">Implicit distinction</span></span>  
 <span data-ttu-id="df9ae-118">Nastavit operace a predikáty (rovnosti):</span><span class="sxs-lookup"><span data-stu-id="df9ae-118">Set operations and predicates (equality):</span></span>  
  
-   <span data-ttu-id="df9ae-119">UNION</span><span class="sxs-lookup"><span data-stu-id="df9ae-119">UNION</span></span>  
  
-   <span data-ttu-id="df9ae-120">INTERSECT</span><span class="sxs-lookup"><span data-stu-id="df9ae-120">INTERSECT</span></span>  
  
-   <span data-ttu-id="df9ae-121">S VÝJIMKOU</span><span class="sxs-lookup"><span data-stu-id="df9ae-121">EXCEPT</span></span>  
  
-   <span data-ttu-id="df9ae-122">NASTAVENÍ</span><span class="sxs-lookup"><span data-stu-id="df9ae-122">SET</span></span>  
  
-   <span data-ttu-id="df9ae-123">PŘEKRYTÍ.</span><span class="sxs-lookup"><span data-stu-id="df9ae-123">OVERLAPS</span></span>  
  
 <span data-ttu-id="df9ae-124">Položka predikáty (rovnosti):</span><span class="sxs-lookup"><span data-stu-id="df9ae-124">Item predicates (equality):</span></span>  
  
-   <span data-ttu-id="df9ae-125">V</span><span class="sxs-lookup"><span data-stu-id="df9ae-125">IN</span></span>  
  
## <a name="supported-combinations"></a><span data-ttu-id="df9ae-126">Podporované kombinace</span><span class="sxs-lookup"><span data-stu-id="df9ae-126">Supported Combinations</span></span>  
 <span data-ttu-id="df9ae-127">Následující tabulka uvádí podporované kombinace operátory porovnání pro jednotlivé typy typu:</span><span class="sxs-lookup"><span data-stu-id="df9ae-127">The following table shows all the supported combinations of comparison operators for each kind of type:</span></span>  
  
|<span data-ttu-id="df9ae-128">**Typ**</span><span class="sxs-lookup"><span data-stu-id="df9ae-128">**Type**</span></span>|**=**<br /><br /> <span data-ttu-id="df9ae-129">**!=**</span><span class="sxs-lookup"><span data-stu-id="df9ae-129">**!=**</span></span>|<span data-ttu-id="df9ae-130">**GROUP BY**</span><span class="sxs-lookup"><span data-stu-id="df9ae-130">**GROUP BY**</span></span><br /><br /> <span data-ttu-id="df9ae-131">**ODLIŠNÉ**</span><span class="sxs-lookup"><span data-stu-id="df9ae-131">**DISTINCT**</span></span>|<span data-ttu-id="df9ae-132">**UNION**</span><span class="sxs-lookup"><span data-stu-id="df9ae-132">**UNION**</span></span><br /><br /> <span data-ttu-id="df9ae-133">**INTERSECT**</span><span class="sxs-lookup"><span data-stu-id="df9ae-133">**INTERSECT**</span></span><br /><br /> <span data-ttu-id="df9ae-134">**EXCEPT**</span><span class="sxs-lookup"><span data-stu-id="df9ae-134">**EXCEPT**</span></span><br /><br /> <span data-ttu-id="df9ae-135">**SET**</span><span class="sxs-lookup"><span data-stu-id="df9ae-135">**SET**</span></span><br /><br /> <span data-ttu-id="df9ae-136">**OVERLAPS**</span><span class="sxs-lookup"><span data-stu-id="df9ae-136">**OVERLAPS**</span></span>|<span data-ttu-id="df9ae-137">**IN**</span><span class="sxs-lookup"><span data-stu-id="df9ae-137">**IN**</span></span>|<span data-ttu-id="df9ae-138">**<   <=**</span><span class="sxs-lookup"><span data-stu-id="df9ae-138">**<   <=**</span></span><br /><br /> <span data-ttu-id="df9ae-139">**>   >=**</span><span class="sxs-lookup"><span data-stu-id="df9ae-139">**>   >=**</span></span>|<span data-ttu-id="df9ae-140">**ORDER BY**</span><span class="sxs-lookup"><span data-stu-id="df9ae-140">**ORDER BY**</span></span>|<span data-ttu-id="df9ae-141">**MÁ HODNOTU NULL.**</span><span class="sxs-lookup"><span data-stu-id="df9ae-141">**IS NULL**</span></span><br /><br /> <span data-ttu-id="df9ae-142">**NEMÁ HODNOTU NULL**</span><span class="sxs-lookup"><span data-stu-id="df9ae-142">**IS NOT NULL**</span></span>|  
|-|-|-|-|-|-|-|-|  
|<span data-ttu-id="df9ae-143">Typ entity</span><span class="sxs-lookup"><span data-stu-id="df9ae-143">Entity type</span></span>|<span data-ttu-id="df9ae-144">REF<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="df9ae-144">Ref<sup>1</sup></span></span>|<span data-ttu-id="df9ae-145">Všechny vlastnosti<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="df9ae-145">All properties<sup>2</sup></span></span>|<span data-ttu-id="df9ae-146">Všechny vlastnosti<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="df9ae-146">All properties<sup>2</sup></span></span>|<span data-ttu-id="df9ae-147">Všechny vlastnosti<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="df9ae-147">All properties<sup>2</sup></span></span>|<span data-ttu-id="df9ae-148">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="df9ae-148">Throw<sup>3</sup></span></span>|<span data-ttu-id="df9ae-149">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="df9ae-149">Throw<sup>3</sup></span></span>|<span data-ttu-id="df9ae-150">REF<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="df9ae-150">Ref<sup>1</sup></span></span>|  
|<span data-ttu-id="df9ae-151">Komplexní typ</span><span class="sxs-lookup"><span data-stu-id="df9ae-151">Complex type</span></span>|<span data-ttu-id="df9ae-152">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="df9ae-152">Throw<sup>3</sup></span></span>|<span data-ttu-id="df9ae-153">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="df9ae-153">Throw<sup>3</sup></span></span>|<span data-ttu-id="df9ae-154">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="df9ae-154">Throw<sup>3</sup></span></span>|<span data-ttu-id="df9ae-155">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="df9ae-155">Throw<sup>3</sup></span></span>|<span data-ttu-id="df9ae-156">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="df9ae-156">Throw<sup>3</sup></span></span>|<span data-ttu-id="df9ae-157">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="df9ae-157">Throw<sup>3</sup></span></span>|<span data-ttu-id="df9ae-158">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="df9ae-158">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="df9ae-159">Řádek</span><span class="sxs-lookup"><span data-stu-id="df9ae-159">Row</span></span>|<span data-ttu-id="df9ae-160">Všechny vlastnosti<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="df9ae-160">All properties<sup>4</sup></span></span>|<span data-ttu-id="df9ae-161">Všechny vlastnosti<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="df9ae-161">All properties<sup>4</sup></span></span>|<span data-ttu-id="df9ae-162">Všechny vlastnosti<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="df9ae-162">All properties<sup>4</sup></span></span>|<span data-ttu-id="df9ae-163">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="df9ae-163">Throw<sup>3</sup></span></span>|<span data-ttu-id="df9ae-164">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="df9ae-164">Throw<sup>3</sup></span></span>|<span data-ttu-id="df9ae-165">Všechny vlastnosti<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="df9ae-165">All properties<sup>4</sup></span></span>|<span data-ttu-id="df9ae-166">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="df9ae-166">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="df9ae-167">primitivní typ</span><span class="sxs-lookup"><span data-stu-id="df9ae-167">Primitive type</span></span>|<span data-ttu-id="df9ae-168">Specifický pro zprostředkovatele</span><span class="sxs-lookup"><span data-stu-id="df9ae-168">Provider-specific</span></span>|<span data-ttu-id="df9ae-169">Specifický pro zprostředkovatele</span><span class="sxs-lookup"><span data-stu-id="df9ae-169">Provider-specific</span></span>|<span data-ttu-id="df9ae-170">Specifický pro zprostředkovatele</span><span class="sxs-lookup"><span data-stu-id="df9ae-170">Provider-specific</span></span>|<span data-ttu-id="df9ae-171">Specifický pro zprostředkovatele</span><span class="sxs-lookup"><span data-stu-id="df9ae-171">Provider-specific</span></span>|<span data-ttu-id="df9ae-172">Specifický pro zprostředkovatele</span><span class="sxs-lookup"><span data-stu-id="df9ae-172">Provider-specific</span></span>|<span data-ttu-id="df9ae-173">Specifický pro zprostředkovatele</span><span class="sxs-lookup"><span data-stu-id="df9ae-173">Provider-specific</span></span>|<span data-ttu-id="df9ae-174">Specifický pro zprostředkovatele</span><span class="sxs-lookup"><span data-stu-id="df9ae-174">Provider-specific</span></span>|  
|<span data-ttu-id="df9ae-175">Multimnožina</span><span class="sxs-lookup"><span data-stu-id="df9ae-175">Multiset</span></span>|<span data-ttu-id="df9ae-176">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="df9ae-176">Throw<sup>3</sup></span></span>|<span data-ttu-id="df9ae-177">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="df9ae-177">Throw<sup>3</sup></span></span>|<span data-ttu-id="df9ae-178">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="df9ae-178">Throw<sup>3</sup></span></span>|<span data-ttu-id="df9ae-179">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="df9ae-179">Throw<sup>3</sup></span></span>|<span data-ttu-id="df9ae-180">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="df9ae-180">Throw<sup>3</sup></span></span>|<span data-ttu-id="df9ae-181">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="df9ae-181">Throw<sup>3</sup></span></span>|<span data-ttu-id="df9ae-182">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="df9ae-182">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="df9ae-183">REF</span><span class="sxs-lookup"><span data-stu-id="df9ae-183">Ref</span></span>|<span data-ttu-id="df9ae-184">Ano<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="df9ae-184">Yes<sup>5</sup></span></span>|<span data-ttu-id="df9ae-185">Ano<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="df9ae-185">Yes<sup>5</sup></span></span>|<span data-ttu-id="df9ae-186">Ano<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="df9ae-186">Yes<sup>5</sup></span></span>|<span data-ttu-id="df9ae-187">Ano<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="df9ae-187">Yes<sup>5</sup></span></span>|<span data-ttu-id="df9ae-188">Throw</span><span class="sxs-lookup"><span data-stu-id="df9ae-188">Throw</span></span>|<span data-ttu-id="df9ae-189">Throw</span><span class="sxs-lookup"><span data-stu-id="df9ae-189">Throw</span></span>|<span data-ttu-id="df9ae-190">Ano<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="df9ae-190">Yes<sup>5</sup></span></span>|  
|<span data-ttu-id="df9ae-191">Přidružení</span><span class="sxs-lookup"><span data-stu-id="df9ae-191">Association</span></span><br /><br /> <span data-ttu-id="df9ae-192">– typ</span><span class="sxs-lookup"><span data-stu-id="df9ae-192">type</span></span>|<span data-ttu-id="df9ae-193">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="df9ae-193">Throw<sup>3</sup></span></span>|<span data-ttu-id="df9ae-194">Throw</span><span class="sxs-lookup"><span data-stu-id="df9ae-194">Throw</span></span>|<span data-ttu-id="df9ae-195">Throw</span><span class="sxs-lookup"><span data-stu-id="df9ae-195">Throw</span></span>|<span data-ttu-id="df9ae-196">Throw</span><span class="sxs-lookup"><span data-stu-id="df9ae-196">Throw</span></span>|<span data-ttu-id="df9ae-197">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="df9ae-197">Throw<sup>3</sup></span></span>|<span data-ttu-id="df9ae-198">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="df9ae-198">Throw<sup>3</sup></span></span>|<span data-ttu-id="df9ae-199">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="df9ae-199">Throw<sup>3</sup></span></span>|  
  
 <span data-ttu-id="df9ae-200"><sup>1</sup>odkazy na danou entitu typu instancí jsou implicitně porovnání, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="df9ae-200"><sup>1</sup>The references of the given entity type instances are implicitly compared, as shown in the following example:</span></span>  
  
```  
SELECT p1, p2   
FROM AdventureWorksEntities.Product AS p1   
     JOIN AdventureWorksEntities.Product AS p2   
WHERE p1 != p2 OR p1 IS NULL  
```  
  
 <span data-ttu-id="df9ae-201">Entity instance nelze porovnat s explicitní odkaz.</span><span class="sxs-lookup"><span data-stu-id="df9ae-201">An entity instance cannot be compared to an explicit reference.</span></span> <span data-ttu-id="df9ae-202">Pokud je tento pokus, je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="df9ae-202">If this is attempted, an exception is thrown.</span></span> <span data-ttu-id="df9ae-203">Například následující dotaz vyvolá výjimku:</span><span class="sxs-lookup"><span data-stu-id="df9ae-203">For example, the following query will throw an exception:</span></span>  
  
```  
SELECT p1, p2   
FROM AdventureWorksEntities.Product AS p1   
     JOIN AdventureWorksEntities.Product AS p2   
WHERE p1 != REF(p2)  
```  
  
 <span data-ttu-id="df9ae-204"><sup>2</sup>vlastnosti komplexních typů se sloučí před odesláním do úložiště, tak, aby se stala porovnatelný z hlediska (pokud jsou jejich vlastnosti porovnatelný z hlediska).</span><span class="sxs-lookup"><span data-stu-id="df9ae-204"><sup>2</sup>Properties of complex types are flattened out before being sent to the store, so they become comparable (as long as all their properties are comparable).</span></span> <span data-ttu-id="df9ae-205">Viz také <sup>4.</sup></span><span class="sxs-lookup"><span data-stu-id="df9ae-205">Also see <sup>4.</sup></span></span>  
  
 <span data-ttu-id="df9ae-206"><sup>3</sup>Entity Framework runtime zjistí nepodporované případ a vyvolá smysluplný výjimky bez zapojení zprostředkovatele nebo úložiště.</span><span class="sxs-lookup"><span data-stu-id="df9ae-206"><sup>3</sup>The Entity Framework runtime detects the unsupported case and throws a meaningful exception without engaging the provider/store.</span></span>  
  
 <span data-ttu-id="df9ae-207"><sup>4</sup>je proveden pokus o porovnat všechny vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="df9ae-207"><sup>4</sup>An attempt is made to compare all properties.</span></span> <span data-ttu-id="df9ae-208">Pokud je vlastnost, která není porovnatelný z hlediska typu, jako je text, ntext nebo image, může být vyvolána výjimka serveru.</span><span class="sxs-lookup"><span data-stu-id="df9ae-208">If there is a property that is of a non-comparable type, such as text, ntext, or image, a server exception might be thrown.</span></span>  
  
 <span data-ttu-id="df9ae-209"><sup>5</sup>všechny jednotlivé elementy odkazy jsou porovnávány (to zahrnuje název sady entit a všechny vlastnosti klíče typu entity).</span><span class="sxs-lookup"><span data-stu-id="df9ae-209"><sup>5</sup>All individual elements of the references are compared (this includes the entity set name and all the key properties of the entity type).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df9ae-210">Viz také</span><span class="sxs-lookup"><span data-stu-id="df9ae-210">See Also</span></span>  
 [<span data-ttu-id="df9ae-211">Přehled Entity SQL</span><span class="sxs-lookup"><span data-stu-id="df9ae-211">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
