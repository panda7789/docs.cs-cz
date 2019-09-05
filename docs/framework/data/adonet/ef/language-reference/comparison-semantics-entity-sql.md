---
title: Sémantika porovnání (Entity SQL)
ms.date: 03/30/2017
ms.assetid: b36ce28a-2fe4-4236-b782-e5f7c054deae
ms.openlocfilehash: da7b8f662d10376abd649e674701b43b7b740a6f
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251184"
---
# <a name="comparison-semantics-entity-sql"></a><span data-ttu-id="4ebda-102">Sémantika porovnání (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="4ebda-102">Comparison Semantics (Entity SQL)</span></span>
<span data-ttu-id="4ebda-103">Provádění kterékoli z následujících [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operátorů zahrnuje porovnání instancí typů:</span><span class="sxs-lookup"><span data-stu-id="4ebda-103">Performing any of the following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operators involves comparison of type instances:</span></span>  
  
## <a name="explicit-comparison"></a><span data-ttu-id="4ebda-104">Explicitní porovnání</span><span class="sxs-lookup"><span data-stu-id="4ebda-104">Explicit comparison</span></span>  
 <span data-ttu-id="4ebda-105">Operace rovnosti:</span><span class="sxs-lookup"><span data-stu-id="4ebda-105">Equality operations:</span></span>  
  
- =  
  
- <span data-ttu-id="4ebda-106">!=</span><span class="sxs-lookup"><span data-stu-id="4ebda-106">!=</span></span>  
  
 <span data-ttu-id="4ebda-107">Operace řazení:</span><span class="sxs-lookup"><span data-stu-id="4ebda-107">Ordering operations:</span></span>  
  
- <  
  
- \<=  
  
- \>  
  
- \>=  
  
 <span data-ttu-id="4ebda-108">Operace s hodnotou null:</span><span class="sxs-lookup"><span data-stu-id="4ebda-108">Nullability operations:</span></span>  
  
- <span data-ttu-id="4ebda-109">MÁ HODNOTU NULL</span><span class="sxs-lookup"><span data-stu-id="4ebda-109">IS NULL</span></span>  
  
- <span data-ttu-id="4ebda-110">NENÍ NULL</span><span class="sxs-lookup"><span data-stu-id="4ebda-110">IS NOT NULL</span></span>  
  
## <a name="explicit-distinction"></a><span data-ttu-id="4ebda-111">Explicitní rozlišení</span><span class="sxs-lookup"><span data-stu-id="4ebda-111">Explicit distinction</span></span>  
 <span data-ttu-id="4ebda-112">Rozlišení rovnosti:</span><span class="sxs-lookup"><span data-stu-id="4ebda-112">Equality distinction:</span></span>  
  
- <span data-ttu-id="4ebda-113">ZNAK</span><span class="sxs-lookup"><span data-stu-id="4ebda-113">DISTINCT</span></span>  
  
- <span data-ttu-id="4ebda-114">GROUP BY</span><span class="sxs-lookup"><span data-stu-id="4ebda-114">GROUP BY</span></span>  
  
 <span data-ttu-id="4ebda-115">Rozlišení řazení:</span><span class="sxs-lookup"><span data-stu-id="4ebda-115">Ordering distinction:</span></span>  
  
- <span data-ttu-id="4ebda-116">ŘADIT PODLE</span><span class="sxs-lookup"><span data-stu-id="4ebda-116">ORDER BY</span></span>  
  
## <a name="implicit-distinction"></a><span data-ttu-id="4ebda-117">Implicitní rozlišení</span><span class="sxs-lookup"><span data-stu-id="4ebda-117">Implicit distinction</span></span>  
 <span data-ttu-id="4ebda-118">Nastavit operace a predikáty (rovnost):</span><span class="sxs-lookup"><span data-stu-id="4ebda-118">Set operations and predicates (equality):</span></span>  
  
- <span data-ttu-id="4ebda-119">UNION</span><span class="sxs-lookup"><span data-stu-id="4ebda-119">UNION</span></span>  
  
- <span data-ttu-id="4ebda-120">INTERSECT</span><span class="sxs-lookup"><span data-stu-id="4ebda-120">INTERSECT</span></span>  
  
- <span data-ttu-id="4ebda-121">EXCEPT</span><span class="sxs-lookup"><span data-stu-id="4ebda-121">EXCEPT</span></span>  
  
- <span data-ttu-id="4ebda-122">SET</span><span class="sxs-lookup"><span data-stu-id="4ebda-122">SET</span></span>  
  
- <span data-ttu-id="4ebda-123">OVERLAPS</span><span class="sxs-lookup"><span data-stu-id="4ebda-123">OVERLAPS</span></span>  
  
 <span data-ttu-id="4ebda-124">Predikáty položky (rovnost):</span><span class="sxs-lookup"><span data-stu-id="4ebda-124">Item predicates (equality):</span></span>  
  
- <span data-ttu-id="4ebda-125">IN</span><span class="sxs-lookup"><span data-stu-id="4ebda-125">IN</span></span>  
  
## <a name="supported-combinations"></a><span data-ttu-id="4ebda-126">Podporované kombinace</span><span class="sxs-lookup"><span data-stu-id="4ebda-126">Supported Combinations</span></span>  
 <span data-ttu-id="4ebda-127">V následující tabulce jsou uvedeny všechny podporované kombinace relačních operátorů pro každý druh typu:</span><span class="sxs-lookup"><span data-stu-id="4ebda-127">The following table shows all the supported combinations of comparison operators for each kind of type:</span></span>  
  
|<span data-ttu-id="4ebda-128">**Typ**</span><span class="sxs-lookup"><span data-stu-id="4ebda-128">**Type**</span></span>|**=**<br /><br /> <span data-ttu-id="4ebda-129">**\!=**</span><span class="sxs-lookup"><span data-stu-id="4ebda-129">**!=**</span></span>|<span data-ttu-id="4ebda-130">**GROUP BY**</span><span class="sxs-lookup"><span data-stu-id="4ebda-130">**GROUP BY**</span></span><br /><br /> <span data-ttu-id="4ebda-131">**ZNAK**</span><span class="sxs-lookup"><span data-stu-id="4ebda-131">**DISTINCT**</span></span>|<span data-ttu-id="4ebda-132">**UNION**</span><span class="sxs-lookup"><span data-stu-id="4ebda-132">**UNION**</span></span><br /><br /> <span data-ttu-id="4ebda-133">**INTERSECT**</span><span class="sxs-lookup"><span data-stu-id="4ebda-133">**INTERSECT**</span></span><br /><br /> <span data-ttu-id="4ebda-134">**EXCEPT**</span><span class="sxs-lookup"><span data-stu-id="4ebda-134">**EXCEPT**</span></span><br /><br /> <span data-ttu-id="4ebda-135">**SET**</span><span class="sxs-lookup"><span data-stu-id="4ebda-135">**SET**</span></span><br /><br /> <span data-ttu-id="4ebda-136">**OVERLAPS**</span><span class="sxs-lookup"><span data-stu-id="4ebda-136">**OVERLAPS**</span></span>|<span data-ttu-id="4ebda-137">**IN**</span><span class="sxs-lookup"><span data-stu-id="4ebda-137">**IN**</span></span>|<span data-ttu-id="4ebda-138">**<   <=**</span><span class="sxs-lookup"><span data-stu-id="4ebda-138">**<   <=**</span></span><br /><br /> <span data-ttu-id="4ebda-139">**>   >=**</span><span class="sxs-lookup"><span data-stu-id="4ebda-139">**>   >=**</span></span>|<span data-ttu-id="4ebda-140">**ORDER BY**</span><span class="sxs-lookup"><span data-stu-id="4ebda-140">**ORDER BY**</span></span>|<span data-ttu-id="4ebda-141">**MÁ HODNOTU NULL**</span><span class="sxs-lookup"><span data-stu-id="4ebda-141">**IS NULL**</span></span><br /><br /> <span data-ttu-id="4ebda-142">**NENÍ NULL**</span><span class="sxs-lookup"><span data-stu-id="4ebda-142">**IS NOT NULL**</span></span>|  
|-|-|-|-|-|-|-|-|  
|<span data-ttu-id="4ebda-143">Typ entity</span><span class="sxs-lookup"><span data-stu-id="4ebda-143">Entity type</span></span>|<span data-ttu-id="4ebda-144">Odkaz<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="4ebda-144">Ref<sup>1</sup></span></span>|<span data-ttu-id="4ebda-145">Všechny vlastnosti<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="4ebda-145">All properties<sup>2</sup></span></span>|<span data-ttu-id="4ebda-146">Všechny vlastnosti<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="4ebda-146">All properties<sup>2</sup></span></span>|<span data-ttu-id="4ebda-147">Všechny vlastnosti<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="4ebda-147">All properties<sup>2</sup></span></span>|<span data-ttu-id="4ebda-148">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="4ebda-148">Throw<sup>3</sup></span></span>|<span data-ttu-id="4ebda-149">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="4ebda-149">Throw<sup>3</sup></span></span>|<span data-ttu-id="4ebda-150">Odkaz<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="4ebda-150">Ref<sup>1</sup></span></span>|  
|<span data-ttu-id="4ebda-151">Komplexní typ</span><span class="sxs-lookup"><span data-stu-id="4ebda-151">Complex type</span></span>|<span data-ttu-id="4ebda-152">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="4ebda-152">Throw<sup>3</sup></span></span>|<span data-ttu-id="4ebda-153">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="4ebda-153">Throw<sup>3</sup></span></span>|<span data-ttu-id="4ebda-154">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="4ebda-154">Throw<sup>3</sup></span></span>|<span data-ttu-id="4ebda-155">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="4ebda-155">Throw<sup>3</sup></span></span>|<span data-ttu-id="4ebda-156">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="4ebda-156">Throw<sup>3</sup></span></span>|<span data-ttu-id="4ebda-157">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="4ebda-157">Throw<sup>3</sup></span></span>|<span data-ttu-id="4ebda-158">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="4ebda-158">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="4ebda-159">Řádek</span><span class="sxs-lookup"><span data-stu-id="4ebda-159">Row</span></span>|<span data-ttu-id="4ebda-160">Všechny vlastnosti<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="4ebda-160">All properties<sup>4</sup></span></span>|<span data-ttu-id="4ebda-161">Všechny vlastnosti<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="4ebda-161">All properties<sup>4</sup></span></span>|<span data-ttu-id="4ebda-162">Všechny vlastnosti<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="4ebda-162">All properties<sup>4</sup></span></span>|<span data-ttu-id="4ebda-163">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="4ebda-163">Throw<sup>3</sup></span></span>|<span data-ttu-id="4ebda-164">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="4ebda-164">Throw<sup>3</sup></span></span>|<span data-ttu-id="4ebda-165">Všechny vlastnosti<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="4ebda-165">All properties<sup>4</sup></span></span>|<span data-ttu-id="4ebda-166">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="4ebda-166">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="4ebda-167">Primitivní typ</span><span class="sxs-lookup"><span data-stu-id="4ebda-167">Primitive type</span></span>|<span data-ttu-id="4ebda-168">Specifické pro poskytovatele</span><span class="sxs-lookup"><span data-stu-id="4ebda-168">Provider-specific</span></span>|<span data-ttu-id="4ebda-169">Specifické pro poskytovatele</span><span class="sxs-lookup"><span data-stu-id="4ebda-169">Provider-specific</span></span>|<span data-ttu-id="4ebda-170">Specifické pro poskytovatele</span><span class="sxs-lookup"><span data-stu-id="4ebda-170">Provider-specific</span></span>|<span data-ttu-id="4ebda-171">Specifické pro poskytovatele</span><span class="sxs-lookup"><span data-stu-id="4ebda-171">Provider-specific</span></span>|<span data-ttu-id="4ebda-172">Specifické pro poskytovatele</span><span class="sxs-lookup"><span data-stu-id="4ebda-172">Provider-specific</span></span>|<span data-ttu-id="4ebda-173">Specifické pro poskytovatele</span><span class="sxs-lookup"><span data-stu-id="4ebda-173">Provider-specific</span></span>|<span data-ttu-id="4ebda-174">Specifické pro poskytovatele</span><span class="sxs-lookup"><span data-stu-id="4ebda-174">Provider-specific</span></span>|  
|<span data-ttu-id="4ebda-175">Multiset</span><span class="sxs-lookup"><span data-stu-id="4ebda-175">Multiset</span></span>|<span data-ttu-id="4ebda-176">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="4ebda-176">Throw<sup>3</sup></span></span>|<span data-ttu-id="4ebda-177">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="4ebda-177">Throw<sup>3</sup></span></span>|<span data-ttu-id="4ebda-178">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="4ebda-178">Throw<sup>3</sup></span></span>|<span data-ttu-id="4ebda-179">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="4ebda-179">Throw<sup>3</sup></span></span>|<span data-ttu-id="4ebda-180">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="4ebda-180">Throw<sup>3</sup></span></span>|<span data-ttu-id="4ebda-181">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="4ebda-181">Throw<sup>3</sup></span></span>|<span data-ttu-id="4ebda-182">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="4ebda-182">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="4ebda-183">Odkazů</span><span class="sxs-lookup"><span data-stu-id="4ebda-183">Ref</span></span>|<span data-ttu-id="4ebda-184">Ano<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="4ebda-184">Yes<sup>5</sup></span></span>|<span data-ttu-id="4ebda-185">Ano<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="4ebda-185">Yes<sup>5</sup></span></span>|<span data-ttu-id="4ebda-186">Ano<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="4ebda-186">Yes<sup>5</sup></span></span>|<span data-ttu-id="4ebda-187">Ano<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="4ebda-187">Yes<sup>5</sup></span></span>|<span data-ttu-id="4ebda-188">Throw</span><span class="sxs-lookup"><span data-stu-id="4ebda-188">Throw</span></span>|<span data-ttu-id="4ebda-189">Throw</span><span class="sxs-lookup"><span data-stu-id="4ebda-189">Throw</span></span>|<span data-ttu-id="4ebda-190">Ano<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="4ebda-190">Yes<sup>5</sup></span></span>|  
|<span data-ttu-id="4ebda-191">Řídí</span><span class="sxs-lookup"><span data-stu-id="4ebda-191">Association</span></span><br /><br /> <span data-ttu-id="4ebda-192">– typ</span><span class="sxs-lookup"><span data-stu-id="4ebda-192">type</span></span>|<span data-ttu-id="4ebda-193">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="4ebda-193">Throw<sup>3</sup></span></span>|<span data-ttu-id="4ebda-194">Throw</span><span class="sxs-lookup"><span data-stu-id="4ebda-194">Throw</span></span>|<span data-ttu-id="4ebda-195">Throw</span><span class="sxs-lookup"><span data-stu-id="4ebda-195">Throw</span></span>|<span data-ttu-id="4ebda-196">Throw</span><span class="sxs-lookup"><span data-stu-id="4ebda-196">Throw</span></span>|<span data-ttu-id="4ebda-197">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="4ebda-197">Throw<sup>3</sup></span></span>|<span data-ttu-id="4ebda-198">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="4ebda-198">Throw<sup>3</sup></span></span>|<span data-ttu-id="4ebda-199">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="4ebda-199">Throw<sup>3</sup></span></span>|  
  
 <span data-ttu-id="4ebda-200"><sup>1</sup> Odkazy na dané instance typů entit jsou implicitně porovnány, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="4ebda-200"><sup>1</sup>The references of the given entity type instances are implicitly compared, as shown in the following example:</span></span>  
  
```  
SELECT p1, p2   
FROM AdventureWorksEntities.Product AS p1   
     JOIN AdventureWorksEntities.Product AS p2   
WHERE p1 != p2 OR p1 IS NULL  
```  
  
 <span data-ttu-id="4ebda-201">Instanci entity nelze porovnat s explicitním odkazem.</span><span class="sxs-lookup"><span data-stu-id="4ebda-201">An entity instance cannot be compared to an explicit reference.</span></span> <span data-ttu-id="4ebda-202">Pokud se to pokusí, je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="4ebda-202">If this is attempted, an exception is thrown.</span></span> <span data-ttu-id="4ebda-203">Například následující dotaz vyvolá výjimku:</span><span class="sxs-lookup"><span data-stu-id="4ebda-203">For example, the following query will throw an exception:</span></span>  
  
```  
SELECT p1, p2   
FROM AdventureWorksEntities.Product AS p1   
     JOIN AdventureWorksEntities.Product AS p2   
WHERE p1 != REF(p2)  
```  
  
 <span data-ttu-id="4ebda-204"><sup>2</sup> . Vlastnosti komplexních typů jsou před odesláním do úložiště shrnuty, takže se stanou srovnatelnými (pokud jsou všechny jejich vlastnosti srovnatelné).</span><span class="sxs-lookup"><span data-stu-id="4ebda-204"><sup>2</sup>Properties of complex types are flattened out before being sent to the store, so they become comparable (as long as all their properties are comparable).</span></span> <span data-ttu-id="4ebda-205">Podívejte se také na <sup>4.</sup></span><span class="sxs-lookup"><span data-stu-id="4ebda-205">Also see <sup>4.</sup></span></span>  
  
 <span data-ttu-id="4ebda-206"><sup>3</sup> . Modul runtime Entity Framework detekuje nepodporovaný případ a vyvolá smysluplnou výjimku bez zásahu poskytovatele nebo úložiště.</span><span class="sxs-lookup"><span data-stu-id="4ebda-206"><sup>3</sup>The Entity Framework runtime detects the unsupported case and throws a meaningful exception without engaging the provider/store.</span></span>  
  
 <span data-ttu-id="4ebda-207"><sup>4</sup> . Byl proveden pokus o porovnání všech vlastností.</span><span class="sxs-lookup"><span data-stu-id="4ebda-207"><sup>4</sup>An attempt is made to compare all properties.</span></span> <span data-ttu-id="4ebda-208">Pokud existuje vlastnost, která má nesrovnatelný typ, jako je například text, ntext nebo Image, může být vyvolána výjimka serveru.</span><span class="sxs-lookup"><span data-stu-id="4ebda-208">If there is a property that is of a non-comparable type, such as text, ntext, or image, a server exception might be thrown.</span></span>  
  
 <span data-ttu-id="4ebda-209"><sup>5</sup> . Všechny jednotlivé prvky odkazů jsou porovnávány (to zahrnuje název sady entit a všechny klíčové vlastnosti typu entity).</span><span class="sxs-lookup"><span data-stu-id="4ebda-209"><sup>5</sup>All individual elements of the references are compared (this includes the entity set name and all the key properties of the entity type).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ebda-210">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4ebda-210">See also</span></span>

- [<span data-ttu-id="4ebda-211">Přehled Entity SQL</span><span class="sxs-lookup"><span data-stu-id="4ebda-211">Entity SQL Overview</span></span>](entity-sql-overview.md)
