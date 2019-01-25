---
title: Sémantika porovnání (Entity SQL)
ms.date: 03/30/2017
ms.assetid: b36ce28a-2fe4-4236-b782-e5f7c054deae
ms.openlocfilehash: 371999df0fb3177ecc90f9b1fa43d457a51bfd7a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54492491"
---
# <a name="comparison-semantics-entity-sql"></a><span data-ttu-id="34b83-102">Sémantika porovnání (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="34b83-102">Comparison Semantics (Entity SQL)</span></span>
<span data-ttu-id="34b83-103">Provádění kterékoli z následujících [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zahrnuje operátory porovnání instance typu:</span><span class="sxs-lookup"><span data-stu-id="34b83-103">Performing any of the following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operators involves comparison of type instances:</span></span>  
  
## <a name="explicit-comparison"></a><span data-ttu-id="34b83-104">Explicitní porovnání</span><span class="sxs-lookup"><span data-stu-id="34b83-104">Explicit comparison</span></span>  
 <span data-ttu-id="34b83-105">Operace rovnosti:</span><span class="sxs-lookup"><span data-stu-id="34b83-105">Equality operations:</span></span>  
  
-   =  
  
-   <span data-ttu-id="34b83-106">!=</span><span class="sxs-lookup"><span data-stu-id="34b83-106">!=</span></span>  
  
 <span data-ttu-id="34b83-107">Pořadí operací:</span><span class="sxs-lookup"><span data-stu-id="34b83-107">Ordering operations:</span></span>  
  
-   <  
  
-   \<=  
  
-   \>  
  
-   \>=  
  
 <span data-ttu-id="34b83-108">Možnost použití hodnoty Null operace:</span><span class="sxs-lookup"><span data-stu-id="34b83-108">Nullability operations:</span></span>  
  
-   <span data-ttu-id="34b83-109">MÁ HODNOTU NULL.</span><span class="sxs-lookup"><span data-stu-id="34b83-109">IS NULL</span></span>  
  
-   <span data-ttu-id="34b83-110">NENÍ ROVNO HODNOTĚ NULL</span><span class="sxs-lookup"><span data-stu-id="34b83-110">IS NOT NULL</span></span>  
  
## <a name="explicit-distinction"></a><span data-ttu-id="34b83-111">Explicitní rozlišení</span><span class="sxs-lookup"><span data-stu-id="34b83-111">Explicit distinction</span></span>  
 <span data-ttu-id="34b83-112">Rovnost rozdíl:</span><span class="sxs-lookup"><span data-stu-id="34b83-112">Equality distinction:</span></span>  
  
-   <span data-ttu-id="34b83-113">DISTINCT</span><span class="sxs-lookup"><span data-stu-id="34b83-113">DISTINCT</span></span>  
  
-   <span data-ttu-id="34b83-114">SESKUPIT PODLE</span><span class="sxs-lookup"><span data-stu-id="34b83-114">GROUP BY</span></span>  
  
 <span data-ttu-id="34b83-115">Řazení rozdíl:</span><span class="sxs-lookup"><span data-stu-id="34b83-115">Ordering distinction:</span></span>  
  
-   <span data-ttu-id="34b83-116">ŘADIT PODLE</span><span class="sxs-lookup"><span data-stu-id="34b83-116">ORDER BY</span></span>  
  
## <a name="implicit-distinction"></a><span data-ttu-id="34b83-117">Implicitní rozlišení</span><span class="sxs-lookup"><span data-stu-id="34b83-117">Implicit distinction</span></span>  
 <span data-ttu-id="34b83-118">Operace a predikáty (rovnost) nastavte:</span><span class="sxs-lookup"><span data-stu-id="34b83-118">Set operations and predicates (equality):</span></span>  
  
-   <span data-ttu-id="34b83-119">UNION</span><span class="sxs-lookup"><span data-stu-id="34b83-119">UNION</span></span>  
  
-   <span data-ttu-id="34b83-120">INTERSECT</span><span class="sxs-lookup"><span data-stu-id="34b83-120">INTERSECT</span></span>  
  
-   <span data-ttu-id="34b83-121">S VÝJIMKOU</span><span class="sxs-lookup"><span data-stu-id="34b83-121">EXCEPT</span></span>  
  
-   <span data-ttu-id="34b83-122">NASTAVIT</span><span class="sxs-lookup"><span data-stu-id="34b83-122">SET</span></span>  
  
-   <span data-ttu-id="34b83-123">PŘEKRYTÍ</span><span class="sxs-lookup"><span data-stu-id="34b83-123">OVERLAPS</span></span>  
  
 <span data-ttu-id="34b83-124">Predikáty položky (rovnost):</span><span class="sxs-lookup"><span data-stu-id="34b83-124">Item predicates (equality):</span></span>  
  
-   <span data-ttu-id="34b83-125">IN</span><span class="sxs-lookup"><span data-stu-id="34b83-125">IN</span></span>  
  
## <a name="supported-combinations"></a><span data-ttu-id="34b83-126">Podporované kombinace</span><span class="sxs-lookup"><span data-stu-id="34b83-126">Supported Combinations</span></span>  
 <span data-ttu-id="34b83-127">V následující tabulce jsou uvedeny podporované kombinace operátory porovnání pro každý druh typu:</span><span class="sxs-lookup"><span data-stu-id="34b83-127">The following table shows all the supported combinations of comparison operators for each kind of type:</span></span>  
  
|<span data-ttu-id="34b83-128">**Typ**</span><span class="sxs-lookup"><span data-stu-id="34b83-128">**Type**</span></span>|**=**<br /><br /> <span data-ttu-id="34b83-129">**\!=**</span><span class="sxs-lookup"><span data-stu-id="34b83-129">**!=**</span></span>|<span data-ttu-id="34b83-130">**GROUP BY**</span><span class="sxs-lookup"><span data-stu-id="34b83-130">**GROUP BY**</span></span><br /><br /> <span data-ttu-id="34b83-131">**DISTINCT**</span><span class="sxs-lookup"><span data-stu-id="34b83-131">**DISTINCT**</span></span>|<span data-ttu-id="34b83-132">**UNION**</span><span class="sxs-lookup"><span data-stu-id="34b83-132">**UNION**</span></span><br /><br /> <span data-ttu-id="34b83-133">**INTERSECT**</span><span class="sxs-lookup"><span data-stu-id="34b83-133">**INTERSECT**</span></span><br /><br /> <span data-ttu-id="34b83-134">**EXCEPT**</span><span class="sxs-lookup"><span data-stu-id="34b83-134">**EXCEPT**</span></span><br /><br /> <span data-ttu-id="34b83-135">**SET**</span><span class="sxs-lookup"><span data-stu-id="34b83-135">**SET**</span></span><br /><br /> <span data-ttu-id="34b83-136">**OVERLAPS**</span><span class="sxs-lookup"><span data-stu-id="34b83-136">**OVERLAPS**</span></span>|<span data-ttu-id="34b83-137">**IN**</span><span class="sxs-lookup"><span data-stu-id="34b83-137">**IN**</span></span>|<span data-ttu-id="34b83-138">**<   <=**</span><span class="sxs-lookup"><span data-stu-id="34b83-138">**<   <=**</span></span><br /><br /> <span data-ttu-id="34b83-139">**>   >=**</span><span class="sxs-lookup"><span data-stu-id="34b83-139">**>   >=**</span></span>|<span data-ttu-id="34b83-140">**ORDER BY**</span><span class="sxs-lookup"><span data-stu-id="34b83-140">**ORDER BY**</span></span>|<span data-ttu-id="34b83-141">**IS NULL**</span><span class="sxs-lookup"><span data-stu-id="34b83-141">**IS NULL**</span></span><br /><br /> <span data-ttu-id="34b83-142">**NENÍ ROVNO HODNOTĚ NULL**</span><span class="sxs-lookup"><span data-stu-id="34b83-142">**IS NOT NULL**</span></span>|  
|-|-|-|-|-|-|-|-|  
|<span data-ttu-id="34b83-143">Typ entity</span><span class="sxs-lookup"><span data-stu-id="34b83-143">Entity type</span></span>|<span data-ttu-id="34b83-144">REF<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="34b83-144">Ref<sup>1</sup></span></span>|<span data-ttu-id="34b83-145">Všechny vlastnosti<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="34b83-145">All properties<sup>2</sup></span></span>|<span data-ttu-id="34b83-146">Všechny vlastnosti<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="34b83-146">All properties<sup>2</sup></span></span>|<span data-ttu-id="34b83-147">Všechny vlastnosti<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="34b83-147">All properties<sup>2</sup></span></span>|<span data-ttu-id="34b83-148">Vyvolat<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="34b83-148">Throw<sup>3</sup></span></span>|<span data-ttu-id="34b83-149">Vyvolat<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="34b83-149">Throw<sup>3</sup></span></span>|<span data-ttu-id="34b83-150">REF<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="34b83-150">Ref<sup>1</sup></span></span>|  
|<span data-ttu-id="34b83-151">komplexní typ</span><span class="sxs-lookup"><span data-stu-id="34b83-151">Complex type</span></span>|<span data-ttu-id="34b83-152">Vyvolat<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="34b83-152">Throw<sup>3</sup></span></span>|<span data-ttu-id="34b83-153">Vyvolat<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="34b83-153">Throw<sup>3</sup></span></span>|<span data-ttu-id="34b83-154">Vyvolat<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="34b83-154">Throw<sup>3</sup></span></span>|<span data-ttu-id="34b83-155">Vyvolat<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="34b83-155">Throw<sup>3</sup></span></span>|<span data-ttu-id="34b83-156">Vyvolat<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="34b83-156">Throw<sup>3</sup></span></span>|<span data-ttu-id="34b83-157">Vyvolat<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="34b83-157">Throw<sup>3</sup></span></span>|<span data-ttu-id="34b83-158">Vyvolat<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="34b83-158">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="34b83-159">Řádek</span><span class="sxs-lookup"><span data-stu-id="34b83-159">Row</span></span>|<span data-ttu-id="34b83-160">Všechny vlastnosti<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="34b83-160">All properties<sup>4</sup></span></span>|<span data-ttu-id="34b83-161">Všechny vlastnosti<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="34b83-161">All properties<sup>4</sup></span></span>|<span data-ttu-id="34b83-162">Všechny vlastnosti<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="34b83-162">All properties<sup>4</sup></span></span>|<span data-ttu-id="34b83-163">Vyvolat<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="34b83-163">Throw<sup>3</sup></span></span>|<span data-ttu-id="34b83-164">Vyvolat<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="34b83-164">Throw<sup>3</sup></span></span>|<span data-ttu-id="34b83-165">Všechny vlastnosti<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="34b83-165">All properties<sup>4</sup></span></span>|<span data-ttu-id="34b83-166">Vyvolat<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="34b83-166">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="34b83-167">primitivní typ</span><span class="sxs-lookup"><span data-stu-id="34b83-167">Primitive type</span></span>|<span data-ttu-id="34b83-168">Specifické pro zprostředkovatele</span><span class="sxs-lookup"><span data-stu-id="34b83-168">Provider-specific</span></span>|<span data-ttu-id="34b83-169">Specifické pro zprostředkovatele</span><span class="sxs-lookup"><span data-stu-id="34b83-169">Provider-specific</span></span>|<span data-ttu-id="34b83-170">Specifické pro zprostředkovatele</span><span class="sxs-lookup"><span data-stu-id="34b83-170">Provider-specific</span></span>|<span data-ttu-id="34b83-171">Specifické pro zprostředkovatele</span><span class="sxs-lookup"><span data-stu-id="34b83-171">Provider-specific</span></span>|<span data-ttu-id="34b83-172">Specifické pro zprostředkovatele</span><span class="sxs-lookup"><span data-stu-id="34b83-172">Provider-specific</span></span>|<span data-ttu-id="34b83-173">Specifické pro zprostředkovatele</span><span class="sxs-lookup"><span data-stu-id="34b83-173">Provider-specific</span></span>|<span data-ttu-id="34b83-174">Specifické pro zprostředkovatele</span><span class="sxs-lookup"><span data-stu-id="34b83-174">Provider-specific</span></span>|  
|<span data-ttu-id="34b83-175">Multiset</span><span class="sxs-lookup"><span data-stu-id="34b83-175">Multiset</span></span>|<span data-ttu-id="34b83-176">Vyvolat<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="34b83-176">Throw<sup>3</sup></span></span>|<span data-ttu-id="34b83-177">Vyvolat<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="34b83-177">Throw<sup>3</sup></span></span>|<span data-ttu-id="34b83-178">Vyvolat<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="34b83-178">Throw<sup>3</sup></span></span>|<span data-ttu-id="34b83-179">Vyvolat<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="34b83-179">Throw<sup>3</sup></span></span>|<span data-ttu-id="34b83-180">Vyvolat<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="34b83-180">Throw<sup>3</sup></span></span>|<span data-ttu-id="34b83-181">Vyvolat<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="34b83-181">Throw<sup>3</sup></span></span>|<span data-ttu-id="34b83-182">Vyvolat<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="34b83-182">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="34b83-183">REF</span><span class="sxs-lookup"><span data-stu-id="34b83-183">Ref</span></span>|<span data-ttu-id="34b83-184">Ano<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="34b83-184">Yes<sup>5</sup></span></span>|<span data-ttu-id="34b83-185">Ano<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="34b83-185">Yes<sup>5</sup></span></span>|<span data-ttu-id="34b83-186">Ano<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="34b83-186">Yes<sup>5</sup></span></span>|<span data-ttu-id="34b83-187">Ano<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="34b83-187">Yes<sup>5</sup></span></span>|<span data-ttu-id="34b83-188">vyvolání výjimky</span><span class="sxs-lookup"><span data-stu-id="34b83-188">Throw</span></span>|<span data-ttu-id="34b83-189">vyvolání výjimky</span><span class="sxs-lookup"><span data-stu-id="34b83-189">Throw</span></span>|<span data-ttu-id="34b83-190">Ano<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="34b83-190">Yes<sup>5</sup></span></span>|  
|<span data-ttu-id="34b83-191">Přidružení</span><span class="sxs-lookup"><span data-stu-id="34b83-191">Association</span></span><br /><br /> <span data-ttu-id="34b83-192">– typ</span><span class="sxs-lookup"><span data-stu-id="34b83-192">type</span></span>|<span data-ttu-id="34b83-193">Vyvolat<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="34b83-193">Throw<sup>3</sup></span></span>|<span data-ttu-id="34b83-194">vyvolání výjimky</span><span class="sxs-lookup"><span data-stu-id="34b83-194">Throw</span></span>|<span data-ttu-id="34b83-195">vyvolání výjimky</span><span class="sxs-lookup"><span data-stu-id="34b83-195">Throw</span></span>|<span data-ttu-id="34b83-196">vyvolání výjimky</span><span class="sxs-lookup"><span data-stu-id="34b83-196">Throw</span></span>|<span data-ttu-id="34b83-197">Vyvolat<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="34b83-197">Throw<sup>3</sup></span></span>|<span data-ttu-id="34b83-198">Vyvolat<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="34b83-198">Throw<sup>3</sup></span></span>|<span data-ttu-id="34b83-199">Vyvolat<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="34b83-199">Throw<sup>3</sup></span></span>|  
  
 <span data-ttu-id="34b83-200"><sup>1</sup>odkazy na danou entitu typu instance jsou implicitně porovnání, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="34b83-200"><sup>1</sup>The references of the given entity type instances are implicitly compared, as shown in the following example:</span></span>  
  
```  
SELECT p1, p2   
FROM AdventureWorksEntities.Product AS p1   
     JOIN AdventureWorksEntities.Product AS p2   
WHERE p1 != p2 OR p1 IS NULL  
```  
  
 <span data-ttu-id="34b83-201">Na explicitní odkaz nelze porovnat instanci entity.</span><span class="sxs-lookup"><span data-stu-id="34b83-201">An entity instance cannot be compared to an explicit reference.</span></span> <span data-ttu-id="34b83-202">Pokud se pokus o, je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="34b83-202">If this is attempted, an exception is thrown.</span></span> <span data-ttu-id="34b83-203">Například následující dotaz vyvolá výjimku:</span><span class="sxs-lookup"><span data-stu-id="34b83-203">For example, the following query will throw an exception:</span></span>  
  
```  
SELECT p1, p2   
FROM AdventureWorksEntities.Product AS p1   
     JOIN AdventureWorksEntities.Product AS p2   
WHERE p1 != REF(p2)  
```  
  
 <span data-ttu-id="34b83-204"><sup>2</sup>komplexní typy vlastností se sloučí před odesláním do úložiště, takže budou srovnatelné (za předpokladu, jejich vlastnosti jsou srovnatelné).</span><span class="sxs-lookup"><span data-stu-id="34b83-204"><sup>2</sup>Properties of complex types are flattened out before being sent to the store, so they become comparable (as long as all their properties are comparable).</span></span> <span data-ttu-id="34b83-205">Viz také <sup>4.</sup></span><span class="sxs-lookup"><span data-stu-id="34b83-205">Also see <sup>4.</sup></span></span>  
  
 <span data-ttu-id="34b83-206"><sup>3</sup>modul runtime rozhraní Entity Framework detekuje nepodporované případ a vyvolá výjimky na smysluplný bez zapojení zprostředkovatele nebo úložiště.</span><span class="sxs-lookup"><span data-stu-id="34b83-206"><sup>3</sup>The Entity Framework runtime detects the unsupported case and throws a meaningful exception without engaging the provider/store.</span></span>  
  
 <span data-ttu-id="34b83-207"><sup>4</sup>je proveden pokus o porovnání všech vlastností.</span><span class="sxs-lookup"><span data-stu-id="34b83-207"><sup>4</sup>An attempt is made to compare all properties.</span></span> <span data-ttu-id="34b83-208">Pokud je vlastnost, která není porovnatelný z hlediska typu, jako je například text, ntext nebo image, může být vyvolána výjimka serveru.</span><span class="sxs-lookup"><span data-stu-id="34b83-208">If there is a property that is of a non-comparable type, such as text, ntext, or image, a server exception might be thrown.</span></span>  
  
 <span data-ttu-id="34b83-209"><sup>5</sup>z odkazů na všechny jednotlivé prvky jsou porovnány (to zahrnuje název sady entit a všechny vlastnosti klíče typu entity).</span><span class="sxs-lookup"><span data-stu-id="34b83-209"><sup>5</sup>All individual elements of the references are compared (this includes the entity set name and all the key properties of the entity type).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34b83-210">Viz také:</span><span class="sxs-lookup"><span data-stu-id="34b83-210">See also</span></span>
- [<span data-ttu-id="34b83-211">Přehled Entity SQL</span><span class="sxs-lookup"><span data-stu-id="34b83-211">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
