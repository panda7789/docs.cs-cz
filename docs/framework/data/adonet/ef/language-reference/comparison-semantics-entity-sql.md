---
title: Porovnání sémantiky (entita SQL)
ms.date: 03/30/2017
ms.assetid: b36ce28a-2fe4-4236-b782-e5f7c054deae
ms.openlocfilehash: 57d81d4b581df76a4382ad5e1d72fe8250b10d43
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150451"
---
# <a name="comparison-semantics-entity-sql"></a><span data-ttu-id="0dfdb-102">Porovnání sémantiky (entita SQL)</span><span class="sxs-lookup"><span data-stu-id="0dfdb-102">Comparison Semantics (Entity SQL)</span></span>
<span data-ttu-id="0dfdb-103">Provedení některého z [!INCLUDE[esql](../../../../../../includes/esql-md.md)] následujících operátorů zahrnuje porovnání instance typu:</span><span class="sxs-lookup"><span data-stu-id="0dfdb-103">Performing any of the following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operators involves comparison of type instances:</span></span>  
  
## <a name="explicit-comparison"></a><span data-ttu-id="0dfdb-104">Explicitní porovnání</span><span class="sxs-lookup"><span data-stu-id="0dfdb-104">Explicit comparison</span></span>  
 <span data-ttu-id="0dfdb-105">Operace rovnosti:</span><span class="sxs-lookup"><span data-stu-id="0dfdb-105">Equality operations:</span></span>  
  
- =  
  
- <span data-ttu-id="0dfdb-106">!=</span><span class="sxs-lookup"><span data-stu-id="0dfdb-106">!=</span></span>  
  
 <span data-ttu-id="0dfdb-107">Objednávání operací:</span><span class="sxs-lookup"><span data-stu-id="0dfdb-107">Ordering operations:</span></span>  
  
- <  
  
- \<=  
  
- \>  
  
- \>=  
  
 <span data-ttu-id="0dfdb-108">Operace s nulovou hodnotou:</span><span class="sxs-lookup"><span data-stu-id="0dfdb-108">Nullability operations:</span></span>  
  
- <span data-ttu-id="0dfdb-109">JE NULL</span><span class="sxs-lookup"><span data-stu-id="0dfdb-109">IS NULL</span></span>  
  
- <span data-ttu-id="0dfdb-110">NENÍ NULL</span><span class="sxs-lookup"><span data-stu-id="0dfdb-110">IS NOT NULL</span></span>  
  
## <a name="explicit-distinction"></a><span data-ttu-id="0dfdb-111">Explicitní rozlišení</span><span class="sxs-lookup"><span data-stu-id="0dfdb-111">Explicit distinction</span></span>  
 <span data-ttu-id="0dfdb-112">Rozlišení rovnosti:</span><span class="sxs-lookup"><span data-stu-id="0dfdb-112">Equality distinction:</span></span>  
  
- <span data-ttu-id="0dfdb-113">DISTINCT</span><span class="sxs-lookup"><span data-stu-id="0dfdb-113">DISTINCT</span></span>  
  
- <span data-ttu-id="0dfdb-114">GROUP BY</span><span class="sxs-lookup"><span data-stu-id="0dfdb-114">GROUP BY</span></span>  
  
 <span data-ttu-id="0dfdb-115">Rozlišování objednávek:</span><span class="sxs-lookup"><span data-stu-id="0dfdb-115">Ordering distinction:</span></span>  
  
- <span data-ttu-id="0dfdb-116">ORDER BY</span><span class="sxs-lookup"><span data-stu-id="0dfdb-116">ORDER BY</span></span>  
  
## <a name="implicit-distinction"></a><span data-ttu-id="0dfdb-117">Implicitní rozlišení</span><span class="sxs-lookup"><span data-stu-id="0dfdb-117">Implicit distinction</span></span>  
 <span data-ttu-id="0dfdb-118">Nastavení operací a predikátů (rovnost):</span><span class="sxs-lookup"><span data-stu-id="0dfdb-118">Set operations and predicates (equality):</span></span>  
  
