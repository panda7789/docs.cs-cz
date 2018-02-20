---
title: "Porovnání sémantiku (entita SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b36ce28a-2fe4-4236-b782-e5f7c054deae
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: e20d47e0ae97067d2dcafcf929f717598d4e3e80
ms.sourcegitcommit: 96cc82cac4650adfb65ba351506d8a8fbcd17b5c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2018
---
# <a name="comparison-semantics-entity-sql"></a><span data-ttu-id="70532-102">Porovnání sémantiku (entita SQL)</span><span class="sxs-lookup"><span data-stu-id="70532-102">Comparison Semantics (Entity SQL)</span></span>
<span data-ttu-id="70532-103">Provádění některý z těchto [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operátory zahrnuje porovnání instance typu:</span><span class="sxs-lookup"><span data-stu-id="70532-103">Performing any of the following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operators involves comparison of type instances:</span></span>  
  
## <a name="explicit-comparison"></a><span data-ttu-id="70532-104">Explicitní porovnání</span><span class="sxs-lookup"><span data-stu-id="70532-104">Explicit comparison</span></span>  
 <span data-ttu-id="70532-105">Operace rovnosti:</span><span class="sxs-lookup"><span data-stu-id="70532-105">Equality operations:</span></span>  
  
-   =  
  
-   <span data-ttu-id="70532-106">!=</span><span class="sxs-lookup"><span data-stu-id="70532-106">!=</span></span>  
  
 <span data-ttu-id="70532-107">Řazení operace:</span><span class="sxs-lookup"><span data-stu-id="70532-107">Ordering operations:</span></span>  
  
-   <  
  
-   \<=  
  
-   \>  
  
-   \>=  
  
 <span data-ttu-id="70532-108">Možnost použití hodnoty Null operace:</span><span class="sxs-lookup"><span data-stu-id="70532-108">Nullability operations:</span></span>  
  
-   <span data-ttu-id="70532-109">MÁ HODNOTU NULL.</span><span class="sxs-lookup"><span data-stu-id="70532-109">IS NULL</span></span>  
  
-   <span data-ttu-id="70532-110">NEMÁ HODNOTU NULL</span><span class="sxs-lookup"><span data-stu-id="70532-110">IS NOT NULL</span></span>  
  
## <a name="explicit-distinction"></a><span data-ttu-id="70532-111">Explicitní rozdíl</span><span class="sxs-lookup"><span data-stu-id="70532-111">Explicit distinction</span></span>  
 <span data-ttu-id="70532-112">Rovnost rozdíl:</span><span class="sxs-lookup"><span data-stu-id="70532-112">Equality distinction:</span></span>  
  
-   <span data-ttu-id="70532-113">DISTINCT</span><span class="sxs-lookup"><span data-stu-id="70532-113">DISTINCT</span></span>  
  
-   <span data-ttu-id="70532-114">SESKUPIT PODLE</span><span class="sxs-lookup"><span data-stu-id="70532-114">GROUP BY</span></span>  
  
 <span data-ttu-id="70532-115">Řazení rozdíl:</span><span class="sxs-lookup"><span data-stu-id="70532-115">Ordering distinction:</span></span>  
  
-   <span data-ttu-id="70532-116">ŘADIT PODLE</span><span class="sxs-lookup"><span data-stu-id="70532-116">ORDER BY</span></span>  
  
## <a name="implicit-distinction"></a><span data-ttu-id="70532-117">Implicitní rozdíl</span><span class="sxs-lookup"><span data-stu-id="70532-117">Implicit distinction</span></span>  
 <span data-ttu-id="70532-118">Nastavit operace a predikáty (rovnosti):</span><span class="sxs-lookup"><span data-stu-id="70532-118">Set operations and predicates (equality):</span></span>  
  
-   <span data-ttu-id="70532-119">UNION</span><span class="sxs-lookup"><span data-stu-id="70532-119">UNION</span></span>  
  
-   <span data-ttu-id="70532-120">INTERSECT</span><span class="sxs-lookup"><span data-stu-id="70532-120">INTERSECT</span></span>  
  
-   <span data-ttu-id="70532-121">S VÝJIMKOU</span><span class="sxs-lookup"><span data-stu-id="70532-121">EXCEPT</span></span>  
  
-   <span data-ttu-id="70532-122">NASTAVENÍ</span><span class="sxs-lookup"><span data-stu-id="70532-122">SET</span></span>  
  
-   <span data-ttu-id="70532-123">PŘEKRYTÍ.</span><span class="sxs-lookup"><span data-stu-id="70532-123">OVERLAPS</span></span>  
  
 <span data-ttu-id="70532-124">Položka predikáty (rovnosti):</span><span class="sxs-lookup"><span data-stu-id="70532-124">Item predicates (equality):</span></span>  
  
-   <span data-ttu-id="70532-125">V</span><span class="sxs-lookup"><span data-stu-id="70532-125">IN</span></span>  
  
## <a name="supported-combinations"></a><span data-ttu-id="70532-126">Podporované kombinace</span><span class="sxs-lookup"><span data-stu-id="70532-126">Supported Combinations</span></span>  
 <span data-ttu-id="70532-127">Následující tabulka uvádí podporované kombinace operátory porovnání pro jednotlivé typy typu:</span><span class="sxs-lookup"><span data-stu-id="70532-127">The following table shows all the supported combinations of comparison operators for each kind of type:</span></span>  
  
|<span data-ttu-id="70532-128">Typ</span><span class="sxs-lookup"><span data-stu-id="70532-128">**Type**</span></span>|**=**<br /><br /> <span data-ttu-id="70532-129">**!=**</span><span class="sxs-lookup"><span data-stu-id="70532-129">**!=**</span></span>|<span data-ttu-id="70532-130">**GROUP BY**</span><span class="sxs-lookup"><span data-stu-id="70532-130">**GROUP BY**</span></span><br /><br /> <span data-ttu-id="70532-131">**DISTINCT**</span><span class="sxs-lookup"><span data-stu-id="70532-131">**DISTINCT**</span></span>|<span data-ttu-id="70532-132">**UNION**</span><span class="sxs-lookup"><span data-stu-id="70532-132">**UNION**</span></span><br /><br /> <span data-ttu-id="70532-133">**INTERSECT**</span><span class="sxs-lookup"><span data-stu-id="70532-133">**INTERSECT**</span></span><br /><br /> <span data-ttu-id="70532-134">**EXCEPT**</span><span class="sxs-lookup"><span data-stu-id="70532-134">**EXCEPT**</span></span><br /><br /> <span data-ttu-id="70532-135">**SET**</span><span class="sxs-lookup"><span data-stu-id="70532-135">**SET**</span></span><br /><br /> <span data-ttu-id="70532-136">**OVERLAPS**</span><span class="sxs-lookup"><span data-stu-id="70532-136">**OVERLAPS**</span></span>|<span data-ttu-id="70532-137">**IN**</span><span class="sxs-lookup"><span data-stu-id="70532-137">**IN**</span></span>|<span data-ttu-id="70532-138">**<   <=**</span><span class="sxs-lookup"><span data-stu-id="70532-138">**<   <=**</span></span><br /><br /> <span data-ttu-id="70532-139">**>   >=**</span><span class="sxs-lookup"><span data-stu-id="70532-139">**>   >=**</span></span>|<span data-ttu-id="70532-140">**ORDER BY**</span><span class="sxs-lookup"><span data-stu-id="70532-140">**ORDER BY**</span></span>|<span data-ttu-id="70532-141">MÁ HODNOTU NULL.</span><span class="sxs-lookup"><span data-stu-id="70532-141">**IS NULL**</span></span><br /><br /> <span data-ttu-id="70532-142">NEMÁ HODNOTU NULL</span><span class="sxs-lookup"><span data-stu-id="70532-142">**IS NOT NULL**</span></span>|  
|-|-|-|-|-|-|-|-|  
|<span data-ttu-id="70532-143">Typ entity</span><span class="sxs-lookup"><span data-stu-id="70532-143">Entity type</span></span>|<span data-ttu-id="70532-144">Ref<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="70532-144">Ref<sup>1</sup></span></span>|<span data-ttu-id="70532-145">Všechny vlastnosti<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="70532-145">All properties<sup>2</sup></span></span>|<span data-ttu-id="70532-146">Všechny vlastnosti<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="70532-146">All properties<sup>2</sup></span></span>|<span data-ttu-id="70532-147">Všechny vlastnosti<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="70532-147">All properties<sup>2</sup></span></span>|<span data-ttu-id="70532-148">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="70532-148">Throw<sup>3</sup></span></span>|<span data-ttu-id="70532-149">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="70532-149">Throw<sup>3</sup></span></span>|<span data-ttu-id="70532-150">Ref<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="70532-150">Ref<sup>1</sup></span></span>|  
|<span data-ttu-id="70532-151">Komplexní typ</span><span class="sxs-lookup"><span data-stu-id="70532-151">Complex type</span></span>|<span data-ttu-id="70532-152">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="70532-152">Throw<sup>3</sup></span></span>|<span data-ttu-id="70532-153">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="70532-153">Throw<sup>3</sup></span></span>|<span data-ttu-id="70532-154">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="70532-154">Throw<sup>3</sup></span></span>|<span data-ttu-id="70532-155">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="70532-155">Throw<sup>3</sup></span></span>|<span data-ttu-id="70532-156">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="70532-156">Throw<sup>3</sup></span></span>|<span data-ttu-id="70532-157">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="70532-157">Throw<sup>3</sup></span></span>|<span data-ttu-id="70532-158">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="70532-158">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="70532-159">Řádek</span><span class="sxs-lookup"><span data-stu-id="70532-159">Row</span></span>|<span data-ttu-id="70532-160">Všechny vlastnosti<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="70532-160">All properties<sup>4</sup></span></span>|<span data-ttu-id="70532-161">Všechny vlastnosti<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="70532-161">All properties<sup>4</sup></span></span>|<span data-ttu-id="70532-162">Všechny vlastnosti<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="70532-162">All properties<sup>4</sup></span></span>|<span data-ttu-id="70532-163">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="70532-163">Throw<sup>3</sup></span></span>|<span data-ttu-id="70532-164">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="70532-164">Throw<sup>3</sup></span></span>|<span data-ttu-id="70532-165">Všechny vlastnosti<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="70532-165">All properties<sup>4</sup></span></span>|<span data-ttu-id="70532-166">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="70532-166">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="70532-167">primitivní typ</span><span class="sxs-lookup"><span data-stu-id="70532-167">Primitive type</span></span>|<span data-ttu-id="70532-168">Specifický pro zprostředkovatele</span><span class="sxs-lookup"><span data-stu-id="70532-168">Provider-specific</span></span>|<span data-ttu-id="70532-169">Specifický pro zprostředkovatele</span><span class="sxs-lookup"><span data-stu-id="70532-169">Provider-specific</span></span>|<span data-ttu-id="70532-170">Specifický pro zprostředkovatele</span><span class="sxs-lookup"><span data-stu-id="70532-170">Provider-specific</span></span>|<span data-ttu-id="70532-171">Specifický pro zprostředkovatele</span><span class="sxs-lookup"><span data-stu-id="70532-171">Provider-specific</span></span>|<span data-ttu-id="70532-172">Specifický pro zprostředkovatele</span><span class="sxs-lookup"><span data-stu-id="70532-172">Provider-specific</span></span>|<span data-ttu-id="70532-173">Specifický pro zprostředkovatele</span><span class="sxs-lookup"><span data-stu-id="70532-173">Provider-specific</span></span>|<span data-ttu-id="70532-174">Specifický pro zprostředkovatele</span><span class="sxs-lookup"><span data-stu-id="70532-174">Provider-specific</span></span>|  
|<span data-ttu-id="70532-175">Multiset</span><span class="sxs-lookup"><span data-stu-id="70532-175">Multiset</span></span>|<span data-ttu-id="70532-176">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="70532-176">Throw<sup>3</sup></span></span>|<span data-ttu-id="70532-177">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="70532-177">Throw<sup>3</sup></span></span>|<span data-ttu-id="70532-178">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="70532-178">Throw<sup>3</sup></span></span>|<span data-ttu-id="70532-179">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="70532-179">Throw<sup>3</sup></span></span>|<span data-ttu-id="70532-180">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="70532-180">Throw<sup>3</sup></span></span>|<span data-ttu-id="70532-181">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="70532-181">Throw<sup>3</sup></span></span>|<span data-ttu-id="70532-182">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="70532-182">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="70532-183">REF</span><span class="sxs-lookup"><span data-stu-id="70532-183">Ref</span></span>|<span data-ttu-id="70532-184">Ano<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="70532-184">Yes<sup>5</sup></span></span>|<span data-ttu-id="70532-185">Ano<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="70532-185">Yes<sup>5</sup></span></span>|<span data-ttu-id="70532-186">Ano<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="70532-186">Yes<sup>5</sup></span></span>|<span data-ttu-id="70532-187">Ano<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="70532-187">Yes<sup>5</sup></span></span>|<span data-ttu-id="70532-188">Throw</span><span class="sxs-lookup"><span data-stu-id="70532-188">Throw</span></span>|<span data-ttu-id="70532-189">Throw</span><span class="sxs-lookup"><span data-stu-id="70532-189">Throw</span></span>|<span data-ttu-id="70532-190">Ano<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="70532-190">Yes<sup>5</sup></span></span>|  
|<span data-ttu-id="70532-191">Přidružení</span><span class="sxs-lookup"><span data-stu-id="70532-191">Association</span></span><br /><br /> <span data-ttu-id="70532-192">– typ</span><span class="sxs-lookup"><span data-stu-id="70532-192">type</span></span>|<span data-ttu-id="70532-193">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="70532-193">Throw<sup>3</sup></span></span>|<span data-ttu-id="70532-194">Throw</span><span class="sxs-lookup"><span data-stu-id="70532-194">Throw</span></span>|<span data-ttu-id="70532-195">Throw</span><span class="sxs-lookup"><span data-stu-id="70532-195">Throw</span></span>|<span data-ttu-id="70532-196">Throw</span><span class="sxs-lookup"><span data-stu-id="70532-196">Throw</span></span>|<span data-ttu-id="70532-197">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="70532-197">Throw<sup>3</sup></span></span>|<span data-ttu-id="70532-198">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="70532-198">Throw<sup>3</sup></span></span>|<span data-ttu-id="70532-199">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="70532-199">Throw<sup>3</sup></span></span>|  
  
 <span data-ttu-id="70532-200"><sup>1</sup>odkazy na danou entitu typu instancí jsou implicitně porovnání, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="70532-200"><sup>1</sup>The references of the given entity type instances are implicitly compared, as shown in the following example:</span></span>  
  
```  
SELECT p1, p2   
FROM AdventureWorksEntities.Product AS p1   
     JOIN AdventureWorksEntities.Product AS p2   
WHERE p1 != p2 OR p1 IS NULL  
```  
  
 <span data-ttu-id="70532-201">Entity instance nelze porovnat s explicitní odkaz.</span><span class="sxs-lookup"><span data-stu-id="70532-201">An entity instance cannot be compared to an explicit reference.</span></span> <span data-ttu-id="70532-202">Pokud je tento pokus, je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="70532-202">If this is attempted, an exception is thrown.</span></span> <span data-ttu-id="70532-203">Například následující dotaz vyvolá výjimku:</span><span class="sxs-lookup"><span data-stu-id="70532-203">For example, the following query will throw an exception:</span></span>  
  
```  
SELECT p1, p2   
FROM AdventureWorksEntities.Product AS p1   
     JOIN AdventureWorksEntities.Product AS p2   
WHERE p1 != REF(p2)  
```  
  
 <span data-ttu-id="70532-204"><sup>2</sup>vlastnosti komplexních typů se sloučí před odesláním do úložiště, tak, aby se stala porovnatelný z hlediska (pokud jsou jejich vlastnosti porovnatelný z hlediska).</span><span class="sxs-lookup"><span data-stu-id="70532-204"><sup>2</sup>Properties of complex types are flattened out before being sent to the store, so they become comparable (as long as all their properties are comparable).</span></span> <span data-ttu-id="70532-205">Viz také <sup>4.</sup></span><span class="sxs-lookup"><span data-stu-id="70532-205">Also see <sup>4.</sup></span></span>  
  
 <span data-ttu-id="70532-206"><sup>3</sup>Entity Framework runtime zjistí nepodporované případ a vyvolá smysluplný výjimky bez zapojení zprostředkovatele nebo úložiště.</span><span class="sxs-lookup"><span data-stu-id="70532-206"><sup>3</sup>The Entity Framework runtime detects the unsupported case and throws a meaningful exception without engaging the provider/store.</span></span>  
  
 <span data-ttu-id="70532-207"><sup>4</sup>je proveden pokus o porovnat všechny vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="70532-207"><sup>4</sup>An attempt is made to compare all properties.</span></span> <span data-ttu-id="70532-208">Pokud je vlastnost, která není porovnatelný z hlediska typu, jako je text, ntext nebo image, může být vyvolána výjimka serveru.</span><span class="sxs-lookup"><span data-stu-id="70532-208">If there is a property that is of a non-comparable type, such as text, ntext, or image, a server exception might be thrown.</span></span>  
  
 <span data-ttu-id="70532-209"><sup>5</sup>všechny jednotlivé elementy odkazy jsou porovnávány (to zahrnuje název sady entit a všechny vlastnosti klíče typu entity).</span><span class="sxs-lookup"><span data-stu-id="70532-209"><sup>5</sup>All individual elements of the references are compared (this includes the entity set name and all the key properties of the entity type).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70532-210">Viz také</span><span class="sxs-lookup"><span data-stu-id="70532-210">See Also</span></span>  
 [<span data-ttu-id="70532-211">Přehled Entity SQL</span><span class="sxs-lookup"><span data-stu-id="70532-211">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
