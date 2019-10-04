---
title: Sémantika porovnání (Entity SQL)
ms.date: 03/30/2017
ms.assetid: b36ce28a-2fe4-4236-b782-e5f7c054deae
ms.openlocfilehash: 8d7868b0166f0a18824ec25e6cdf639deec665ac
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833934"
---
# <a name="comparison-semantics-entity-sql"></a><span data-ttu-id="df559-102">Sémantika porovnání (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="df559-102">Comparison Semantics (Entity SQL)</span></span>
<span data-ttu-id="df559-103">Provádění kterékoli z následujících operátorů [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zahrnuje porovnání instancí typů:</span><span class="sxs-lookup"><span data-stu-id="df559-103">Performing any of the following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operators involves comparison of type instances:</span></span>  
  
## <a name="explicit-comparison"></a><span data-ttu-id="df559-104">Explicitní porovnání</span><span class="sxs-lookup"><span data-stu-id="df559-104">Explicit comparison</span></span>  
 <span data-ttu-id="df559-105">Operace rovnosti:</span><span class="sxs-lookup"><span data-stu-id="df559-105">Equality operations:</span></span>  
  
- =  
  
- <span data-ttu-id="df559-106">!=</span><span class="sxs-lookup"><span data-stu-id="df559-106">!=</span></span>  
  
 <span data-ttu-id="df559-107">Operace řazení:</span><span class="sxs-lookup"><span data-stu-id="df559-107">Ordering operations:</span></span>  
  
- <  
  
- \<=  
  
- \>  
  
- \>=  
  
 <span data-ttu-id="df559-108">Operace s hodnotou null:</span><span class="sxs-lookup"><span data-stu-id="df559-108">Nullability operations:</span></span>  
  
- <span data-ttu-id="df559-109">MÁ HODNOTU NULL</span><span class="sxs-lookup"><span data-stu-id="df559-109">IS NULL</span></span>  
  
- <span data-ttu-id="df559-110">NENÍ NULL</span><span class="sxs-lookup"><span data-stu-id="df559-110">IS NOT NULL</span></span>  
  
## <a name="explicit-distinction"></a><span data-ttu-id="df559-111">Explicitní rozlišení</span><span class="sxs-lookup"><span data-stu-id="df559-111">Explicit distinction</span></span>  
 <span data-ttu-id="df559-112">Rozlišení rovnosti:</span><span class="sxs-lookup"><span data-stu-id="df559-112">Equality distinction:</span></span>  
  
- <span data-ttu-id="df559-113">ZNAK</span><span class="sxs-lookup"><span data-stu-id="df559-113">DISTINCT</span></span>  
  
- <span data-ttu-id="df559-114">GROUP BY</span><span class="sxs-lookup"><span data-stu-id="df559-114">GROUP BY</span></span>  
  
 <span data-ttu-id="df559-115">Rozlišení řazení:</span><span class="sxs-lookup"><span data-stu-id="df559-115">Ordering distinction:</span></span>  
  
- <span data-ttu-id="df559-116">ŘADIT PODLE</span><span class="sxs-lookup"><span data-stu-id="df559-116">ORDER BY</span></span>  
  
## <a name="implicit-distinction"></a><span data-ttu-id="df559-117">Implicitní rozlišení</span><span class="sxs-lookup"><span data-stu-id="df559-117">Implicit distinction</span></span>  
 <span data-ttu-id="df559-118">Nastavit operace a predikáty (rovnost):</span><span class="sxs-lookup"><span data-stu-id="df559-118">Set operations and predicates (equality):</span></span>  
  
- <span data-ttu-id="df559-119">UNION</span><span class="sxs-lookup"><span data-stu-id="df559-119">UNION</span></span>  
  
- <span data-ttu-id="df559-120">INTERSECT</span><span class="sxs-lookup"><span data-stu-id="df559-120">INTERSECT</span></span>  
  
- <span data-ttu-id="df559-121">EXCEPT</span><span class="sxs-lookup"><span data-stu-id="df559-121">EXCEPT</span></span>  
  
- <span data-ttu-id="df559-122">SET</span><span class="sxs-lookup"><span data-stu-id="df559-122">SET</span></span>  
  
- <span data-ttu-id="df559-123">OVERLAPS</span><span class="sxs-lookup"><span data-stu-id="df559-123">OVERLAPS</span></span>  
  
 <span data-ttu-id="df559-124">Predikáty položky (rovnost):</span><span class="sxs-lookup"><span data-stu-id="df559-124">Item predicates (equality):</span></span>  
  
- <span data-ttu-id="df559-125">IN</span><span class="sxs-lookup"><span data-stu-id="df559-125">IN</span></span>  
  
## <a name="supported-combinations"></a><span data-ttu-id="df559-126">Podporované kombinace</span><span class="sxs-lookup"><span data-stu-id="df559-126">Supported Combinations</span></span>  
 <span data-ttu-id="df559-127">V následující tabulce jsou uvedeny všechny podporované kombinace relačních operátorů pro každý druh typu:</span><span class="sxs-lookup"><span data-stu-id="df559-127">The following table shows all the supported combinations of comparison operators for each kind of type:</span></span>  
  
|<span data-ttu-id="df559-128">**Textový**</span><span class="sxs-lookup"><span data-stu-id="df559-128">**Type**</span></span>|**=**<br /><br /> <span data-ttu-id="df559-129">**!=**</span><span class="sxs-lookup"><span data-stu-id="df559-129">**!=**</span></span>|<span data-ttu-id="df559-130">**GROUP BY**</span><span class="sxs-lookup"><span data-stu-id="df559-130">**GROUP BY**</span></span><br /><br /> <span data-ttu-id="df559-131">**ZNAK**</span><span class="sxs-lookup"><span data-stu-id="df559-131">**DISTINCT**</span></span>|<span data-ttu-id="df559-132">**UNION**</span><span class="sxs-lookup"><span data-stu-id="df559-132">**UNION**</span></span><br /><br /> <span data-ttu-id="df559-133">**INTERSECT**</span><span class="sxs-lookup"><span data-stu-id="df559-133">**INTERSECT**</span></span><br /><br /> <span data-ttu-id="df559-134">**EXCEPT**</span><span class="sxs-lookup"><span data-stu-id="df559-134">**EXCEPT**</span></span><br /><br /> <span data-ttu-id="df559-135">**SET**</span><span class="sxs-lookup"><span data-stu-id="df559-135">**SET**</span></span><br /><br /> <span data-ttu-id="df559-136">**OVERLAPS**</span><span class="sxs-lookup"><span data-stu-id="df559-136">**OVERLAPS**</span></span>|<span data-ttu-id="df559-137">**IN**</span><span class="sxs-lookup"><span data-stu-id="df559-137">**IN**</span></span>|<span data-ttu-id="df559-138">**< < =**</span><span class="sxs-lookup"><span data-stu-id="df559-138">**<   <=**</span></span><br /><br /> <span data-ttu-id="df559-139">**> > =**</span><span class="sxs-lookup"><span data-stu-id="df559-139">**>   >=**</span></span>|<span data-ttu-id="df559-140">**ORDER BY**</span><span class="sxs-lookup"><span data-stu-id="df559-140">**ORDER BY**</span></span>|<span data-ttu-id="df559-141">**MÁ HODNOTU NULL**</span><span class="sxs-lookup"><span data-stu-id="df559-141">**IS NULL**</span></span><br /><br /> <span data-ttu-id="df559-142">**NENÍ NULL**</span><span class="sxs-lookup"><span data-stu-id="df559-142">**IS NOT NULL**</span></span>|  
|-|-|-|-|-|-|-|-|  
|<span data-ttu-id="df559-143">Typ entity</span><span class="sxs-lookup"><span data-stu-id="df559-143">Entity type</span></span>|<span data-ttu-id="df559-144">Odkaz<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="df559-144">Ref<sup>1</sup></span></span>|<span data-ttu-id="df559-145">Všechny vlastnosti<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="df559-145">All properties<sup>2</sup></span></span>|<span data-ttu-id="df559-146">Všechny vlastnosti<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="df559-146">All properties<sup>2</sup></span></span>|<span data-ttu-id="df559-147">Všechny vlastnosti<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="df559-147">All properties<sup>2</sup></span></span>|<span data-ttu-id="df559-148">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="df559-148">Throw<sup>3</sup></span></span>|<span data-ttu-id="df559-149">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="df559-149">Throw<sup>3</sup></span></span>|<span data-ttu-id="df559-150">Odkaz<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="df559-150">Ref<sup>1</sup></span></span>|  
|<span data-ttu-id="df559-151">komplexní typ</span><span class="sxs-lookup"><span data-stu-id="df559-151">Complex type</span></span>|<span data-ttu-id="df559-152">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="df559-152">Throw<sup>3</sup></span></span>|<span data-ttu-id="df559-153">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="df559-153">Throw<sup>3</sup></span></span>|<span data-ttu-id="df559-154">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="df559-154">Throw<sup>3</sup></span></span>|<span data-ttu-id="df559-155">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="df559-155">Throw<sup>3</sup></span></span>|<span data-ttu-id="df559-156">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="df559-156">Throw<sup>3</sup></span></span>|<span data-ttu-id="df559-157">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="df559-157">Throw<sup>3</sup></span></span>|<span data-ttu-id="df559-158">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="df559-158">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="df559-159">řadě</span><span class="sxs-lookup"><span data-stu-id="df559-159">Row</span></span>|<span data-ttu-id="df559-160">Všechny vlastnosti<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="df559-160">All properties<sup>4</sup></span></span>|<span data-ttu-id="df559-161">Všechny vlastnosti<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="df559-161">All properties<sup>4</sup></span></span>|<span data-ttu-id="df559-162">Všechny vlastnosti<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="df559-162">All properties<sup>4</sup></span></span>|<span data-ttu-id="df559-163">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="df559-163">Throw<sup>3</sup></span></span>|<span data-ttu-id="df559-164">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="df559-164">Throw<sup>3</sup></span></span>|<span data-ttu-id="df559-165">Všechny vlastnosti<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="df559-165">All properties<sup>4</sup></span></span>|<span data-ttu-id="df559-166">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="df559-166">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="df559-167">Primitivní typ</span><span class="sxs-lookup"><span data-stu-id="df559-167">Primitive type</span></span>|<span data-ttu-id="df559-168">Specifické pro poskytovatele</span><span class="sxs-lookup"><span data-stu-id="df559-168">Provider-specific</span></span>|<span data-ttu-id="df559-169">Specifické pro poskytovatele</span><span class="sxs-lookup"><span data-stu-id="df559-169">Provider-specific</span></span>|<span data-ttu-id="df559-170">Specifické pro poskytovatele</span><span class="sxs-lookup"><span data-stu-id="df559-170">Provider-specific</span></span>|<span data-ttu-id="df559-171">Specifické pro poskytovatele</span><span class="sxs-lookup"><span data-stu-id="df559-171">Provider-specific</span></span>|<span data-ttu-id="df559-172">Specifické pro poskytovatele</span><span class="sxs-lookup"><span data-stu-id="df559-172">Provider-specific</span></span>|<span data-ttu-id="df559-173">Specifické pro poskytovatele</span><span class="sxs-lookup"><span data-stu-id="df559-173">Provider-specific</span></span>|<span data-ttu-id="df559-174">Specifické pro poskytovatele</span><span class="sxs-lookup"><span data-stu-id="df559-174">Provider-specific</span></span>|  
|<span data-ttu-id="df559-175">Multiset</span><span class="sxs-lookup"><span data-stu-id="df559-175">Multiset</span></span>|<span data-ttu-id="df559-176">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="df559-176">Throw<sup>3</sup></span></span>|<span data-ttu-id="df559-177">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="df559-177">Throw<sup>3</sup></span></span>|<span data-ttu-id="df559-178">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="df559-178">Throw<sup>3</sup></span></span>|<span data-ttu-id="df559-179">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="df559-179">Throw<sup>3</sup></span></span>|<span data-ttu-id="df559-180">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="df559-180">Throw<sup>3</sup></span></span>|<span data-ttu-id="df559-181">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="df559-181">Throw<sup>3</sup></span></span>|<span data-ttu-id="df559-182">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="df559-182">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="df559-183">odkazů</span><span class="sxs-lookup"><span data-stu-id="df559-183">Ref</span></span>|<span data-ttu-id="df559-184">Ano<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="df559-184">Yes<sup>5</sup></span></span>|<span data-ttu-id="df559-185">Ano<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="df559-185">Yes<sup>5</sup></span></span>|<span data-ttu-id="df559-186">Ano<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="df559-186">Yes<sup>5</sup></span></span>|<span data-ttu-id="df559-187">Ano<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="df559-187">Yes<sup>5</sup></span></span>|<span data-ttu-id="df559-188">Throw</span><span class="sxs-lookup"><span data-stu-id="df559-188">Throw</span></span>|<span data-ttu-id="df559-189">Throw</span><span class="sxs-lookup"><span data-stu-id="df559-189">Throw</span></span>|<span data-ttu-id="df559-190">Ano<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="df559-190">Yes<sup>5</sup></span></span>|  
|<span data-ttu-id="df559-191">řídí</span><span class="sxs-lookup"><span data-stu-id="df559-191">Association</span></span><br /><br /> <span data-ttu-id="df559-192">– typ</span><span class="sxs-lookup"><span data-stu-id="df559-192">type</span></span>|<span data-ttu-id="df559-193">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="df559-193">Throw<sup>3</sup></span></span>|<span data-ttu-id="df559-194">Throw</span><span class="sxs-lookup"><span data-stu-id="df559-194">Throw</span></span>|<span data-ttu-id="df559-195">Throw</span><span class="sxs-lookup"><span data-stu-id="df559-195">Throw</span></span>|<span data-ttu-id="df559-196">Throw</span><span class="sxs-lookup"><span data-stu-id="df559-196">Throw</span></span>|<span data-ttu-id="df559-197">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="df559-197">Throw<sup>3</sup></span></span>|<span data-ttu-id="df559-198">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="df559-198">Throw<sup>3</sup></span></span>|<span data-ttu-id="df559-199">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="df559-199">Throw<sup>3</sup></span></span>|  
  
 <span data-ttu-id="df559-200"><sup>1</sup> Odkazy na dané instance typů entit jsou implicitně porovnány, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="df559-200"><sup>1</sup>The references of the given entity type instances are implicitly compared, as shown in the following example:</span></span>  
  
```sql  
SELECT p1, p2   
FROM AdventureWorksEntities.Product AS p1   
     JOIN AdventureWorksEntities.Product AS p2   
WHERE p1 != p2 OR p1 IS NULL  
```  
  
 <span data-ttu-id="df559-201">Instanci entity nelze porovnat s explicitním odkazem.</span><span class="sxs-lookup"><span data-stu-id="df559-201">An entity instance cannot be compared to an explicit reference.</span></span> <span data-ttu-id="df559-202">Pokud se to pokusí, je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="df559-202">If this is attempted, an exception is thrown.</span></span> <span data-ttu-id="df559-203">Například následující dotaz vyvolá výjimku:</span><span class="sxs-lookup"><span data-stu-id="df559-203">For example, the following query will throw an exception:</span></span>  
  
```sql  
SELECT p1, p2   
FROM AdventureWorksEntities.Product AS p1   
     JOIN AdventureWorksEntities.Product AS p2   
WHERE p1 != REF(p2)  
```  
  
 <span data-ttu-id="df559-204"><sup>2</sup> . Vlastnosti komplexních typů jsou před odesláním do úložiště shrnuty, takže se stanou srovnatelnými (pokud jsou všechny jejich vlastnosti srovnatelné).</span><span class="sxs-lookup"><span data-stu-id="df559-204"><sup>2</sup>Properties of complex types are flattened out before being sent to the store, so they become comparable (as long as all their properties are comparable).</span></span> <span data-ttu-id="df559-205">Podívejte se také na <sup>4.</sup></span><span class="sxs-lookup"><span data-stu-id="df559-205">Also see <sup>4.</sup></span></span>  
  
 <span data-ttu-id="df559-206"><sup>3</sup> . Modul runtime Entity Framework detekuje nepodporovaný případ a vyvolá smysluplnou výjimku bez zásahu poskytovatele nebo úložiště.</span><span class="sxs-lookup"><span data-stu-id="df559-206"><sup>3</sup>The Entity Framework runtime detects the unsupported case and throws a meaningful exception without engaging the provider/store.</span></span>  
  
 <span data-ttu-id="df559-207"><sup>4</sup> . Byl proveden pokus o porovnání všech vlastností.</span><span class="sxs-lookup"><span data-stu-id="df559-207"><sup>4</sup>An attempt is made to compare all properties.</span></span> <span data-ttu-id="df559-208">Pokud existuje vlastnost, která má nesrovnatelný typ, jako je například text, ntext nebo Image, může být vyvolána výjimka serveru.</span><span class="sxs-lookup"><span data-stu-id="df559-208">If there is a property that is of a non-comparable type, such as text, ntext, or image, a server exception might be thrown.</span></span>  
  
 <span data-ttu-id="df559-209"><sup>5</sup> . Všechny jednotlivé prvky odkazů jsou porovnávány (to zahrnuje název sady entit a všechny klíčové vlastnosti typu entity).</span><span class="sxs-lookup"><span data-stu-id="df559-209"><sup>5</sup>All individual elements of the references are compared (this includes the entity set name and all the key properties of the entity type).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df559-210">Viz také:</span><span class="sxs-lookup"><span data-stu-id="df559-210">See also</span></span>

- [<span data-ttu-id="df559-211">Přehled Entity SQL</span><span class="sxs-lookup"><span data-stu-id="df559-211">Entity SQL Overview</span></span>](entity-sql-overview.md)