- <span data-ttu-id="0dfdb-119">UNION</span><span class="sxs-lookup"><span data-stu-id="0dfdb-119">UNION</span></span>  
  
- <span data-ttu-id="0dfdb-120">INTERSECT</span><span class="sxs-lookup"><span data-stu-id="0dfdb-120">INTERSECT</span></span>  
  
- <span data-ttu-id="0dfdb-121">EXCEPT</span><span class="sxs-lookup"><span data-stu-id="0dfdb-121">EXCEPT</span></span>  
  
- <span data-ttu-id="0dfdb-122">SET</span><span class="sxs-lookup"><span data-stu-id="0dfdb-122">SET</span></span>  
  
- <span data-ttu-id="0dfdb-123">OVERLAPS</span><span class="sxs-lookup"><span data-stu-id="0dfdb-123">OVERLAPS</span></span>  
  
 <span data-ttu-id="0dfdb-124">Predikáty položek (rovnost):</span><span class="sxs-lookup"><span data-stu-id="0dfdb-124">Item predicates (equality):</span></span>  
  
- <span data-ttu-id="0dfdb-125">IN</span><span class="sxs-lookup"><span data-stu-id="0dfdb-125">IN</span></span>  
  
## <a name="supported-combinations"></a><span data-ttu-id="0dfdb-126">Podporované kombinace</span><span class="sxs-lookup"><span data-stu-id="0dfdb-126">Supported Combinations</span></span>  
 <span data-ttu-id="0dfdb-127">V následující tabulce jsou uvedeny všechny podporované kombinace operátorů porovnání pro každý typ:</span><span class="sxs-lookup"><span data-stu-id="0dfdb-127">The following table shows all the supported combinations of comparison operators for each kind of type:</span></span>  
  
