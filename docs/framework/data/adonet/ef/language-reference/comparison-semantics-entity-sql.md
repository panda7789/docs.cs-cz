---
title: Sémantika porovnání (Entity SQL)
ms.date: 03/30/2017
ms.assetid: b36ce28a-2fe4-4236-b782-e5f7c054deae
ms.openlocfilehash: 2ca91861d4830321168e96fb200c4889dc33b04b
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64631726"
---
# <a name="comparison-semantics-entity-sql"></a><span data-ttu-id="2ad7e-102">Sémantika porovnání (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="2ad7e-102">Comparison Semantics (Entity SQL)</span></span>
<span data-ttu-id="2ad7e-103">Provádění kterékoli z následujících [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zahrnuje operátory porovnání instance typu:</span><span class="sxs-lookup"><span data-stu-id="2ad7e-103">Performing any of the following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operators involves comparison of type instances:</span></span>  
  
## <a name="explicit-comparison"></a><span data-ttu-id="2ad7e-104">Explicitní porovnání</span><span class="sxs-lookup"><span data-stu-id="2ad7e-104">Explicit comparison</span></span>  
 <span data-ttu-id="2ad7e-105">Operace rovnosti:</span><span class="sxs-lookup"><span data-stu-id="2ad7e-105">Equality operations:</span></span>  
  
- =  
  
- <span data-ttu-id="2ad7e-106">!=</span><span class="sxs-lookup"><span data-stu-id="2ad7e-106">!=</span></span>  
  
 <span data-ttu-id="2ad7e-107">Pořadí operací:</span><span class="sxs-lookup"><span data-stu-id="2ad7e-107">Ordering operations:</span></span>  
  
- <  
  
- \<=  
  
- \>  
  
- \>=  
  
 <span data-ttu-id="2ad7e-108">Možnost použití hodnoty Null operace:</span><span class="sxs-lookup"><span data-stu-id="2ad7e-108">Nullability operations:</span></span>  
  
- <span data-ttu-id="2ad7e-109">MÁ HODNOTU NULL.</span><span class="sxs-lookup"><span data-stu-id="2ad7e-109">IS NULL</span></span>  
  
- <span data-ttu-id="2ad7e-110">NENÍ ROVNO HODNOTĚ NULL</span><span class="sxs-lookup"><span data-stu-id="2ad7e-110">IS NOT NULL</span></span>  
  
## <a name="explicit-distinction"></a><span data-ttu-id="2ad7e-111">Explicitní rozlišení</span><span class="sxs-lookup"><span data-stu-id="2ad7e-111">Explicit distinction</span></span>  
 <span data-ttu-id="2ad7e-112">Rovnost rozdíl:</span><span class="sxs-lookup"><span data-stu-id="2ad7e-112">Equality distinction:</span></span>  
  
- <span data-ttu-id="2ad7e-113">DISTINCT</span><span class="sxs-lookup"><span data-stu-id="2ad7e-113">DISTINCT</span></span>  
  
- <span data-ttu-id="2ad7e-114">GROUP BY</span><span class="sxs-lookup"><span data-stu-id="2ad7e-114">GROUP BY</span></span>  
  
 <span data-ttu-id="2ad7e-115">Řazení rozdíl:</span><span class="sxs-lookup"><span data-stu-id="2ad7e-115">Ordering distinction:</span></span>  
  
- <span data-ttu-id="2ad7e-116">ŘADIT PODLE</span><span class="sxs-lookup"><span data-stu-id="2ad7e-116">ORDER BY</span></span>  
  
## <a name="implicit-distinction"></a><span data-ttu-id="2ad7e-117">Implicitní rozlišení</span><span class="sxs-lookup"><span data-stu-id="2ad7e-117">Implicit distinction</span></span>  
 <span data-ttu-id="2ad7e-118">Operace a predikáty (rovnost) nastavte:</span><span class="sxs-lookup"><span data-stu-id="2ad7e-118">Set operations and predicates (equality):</span></span>  
  
- <span data-ttu-id="2ad7e-119">UNION</span><span class="sxs-lookup"><span data-stu-id="2ad7e-119">UNION</span></span>  
  
- <span data-ttu-id="2ad7e-120">INTERSECT</span><span class="sxs-lookup"><span data-stu-id="2ad7e-120">INTERSECT</span></span>  
  
- <span data-ttu-id="2ad7e-121">EXCEPT</span><span class="sxs-lookup"><span data-stu-id="2ad7e-121">EXCEPT</span></span>  
  
- <span data-ttu-id="2ad7e-122">SET</span><span class="sxs-lookup"><span data-stu-id="2ad7e-122">SET</span></span>  
  
- <span data-ttu-id="2ad7e-123">OVERLAPS</span><span class="sxs-lookup"><span data-stu-id="2ad7e-123">OVERLAPS</span></span>  
  
 <span data-ttu-id="2ad7e-124">Predikáty položky (rovnost):</span><span class="sxs-lookup"><span data-stu-id="2ad7e-124">Item predicates (equality):</span></span>  
  
- <span data-ttu-id="2ad7e-125">IN</span><span class="sxs-lookup"><span data-stu-id="2ad7e-125">IN</span></span>  
  
## <a name="supported-combinations"></a><span data-ttu-id="2ad7e-126">Podporované kombinace</span><span class="sxs-lookup"><span data-stu-id="2ad7e-126">Supported Combinations</span></span>  
 <span data-ttu-id="2ad7e-127">V následující tabulce jsou uvedeny podporované kombinace operátory porovnání pro každý druh typu:</span><span class="sxs-lookup"><span data-stu-id="2ad7e-127">The following table shows all the supported combinations of comparison operators for each kind of type:</span></span>  
  
|<span data-ttu-id="2ad7e-128">**Typ**</span><span class="sxs-lookup"><span data-stu-id="2ad7e-128">**Type**</span></span>|**=**<br /><br /> <span data-ttu-id="2ad7e-129">**\!=**</span><span class="sxs-lookup"><span data-stu-id="2ad7e-129">**!=**</span></span>|<span data-ttu-id="2ad7e-130">**GROUP BY**</span><span class="sxs-lookup"><span data-stu-id="2ad7e-130">**GROUP BY**</span></span><br /><br /> <span data-ttu-id="2ad7e-131">**DISTINCT**</span><span class="sxs-lookup"><span data-stu-id="2ad7e-131">**DISTINCT**</span></span>|<span data-ttu-id="2ad7e-132">**UNION**</span><span class="sxs-lookup"><span data-stu-id="2ad7e-132">**UNION**</span></span><br /><br /> <span data-ttu-id="2ad7e-133">**INTERSECT**</span><span class="sxs-lookup"><span data-stu-id="2ad7e-133">**INTERSECT**</span></span><br /><br /> <span data-ttu-id="2ad7e-134">**EXCEPT**</span><span class="sxs-lookup"><span data-stu-id="2ad7e-134">**EXCEPT**</span></span><br /><br /> <span data-ttu-id="2ad7e-135">**SET**</span><span class="sxs-lookup"><span data-stu-id="2ad7e-135">**SET**</span></span><br /><br /> <span data-ttu-id="2ad7e-136">**OVERLAPS**</span><span class="sxs-lookup"><span data-stu-id="2ad7e-136">**OVERLAPS**</span></span>|<span data-ttu-id="2ad7e-137">**IN**</span><span class="sxs-lookup"><span data-stu-id="2ad7e-137">**IN**</span></span>|<span data-ttu-id="2ad7e-138">**<   <=**</span><span class="sxs-lookup"><span data-stu-id="2ad7e-138">**<   <=**</span></span><br /><br /> <span data-ttu-id="2ad7e-139">**>   >=**</span><span class="sxs-lookup"><span data-stu-id="2ad7e-139">**>   >=**</span></span>|<span data-ttu-id="2ad7e-140">**ORDER BY**</span><span class="sxs-lookup"><span data-stu-id="2ad7e-140">**ORDER BY**</span></span>|<span data-ttu-id="2ad7e-141">**IS NULL**</span><span class="sxs-lookup"><span data-stu-id="2ad7e-141">**IS NULL**</span></span><br /><br /> <span data-ttu-id="2ad7e-142">**NENÍ ROVNO HODNOTĚ NULL**</span><span class="sxs-lookup"><span data-stu-id="2ad7e-142">**IS NOT NULL**</span></span>|  
|-|-|-|-|-|-|-|-|  
|<span data-ttu-id="2ad7e-143">Typ entity</span><span class="sxs-lookup"><span data-stu-id="2ad7e-143">Entity type</span></span>|<span data-ttu-id="2ad7e-144">REF<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="2ad7e-144">Ref<sup>1</sup></span></span>|<span data-ttu-id="2ad7e-145">Všechny vlastnosti<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="2ad7e-145">All properties<sup>2</sup></span></span>|<span data-ttu-id="2ad7e-146">Všechny vlastnosti<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="2ad7e-146">All properties<sup>2</sup></span></span>|<span data-ttu-id="2ad7e-147">Všechny vlastnosti<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="2ad7e-147">All properties<sup>2</sup></span></span>|<span data-ttu-id="2ad7e-148">Vyvolat<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="2ad7e-148">Throw<sup>3</sup></span></span>|<span data-ttu-id="2ad7e-149">Vyvolat<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="2ad7e-149">Throw<sup>3</sup></span></span>|<span data-ttu-id="2ad7e-150">REF<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="2ad7e-150">Ref<sup>1</sup></span></span>|  
|<span data-ttu-id="2ad7e-151">komplexní typ</span><span class="sxs-lookup"><span data-stu-id="2ad7e-151">Complex type</span></span>|<span data-ttu-id="2ad7e-152">Vyvolat<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="2ad7e-152">Throw<sup>3</sup></span></span>|<span data-ttu-id="2ad7e-153">Vyvolat<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="2ad7e-153">Throw<sup>3</sup></span></span>|<span data-ttu-id="2ad7e-154">Vyvolat<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="2ad7e-154">Throw<sup>3</sup></span></span>|<span data-ttu-id="2ad7e-155">Vyvolat<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="2ad7e-155">Throw<sup>3</sup></span></span>|<span data-ttu-id="2ad7e-156">Vyvolat<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="2ad7e-156">Throw<sup>3</sup></span></span>|<span data-ttu-id="2ad7e-157">Vyvolat<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="2ad7e-157">Throw<sup>3</sup></span></span>|<span data-ttu-id="2ad7e-158">Vyvolat<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="2ad7e-158">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="2ad7e-159">Řádek</span><span class="sxs-lookup"><span data-stu-id="2ad7e-159">Row</span></span>|<span data-ttu-id="2ad7e-160">Všechny vlastnosti<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="2ad7e-160">All properties<sup>4</sup></span></span>|<span data-ttu-id="2ad7e-161">Všechny vlastnosti<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="2ad7e-161">All properties<sup>4</sup></span></span>|<span data-ttu-id="2ad7e-162">Všechny vlastnosti<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="2ad7e-162">All properties<sup>4</sup></span></span>|<span data-ttu-id="2ad7e-163">Vyvolat<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="2ad7e-163">Throw<sup>3</sup></span></span>|<span data-ttu-id="2ad7e-164">Vyvolat<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="2ad7e-164">Throw<sup>3</sup></span></span>|<span data-ttu-id="2ad7e-165">Všechny vlastnosti<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="2ad7e-165">All properties<sup>4</sup></span></span>|<span data-ttu-id="2ad7e-166">Vyvolat<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="2ad7e-166">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="2ad7e-167">primitivní typ</span><span class="sxs-lookup"><span data-stu-id="2ad7e-167">Primitive type</span></span>|<span data-ttu-id="2ad7e-168">Specifické pro zprostředkovatele</span><span class="sxs-lookup"><span data-stu-id="2ad7e-168">Provider-specific</span></span>|<span data-ttu-id="2ad7e-169">Specifické pro zprostředkovatele</span><span class="sxs-lookup"><span data-stu-id="2ad7e-169">Provider-specific</span></span>|<span data-ttu-id="2ad7e-170">Specifické pro zprostředkovatele</span><span class="sxs-lookup"><span data-stu-id="2ad7e-170">Provider-specific</span></span>|<span data-ttu-id="2ad7e-171">Specifické pro zprostředkovatele</span><span class="sxs-lookup"><span data-stu-id="2ad7e-171">Provider-specific</span></span>|<span data-ttu-id="2ad7e-172">Specifické pro zprostředkovatele</span><span class="sxs-lookup"><span data-stu-id="2ad7e-172">Provider-specific</span></span>|<span data-ttu-id="2ad7e-173">Specifické pro zprostředkovatele</span><span class="sxs-lookup"><span data-stu-id="2ad7e-173">Provider-specific</span></span>|<span data-ttu-id="2ad7e-174">Specifické pro zprostředkovatele</span><span class="sxs-lookup"><span data-stu-id="2ad7e-174">Provider-specific</span></span>|  
|<span data-ttu-id="2ad7e-175">Multiset</span><span class="sxs-lookup"><span data-stu-id="2ad7e-175">Multiset</span></span>|<span data-ttu-id="2ad7e-176">Vyvolat<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="2ad7e-176">Throw<sup>3</sup></span></span>|<span data-ttu-id="2ad7e-177">Vyvolat<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="2ad7e-177">Throw<sup>3</sup></span></span>|<span data-ttu-id="2ad7e-178">Vyvolat<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="2ad7e-178">Throw<sup>3</sup></span></span>|<span data-ttu-id="2ad7e-179">Vyvolat<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="2ad7e-179">Throw<sup>3</sup></span></span>|<span data-ttu-id="2ad7e-180">Vyvolat<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="2ad7e-180">Throw<sup>3</sup></span></span>|<span data-ttu-id="2ad7e-181">Vyvolat<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="2ad7e-181">Throw<sup>3</sup></span></span>|<span data-ttu-id="2ad7e-182">Vyvolat<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="2ad7e-182">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="2ad7e-183">REF</span><span class="sxs-lookup"><span data-stu-id="2ad7e-183">Ref</span></span>|<span data-ttu-id="2ad7e-184">Ano<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="2ad7e-184">Yes<sup>5</sup></span></span>|<span data-ttu-id="2ad7e-185">Ano<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="2ad7e-185">Yes<sup>5</sup></span></span>|<span data-ttu-id="2ad7e-186">Ano<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="2ad7e-186">Yes<sup>5</sup></span></span>|<span data-ttu-id="2ad7e-187">Ano<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="2ad7e-187">Yes<sup>5</sup></span></span>|<span data-ttu-id="2ad7e-188">vyvolání výjimky</span><span class="sxs-lookup"><span data-stu-id="2ad7e-188">Throw</span></span>|<span data-ttu-id="2ad7e-189">vyvolání výjimky</span><span class="sxs-lookup"><span data-stu-id="2ad7e-189">Throw</span></span>|<span data-ttu-id="2ad7e-190">Ano<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="2ad7e-190">Yes<sup>5</sup></span></span>|  
|<span data-ttu-id="2ad7e-191">Přidružení</span><span class="sxs-lookup"><span data-stu-id="2ad7e-191">Association</span></span><br /><br /> <span data-ttu-id="2ad7e-192"> – typ</span><span class="sxs-lookup"><span data-stu-id="2ad7e-192">type</span></span>|<span data-ttu-id="2ad7e-193">Vyvolat<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="2ad7e-193">Throw<sup>3</sup></span></span>|<span data-ttu-id="2ad7e-194">vyvolání výjimky</span><span class="sxs-lookup"><span data-stu-id="2ad7e-194">Throw</span></span>|<span data-ttu-id="2ad7e-195">vyvolání výjimky</span><span class="sxs-lookup"><span data-stu-id="2ad7e-195">Throw</span></span>|<span data-ttu-id="2ad7e-196">vyvolání výjimky</span><span class="sxs-lookup"><span data-stu-id="2ad7e-196">Throw</span></span>|<span data-ttu-id="2ad7e-197">Vyvolat<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="2ad7e-197">Throw<sup>3</sup></span></span>|<span data-ttu-id="2ad7e-198">Vyvolat<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="2ad7e-198">Throw<sup>3</sup></span></span>|<span data-ttu-id="2ad7e-199">Vyvolat<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="2ad7e-199">Throw<sup>3</sup></span></span>|  
  
 <span data-ttu-id="2ad7e-200"><sup>1</sup>odkazy na danou entitu typu instance jsou implicitně porovnání, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="2ad7e-200"><sup>1</sup>The references of the given entity type instances are implicitly compared, as shown in the following example:</span></span>  
  
```  
SELECT p1, p2   
FROM AdventureWorksEntities.Product AS p1   
     JOIN AdventureWorksEntities.Product AS p2   
WHERE p1 != p2 OR p1 IS NULL  
```  
  
 <span data-ttu-id="2ad7e-201">Na explicitní odkaz nelze porovnat instanci entity.</span><span class="sxs-lookup"><span data-stu-id="2ad7e-201">An entity instance cannot be compared to an explicit reference.</span></span> <span data-ttu-id="2ad7e-202">Pokud se pokus o, je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="2ad7e-202">If this is attempted, an exception is thrown.</span></span> <span data-ttu-id="2ad7e-203">Například následující dotaz vyvolá výjimku:</span><span class="sxs-lookup"><span data-stu-id="2ad7e-203">For example, the following query will throw an exception:</span></span>  
  
```  
SELECT p1, p2   
FROM AdventureWorksEntities.Product AS p1   
     JOIN AdventureWorksEntities.Product AS p2   
WHERE p1 != REF(p2)  
```  
  
 <span data-ttu-id="2ad7e-204"><sup>2</sup>komplexní typy vlastností se sloučí před odesláním do úložiště, takže budou srovnatelné (za předpokladu, jejich vlastnosti jsou srovnatelné).</span><span class="sxs-lookup"><span data-stu-id="2ad7e-204"><sup>2</sup>Properties of complex types are flattened out before being sent to the store, so they become comparable (as long as all their properties are comparable).</span></span> <span data-ttu-id="2ad7e-205">Viz také <sup>4.</sup></span><span class="sxs-lookup"><span data-stu-id="2ad7e-205">Also see <sup>4.</sup></span></span>  
  
 <span data-ttu-id="2ad7e-206"><sup>3</sup>modul runtime rozhraní Entity Framework detekuje nepodporované případ a vyvolá výjimky na smysluplný bez zapojení zprostředkovatele nebo úložiště.</span><span class="sxs-lookup"><span data-stu-id="2ad7e-206"><sup>3</sup>The Entity Framework runtime detects the unsupported case and throws a meaningful exception without engaging the provider/store.</span></span>  
  
 <span data-ttu-id="2ad7e-207"><sup>4</sup>je proveden pokus o porovnání všech vlastností.</span><span class="sxs-lookup"><span data-stu-id="2ad7e-207"><sup>4</sup>An attempt is made to compare all properties.</span></span> <span data-ttu-id="2ad7e-208">Pokud je vlastnost, která není porovnatelný z hlediska typu, jako je například text, ntext nebo image, může být vyvolána výjimka serveru.</span><span class="sxs-lookup"><span data-stu-id="2ad7e-208">If there is a property that is of a non-comparable type, such as text, ntext, or image, a server exception might be thrown.</span></span>  
  
 <span data-ttu-id="2ad7e-209"><sup>5</sup>z odkazů na všechny jednotlivé prvky jsou porovnány (to zahrnuje název sady entit a všechny vlastnosti klíče typu entity).</span><span class="sxs-lookup"><span data-stu-id="2ad7e-209"><sup>5</sup>All individual elements of the references are compared (this includes the entity set name and all the key properties of the entity type).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ad7e-210">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2ad7e-210">See also</span></span>

- [<span data-ttu-id="2ad7e-211">Přehled Entity SQL</span><span class="sxs-lookup"><span data-stu-id="2ad7e-211">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