|<span data-ttu-id="0dfdb-128">**Typ**</span><span class="sxs-lookup"><span data-stu-id="0dfdb-128">**Type**</span></span>|**=**<br /><br /> <span data-ttu-id="0dfdb-129">**!=**</span><span class="sxs-lookup"><span data-stu-id="0dfdb-129">**!=**</span></span>|<span data-ttu-id="0dfdb-130">**SKUPINA PODLE**</span><span class="sxs-lookup"><span data-stu-id="0dfdb-130">**GROUP BY**</span></span><br /><br /> <span data-ttu-id="0dfdb-131">**Odlišné**</span><span class="sxs-lookup"><span data-stu-id="0dfdb-131">**DISTINCT**</span></span>|<span data-ttu-id="0dfdb-132">**Unie**</span><span class="sxs-lookup"><span data-stu-id="0dfdb-132">**UNION**</span></span><br /><br /> <span data-ttu-id="0dfdb-133">**INTERSECT**</span><span class="sxs-lookup"><span data-stu-id="0dfdb-133">**INTERSECT**</span></span><br /><br /> <span data-ttu-id="0dfdb-134">**EXCEPT**</span><span class="sxs-lookup"><span data-stu-id="0dfdb-134">**EXCEPT**</span></span><br /><br /> <span data-ttu-id="0dfdb-135">**Nastavit**</span><span class="sxs-lookup"><span data-stu-id="0dfdb-135">**SET**</span></span><br /><br /> <span data-ttu-id="0dfdb-136">**OVERLAPS**</span><span class="sxs-lookup"><span data-stu-id="0dfdb-136">**OVERLAPS**</span></span>|<span data-ttu-id="0dfdb-137">**In**</span><span class="sxs-lookup"><span data-stu-id="0dfdb-137">**IN**</span></span>|<span data-ttu-id="0dfdb-138">**< <=**</span><span class="sxs-lookup"><span data-stu-id="0dfdb-138">**<   <=**</span></span><br /><br /> <span data-ttu-id="0dfdb-139">**> >=**</span><span class="sxs-lookup"><span data-stu-id="0dfdb-139">**>   >=**</span></span>|<span data-ttu-id="0dfdb-140">**ORDER BY**</span><span class="sxs-lookup"><span data-stu-id="0dfdb-140">**ORDER BY**</span></span>|<span data-ttu-id="0dfdb-141">**JE NULL**</span><span class="sxs-lookup"><span data-stu-id="0dfdb-141">**IS NULL**</span></span><br /><br /> <span data-ttu-id="0dfdb-142">**NENÍ NULL**</span><span class="sxs-lookup"><span data-stu-id="0dfdb-142">**IS NOT NULL**</span></span>|  
|-|-|-|-|-|-|-|-|  
|<span data-ttu-id="0dfdb-143">Typ entity</span><span class="sxs-lookup"><span data-stu-id="0dfdb-143">Entity type</span></span>|<span data-ttu-id="0dfdb-144">Ref<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="0dfdb-144">Ref<sup>1</sup></span></span>|<span data-ttu-id="0dfdb-145">Všechny vlastnosti<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="0dfdb-145">All properties<sup>2</sup></span></span>|<span data-ttu-id="0dfdb-146">Všechny vlastnosti<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="0dfdb-146">All properties<sup>2</sup></span></span>|<span data-ttu-id="0dfdb-147">Všechny vlastnosti<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="0dfdb-147">All properties<sup>2</sup></span></span>|<span data-ttu-id="0dfdb-148">Hod<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="0dfdb-148">Throw<sup>3</sup></span></span>|<span data-ttu-id="0dfdb-149">Hod<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="0dfdb-149">Throw<sup>3</sup></span></span>|<span data-ttu-id="0dfdb-150">Ref<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="0dfdb-150">Ref<sup>1</sup></span></span>|  
|<span data-ttu-id="0dfdb-151">Komplexní typ</span><span class="sxs-lookup"><span data-stu-id="0dfdb-151">Complex type</span></span>|<span data-ttu-id="0dfdb-152">Hod<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="0dfdb-152">Throw<sup>3</sup></span></span>|<span data-ttu-id="0dfdb-153">Hod<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="0dfdb-153">Throw<sup>3</sup></span></span>|<span data-ttu-id="0dfdb-154">Hod<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="0dfdb-154">Throw<sup>3</sup></span></span>|<span data-ttu-id="0dfdb-155">Hod<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="0dfdb-155">Throw<sup>3</sup></span></span>|<span data-ttu-id="0dfdb-156">Hod<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="0dfdb-156">Throw<sup>3</sup></span></span>|<span data-ttu-id="0dfdb-157">Hod<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="0dfdb-157">Throw<sup>3</sup></span></span>|<span data-ttu-id="0dfdb-158">Hod<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="0dfdb-158">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="0dfdb-159">Řádek</span><span class="sxs-lookup"><span data-stu-id="0dfdb-159">Row</span></span>|<span data-ttu-id="0dfdb-160">Všechny vlastnosti<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="0dfdb-160">All properties<sup>4</sup></span></span>|<span data-ttu-id="0dfdb-161">Všechny vlastnosti<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="0dfdb-161">All properties<sup>4</sup></span></span>|<span data-ttu-id="0dfdb-162">Všechny vlastnosti<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="0dfdb-162">All properties<sup>4</sup></span></span>|<span data-ttu-id="0dfdb-163">Hod<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="0dfdb-163">Throw<sup>3</sup></span></span>|<span data-ttu-id="0dfdb-164">Hod<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="0dfdb-164">Throw<sup>3</sup></span></span>|<span data-ttu-id="0dfdb-165">Všechny vlastnosti<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="0dfdb-165">All properties<sup>4</sup></span></span>|<span data-ttu-id="0dfdb-166">Hod<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="0dfdb-166">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="0dfdb-167">Primitivní typ</span><span class="sxs-lookup"><span data-stu-id="0dfdb-167">Primitive type</span></span>|<span data-ttu-id="0dfdb-168">Specifické pro poskytovatele</span><span class="sxs-lookup"><span data-stu-id="0dfdb-168">Provider-specific</span></span>|<span data-ttu-id="0dfdb-169">Specifické pro poskytovatele</span><span class="sxs-lookup"><span data-stu-id="0dfdb-169">Provider-specific</span></span>|<span data-ttu-id="0dfdb-170">Specifické pro poskytovatele</span><span class="sxs-lookup"><span data-stu-id="0dfdb-170">Provider-specific</span></span>|<span data-ttu-id="0dfdb-171">Specifické pro poskytovatele</span><span class="sxs-lookup"><span data-stu-id="0dfdb-171">Provider-specific</span></span>|<span data-ttu-id="0dfdb-172">Specifické pro poskytovatele</span><span class="sxs-lookup"><span data-stu-id="0dfdb-172">Provider-specific</span></span>|<span data-ttu-id="0dfdb-173">Specifické pro poskytovatele</span><span class="sxs-lookup"><span data-stu-id="0dfdb-173">Provider-specific</span></span>|<span data-ttu-id="0dfdb-174">Specifické pro poskytovatele</span><span class="sxs-lookup"><span data-stu-id="0dfdb-174">Provider-specific</span></span>|  
|<span data-ttu-id="0dfdb-175">Vícesetový soubor</span><span class="sxs-lookup"><span data-stu-id="0dfdb-175">Multiset</span></span>|<span data-ttu-id="0dfdb-176">Hod<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="0dfdb-176">Throw<sup>3</sup></span></span>|<span data-ttu-id="0dfdb-177">Hod<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="0dfdb-177">Throw<sup>3</sup></span></span>|<span data-ttu-id="0dfdb-178">Hod<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="0dfdb-178">Throw<sup>3</sup></span></span>|<span data-ttu-id="0dfdb-179">Hod<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="0dfdb-179">Throw<sup>3</sup></span></span>|<span data-ttu-id="0dfdb-180">Hod<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="0dfdb-180">Throw<sup>3</sup></span></span>|<span data-ttu-id="0dfdb-181">Hod<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="0dfdb-181">Throw<sup>3</sup></span></span>|<span data-ttu-id="0dfdb-182">Hod<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="0dfdb-182">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="0dfdb-183">Ref</span><span class="sxs-lookup"><span data-stu-id="0dfdb-183">Ref</span></span>|<span data-ttu-id="0dfdb-184">Ano<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="0dfdb-184">Yes<sup>5</sup></span></span>|<span data-ttu-id="0dfdb-185">Ano<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="0dfdb-185">Yes<sup>5</sup></span></span>|<span data-ttu-id="0dfdb-186">Ano<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="0dfdb-186">Yes<sup>5</sup></span></span>|<span data-ttu-id="0dfdb-187">Ano<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="0dfdb-187">Yes<sup>5</sup></span></span>|<span data-ttu-id="0dfdb-188">Throw</span><span class="sxs-lookup"><span data-stu-id="0dfdb-188">Throw</span></span>|<span data-ttu-id="0dfdb-189">Throw</span><span class="sxs-lookup"><span data-stu-id="0dfdb-189">Throw</span></span>|<span data-ttu-id="0dfdb-190">Ano<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="0dfdb-190">Yes<sup>5</sup></span></span>|  
|<span data-ttu-id="0dfdb-191">Přidružení</span><span class="sxs-lookup"><span data-stu-id="0dfdb-191">Association</span></span><br /><br /> <span data-ttu-id="0dfdb-192">type</span><span class="sxs-lookup"><span data-stu-id="0dfdb-192">type</span></span>|<span data-ttu-id="0dfdb-193">Hod<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="0dfdb-193">Throw<sup>3</sup></span></span>|<span data-ttu-id="0dfdb-194">Throw</span><span class="sxs-lookup"><span data-stu-id="0dfdb-194">Throw</span></span>|<span data-ttu-id="0dfdb-195">Throw</span><span class="sxs-lookup"><span data-stu-id="0dfdb-195">Throw</span></span>|<span data-ttu-id="0dfdb-196">Throw</span><span class="sxs-lookup"><span data-stu-id="0dfdb-196">Throw</span></span>|<span data-ttu-id="0dfdb-197">Hod<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="0dfdb-197">Throw<sup>3</sup></span></span>|<span data-ttu-id="0dfdb-198">Hod<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="0dfdb-198">Throw<sup>3</sup></span></span>|<span data-ttu-id="0dfdb-199">Hod<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="0dfdb-199">Throw<sup>3</sup></span></span>|  
  
 <span data-ttu-id="0dfdb-200"><sup>1.</sup> Odkazy na dané instance typu entity jsou implicitně porovnány, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="0dfdb-200"><sup>1</sup>The references of the given entity type instances are implicitly compared, as shown in the following example:</span></span>  
  
```sql  
SELECT p1, p2
FROM AdventureWorksEntities.Product AS p1
     JOIN AdventureWorksEntities.Product AS p2
WHERE p1 != p2 OR p1 IS NULL  
```  
  
 <span data-ttu-id="0dfdb-201">Instanci entity nelze porovnat s explicitním odkazem.</span><span class="sxs-lookup"><span data-stu-id="0dfdb-201">An entity instance cannot be compared to an explicit reference.</span></span> <span data-ttu-id="0dfdb-202">Pokud se o to pokusí, je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="0dfdb-202">If this is attempted, an exception is thrown.</span></span> <span data-ttu-id="0dfdb-203">Například následující dotaz vyvolá výjimku:</span><span class="sxs-lookup"><span data-stu-id="0dfdb-203">For example, the following query will throw an exception:</span></span>  
  
```sql  
SELECT p1, p2
FROM AdventureWorksEntities.Product AS p1
     JOIN AdventureWorksEntities.Product AS p2
WHERE p1 != REF(p2)  
```  
  
 <span data-ttu-id="0dfdb-204"><sup>2.</sup> Vlastnosti komplexních typů jsou před odesláním do obchodu srovnány se slouhány, takže se stanou srovnatelnými (pokud jsou všechny jejich vlastnosti srovnatelné).</span><span class="sxs-lookup"><span data-stu-id="0dfdb-204"><sup>2</sup>Properties of complex types are flattened out before being sent to the store, so they become comparable (as long as all their properties are comparable).</span></span> <span data-ttu-id="0dfdb-205">Viz také <sup>4.</sup></span><span class="sxs-lookup"><span data-stu-id="0dfdb-205">Also see <sup>4.</sup></span></span>  
  
 <span data-ttu-id="0dfdb-206"><sup>3.</sup> Modul runtime Entity Framework detekuje nepodporovaný případ a vyvolá smysluplnou výjimku bez zapojení zprostředkovatele nebo úložiště.</span><span class="sxs-lookup"><span data-stu-id="0dfdb-206"><sup>3</sup>The Entity Framework runtime detects the unsupported case and throws a meaningful exception without engaging the provider/store.</span></span>  
  
 <span data-ttu-id="0dfdb-207"><sup>4.</sup> Je proveden pokus o porovnání všech vlastností.</span><span class="sxs-lookup"><span data-stu-id="0dfdb-207"><sup>4</sup>An attempt is made to compare all properties.</span></span> <span data-ttu-id="0dfdb-208">Pokud je vlastnost, která je nesrovnatelného typu, jako je například text, ntext nebo obrázek, může být vyvolána výjimka serveru.</span><span class="sxs-lookup"><span data-stu-id="0dfdb-208">If there is a property that is of a non-comparable type, such as text, ntext, or image, a server exception might be thrown.</span></span>  
  
 <span data-ttu-id="0dfdb-209"><sup>5.</sup> Porovnávají se všechny jednotlivé prvky odkazů (to zahrnuje název sady entit a všechny klíčové vlastnosti typu entity).</span><span class="sxs-lookup"><span data-stu-id="0dfdb-209"><sup>5</sup>All individual elements of the references are compared (this includes the entity set name and all the key properties of the entity type).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0dfdb-210">Viz také</span><span class="sxs-lookup"><span data-stu-id="0dfdb-210">See also</span></span>

- [<span data-ttu-id="0dfdb-211">Přehled Entity SQL</span><span class="sxs-lookup"><span data-stu-id="0dfdb-211">Entity SQL Overview</span></span>](entity-sql-overview.md)
