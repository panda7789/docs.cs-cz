---
title: Sémantika porovnání (Entity SQL)
ms.date: 03/30/2017
ms.assetid: b36ce28a-2fe4-4236-b782-e5f7c054deae
ms.openlocfilehash: 6b4c4177ebd6c45e00a1ac7774e40a43e0c14a74
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59083332"
---
# <a name="comparison-semantics-entity-sql"></a><span data-ttu-id="e7702-102">Sémantika porovnání (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="e7702-102">Comparison Semantics (Entity SQL)</span></span>
<span data-ttu-id="e7702-103">Provádění kterékoli z následujících [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zahrnuje operátory porovnání instance typu:</span><span class="sxs-lookup"><span data-stu-id="e7702-103">Performing any of the following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operators involves comparison of type instances:</span></span>  
  
## <a name="explicit-comparison"></a><span data-ttu-id="e7702-104">Explicitní porovnání</span><span class="sxs-lookup"><span data-stu-id="e7702-104">Explicit comparison</span></span>  
 <span data-ttu-id="e7702-105">Operace rovnosti:</span><span class="sxs-lookup"><span data-stu-id="e7702-105">Equality operations:</span></span>  
  
-   =  
  
-   <span data-ttu-id="e7702-106">!=</span><span class="sxs-lookup"><span data-stu-id="e7702-106">!=</span></span>  
  
 <span data-ttu-id="e7702-107">Pořadí operací:</span><span class="sxs-lookup"><span data-stu-id="e7702-107">Ordering operations:</span></span>  
  
-   <  
  
-   \<=  
  
-   \>  
  
-   \>=  
  
 <span data-ttu-id="e7702-108">Možnost použití hodnoty Null operace:</span><span class="sxs-lookup"><span data-stu-id="e7702-108">Nullability operations:</span></span>  
  
-   <span data-ttu-id="e7702-109">MÁ HODNOTU NULL.</span><span class="sxs-lookup"><span data-stu-id="e7702-109">IS NULL</span></span>  
  
-   <span data-ttu-id="e7702-110">NENÍ ROVNO HODNOTĚ NULL</span><span class="sxs-lookup"><span data-stu-id="e7702-110">IS NOT NULL</span></span>  
  
## <a name="explicit-distinction"></a><span data-ttu-id="e7702-111">Explicitní rozlišení</span><span class="sxs-lookup"><span data-stu-id="e7702-111">Explicit distinction</span></span>  
 <span data-ttu-id="e7702-112">Rovnost rozdíl:</span><span class="sxs-lookup"><span data-stu-id="e7702-112">Equality distinction:</span></span>  
  
-   <span data-ttu-id="e7702-113">DISTINCT</span><span class="sxs-lookup"><span data-stu-id="e7702-113">DISTINCT</span></span>  
  
-   <span data-ttu-id="e7702-114">GROUP BY</span><span class="sxs-lookup"><span data-stu-id="e7702-114">GROUP BY</span></span>  
  
 <span data-ttu-id="e7702-115">Řazení rozdíl:</span><span class="sxs-lookup"><span data-stu-id="e7702-115">Ordering distinction:</span></span>  
  
-   <span data-ttu-id="e7702-116">ŘADIT PODLE</span><span class="sxs-lookup"><span data-stu-id="e7702-116">ORDER BY</span></span>  
  
## <a name="implicit-distinction"></a><span data-ttu-id="e7702-117">Implicitní rozlišení</span><span class="sxs-lookup"><span data-stu-id="e7702-117">Implicit distinction</span></span>  
 <span data-ttu-id="e7702-118">Operace a predikáty (rovnost) nastavte:</span><span class="sxs-lookup"><span data-stu-id="e7702-118">Set operations and predicates (equality):</span></span>  
  
-   <span data-ttu-id="e7702-119">UNION</span><span class="sxs-lookup"><span data-stu-id="e7702-119">UNION</span></span>  
  
-   <span data-ttu-id="e7702-120">INTERSECT</span><span class="sxs-lookup"><span data-stu-id="e7702-120">INTERSECT</span></span>  
  
-   <span data-ttu-id="e7702-121">EXCEPT</span><span class="sxs-lookup"><span data-stu-id="e7702-121">EXCEPT</span></span>  
  
-   <span data-ttu-id="e7702-122">SET</span><span class="sxs-lookup"><span data-stu-id="e7702-122">SET</span></span>  
  
-   <span data-ttu-id="e7702-123">OVERLAPS</span><span class="sxs-lookup"><span data-stu-id="e7702-123">OVERLAPS</span></span>  
  
 <span data-ttu-id="e7702-124">Predikáty položky (rovnost):</span><span class="sxs-lookup"><span data-stu-id="e7702-124">Item predicates (equality):</span></span>  
  
-   <span data-ttu-id="e7702-125">IN</span><span class="sxs-lookup"><span data-stu-id="e7702-125">IN</span></span>  
  
## <a name="supported-combinations"></a><span data-ttu-id="e7702-126">Podporované kombinace</span><span class="sxs-lookup"><span data-stu-id="e7702-126">Supported Combinations</span></span>  
 <span data-ttu-id="e7702-127">V následující tabulce jsou uvedeny podporované kombinace operátory porovnání pro každý druh typu:</span><span class="sxs-lookup"><span data-stu-id="e7702-127">The following table shows all the supported combinations of comparison operators for each kind of type:</span></span>  
  
|**<span data-ttu-id="e7702-128">Type</span><span class="sxs-lookup"><span data-stu-id="e7702-128">Type</span></span>**|**=**<br /><br /> **<span data-ttu-id="e7702-129">!=</span><span class="sxs-lookup"><span data-stu-id="e7702-129">!=</span></span>**|**<span data-ttu-id="e7702-130">GROUP BY</span><span class="sxs-lookup"><span data-stu-id="e7702-130">GROUP BY</span></span>**<br /><br /> **<span data-ttu-id="e7702-131">DISTINCT</span><span class="sxs-lookup"><span data-stu-id="e7702-131">DISTINCT</span></span>**|**<span data-ttu-id="e7702-132">UNION</span><span class="sxs-lookup"><span data-stu-id="e7702-132">UNION</span></span>**<br /><br /> **<span data-ttu-id="e7702-133">INTERSECT</span><span class="sxs-lookup"><span data-stu-id="e7702-133">INTERSECT</span></span>**<br /><br /> **<span data-ttu-id="e7702-134">EXCEPT</span><span class="sxs-lookup"><span data-stu-id="e7702-134">EXCEPT</span></span>**<br /><br /> **<span data-ttu-id="e7702-135">SET</span><span class="sxs-lookup"><span data-stu-id="e7702-135">SET</span></span>**<br /><br /> **<span data-ttu-id="e7702-136">OVERLAPS</span><span class="sxs-lookup"><span data-stu-id="e7702-136">OVERLAPS</span></span>**|**<span data-ttu-id="e7702-137">IN</span><span class="sxs-lookup"><span data-stu-id="e7702-137">IN</span></span>**|**<span data-ttu-id="e7702-138"><   <=</span><span class="sxs-lookup"><span data-stu-id="e7702-138"><   <=</span></span>**<br /><br /> **<span data-ttu-id="e7702-139">>   >=</span><span class="sxs-lookup"><span data-stu-id="e7702-139">>   >=</span></span>**|**<span data-ttu-id="e7702-140">ŘADIT PODLE</span><span class="sxs-lookup"><span data-stu-id="e7702-140">ORDER BY</span></span>**|**<span data-ttu-id="e7702-141">MÁ HODNOTU NULL.</span><span class="sxs-lookup"><span data-stu-id="e7702-141">IS NULL</span></span>**<br /><br /> **<span data-ttu-id="e7702-142">NENÍ ROVNO HODNOTĚ NULL</span><span class="sxs-lookup"><span data-stu-id="e7702-142">IS NOT NULL</span></span>**|  
|-|-|-|-|-|-|-|-|  
|<span data-ttu-id="e7702-143">Typ entity</span><span class="sxs-lookup"><span data-stu-id="e7702-143">Entity type</span></span>|<span data-ttu-id="e7702-144">REF<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="e7702-144">Ref<sup>1</sup></span></span>|<span data-ttu-id="e7702-145">Všechny vlastnosti<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="e7702-145">All properties<sup>2</sup></span></span>|<span data-ttu-id="e7702-146">Všechny vlastnosti<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="e7702-146">All properties<sup>2</sup></span></span>|<span data-ttu-id="e7702-147">Všechny vlastnosti<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="e7702-147">All properties<sup>2</sup></span></span>|<span data-ttu-id="e7702-148">Vyvolat<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="e7702-148">Throw<sup>3</sup></span></span>|<span data-ttu-id="e7702-149">Vyvolat<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="e7702-149">Throw<sup>3</sup></span></span>|<span data-ttu-id="e7702-150">REF<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="e7702-150">Ref<sup>1</sup></span></span>|  
|<span data-ttu-id="e7702-151">komplexní typ</span><span class="sxs-lookup"><span data-stu-id="e7702-151">Complex type</span></span>|<span data-ttu-id="e7702-152">Vyvolat<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="e7702-152">Throw<sup>3</sup></span></span>|<span data-ttu-id="e7702-153">Vyvolat<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="e7702-153">Throw<sup>3</sup></span></span>|<span data-ttu-id="e7702-154">Vyvolat<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="e7702-154">Throw<sup>3</sup></span></span>|<span data-ttu-id="e7702-155">Vyvolat<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="e7702-155">Throw<sup>3</sup></span></span>|<span data-ttu-id="e7702-156">Vyvolat<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="e7702-156">Throw<sup>3</sup></span></span>|<span data-ttu-id="e7702-157">Vyvolat<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="e7702-157">Throw<sup>3</sup></span></span>|<span data-ttu-id="e7702-158">Vyvolat<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="e7702-158">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="e7702-159">Řádek</span><span class="sxs-lookup"><span data-stu-id="e7702-159">Row</span></span>|<span data-ttu-id="e7702-160">Všechny vlastnosti<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="e7702-160">All properties<sup>4</sup></span></span>|<span data-ttu-id="e7702-161">Všechny vlastnosti<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="e7702-161">All properties<sup>4</sup></span></span>|<span data-ttu-id="e7702-162">Všechny vlastnosti<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="e7702-162">All properties<sup>4</sup></span></span>|<span data-ttu-id="e7702-163">Vyvolat<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="e7702-163">Throw<sup>3</sup></span></span>|<span data-ttu-id="e7702-164">Vyvolat<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="e7702-164">Throw<sup>3</sup></span></span>|<span data-ttu-id="e7702-165">Všechny vlastnosti<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="e7702-165">All properties<sup>4</sup></span></span>|<span data-ttu-id="e7702-166">Vyvolat<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="e7702-166">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="e7702-167">primitivní typ</span><span class="sxs-lookup"><span data-stu-id="e7702-167">Primitive type</span></span>|<span data-ttu-id="e7702-168">Specifické pro zprostředkovatele</span><span class="sxs-lookup"><span data-stu-id="e7702-168">Provider-specific</span></span>|<span data-ttu-id="e7702-169">Specifické pro zprostředkovatele</span><span class="sxs-lookup"><span data-stu-id="e7702-169">Provider-specific</span></span>|<span data-ttu-id="e7702-170">Specifické pro zprostředkovatele</span><span class="sxs-lookup"><span data-stu-id="e7702-170">Provider-specific</span></span>|<span data-ttu-id="e7702-171">Specifické pro zprostředkovatele</span><span class="sxs-lookup"><span data-stu-id="e7702-171">Provider-specific</span></span>|<span data-ttu-id="e7702-172">Specifické pro zprostředkovatele</span><span class="sxs-lookup"><span data-stu-id="e7702-172">Provider-specific</span></span>|<span data-ttu-id="e7702-173">Specifické pro zprostředkovatele</span><span class="sxs-lookup"><span data-stu-id="e7702-173">Provider-specific</span></span>|<span data-ttu-id="e7702-174">Specifické pro zprostředkovatele</span><span class="sxs-lookup"><span data-stu-id="e7702-174">Provider-specific</span></span>|  
|<span data-ttu-id="e7702-175">Multiset</span><span class="sxs-lookup"><span data-stu-id="e7702-175">Multiset</span></span>|<span data-ttu-id="e7702-176">Vyvolat<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="e7702-176">Throw<sup>3</sup></span></span>|<span data-ttu-id="e7702-177">Vyvolat<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="e7702-177">Throw<sup>3</sup></span></span>|<span data-ttu-id="e7702-178">Vyvolat<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="e7702-178">Throw<sup>3</sup></span></span>|<span data-ttu-id="e7702-179">Vyvolat<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="e7702-179">Throw<sup>3</sup></span></span>|<span data-ttu-id="e7702-180">Vyvolat<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="e7702-180">Throw<sup>3</sup></span></span>|<span data-ttu-id="e7702-181">Vyvolat<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="e7702-181">Throw<sup>3</sup></span></span>|<span data-ttu-id="e7702-182">Vyvolat<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="e7702-182">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="e7702-183">REF</span><span class="sxs-lookup"><span data-stu-id="e7702-183">Ref</span></span>|<span data-ttu-id="e7702-184">Ano<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="e7702-184">Yes<sup>5</sup></span></span>|<span data-ttu-id="e7702-185">Ano<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="e7702-185">Yes<sup>5</sup></span></span>|<span data-ttu-id="e7702-186">Ano<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="e7702-186">Yes<sup>5</sup></span></span>|<span data-ttu-id="e7702-187">Ano<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="e7702-187">Yes<sup>5</sup></span></span>|<span data-ttu-id="e7702-188">vyvolání výjimky</span><span class="sxs-lookup"><span data-stu-id="e7702-188">Throw</span></span>|<span data-ttu-id="e7702-189">vyvolání výjimky</span><span class="sxs-lookup"><span data-stu-id="e7702-189">Throw</span></span>|<span data-ttu-id="e7702-190">Ano<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="e7702-190">Yes<sup>5</sup></span></span>|  
|<span data-ttu-id="e7702-191">Přidružení</span><span class="sxs-lookup"><span data-stu-id="e7702-191">Association</span></span><br /><br /> <span data-ttu-id="e7702-192"> – typ</span><span class="sxs-lookup"><span data-stu-id="e7702-192">type</span></span>|<span data-ttu-id="e7702-193">Vyvolat<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="e7702-193">Throw<sup>3</sup></span></span>|<span data-ttu-id="e7702-194">vyvolání výjimky</span><span class="sxs-lookup"><span data-stu-id="e7702-194">Throw</span></span>|<span data-ttu-id="e7702-195">vyvolání výjimky</span><span class="sxs-lookup"><span data-stu-id="e7702-195">Throw</span></span>|<span data-ttu-id="e7702-196">vyvolání výjimky</span><span class="sxs-lookup"><span data-stu-id="e7702-196">Throw</span></span>|<span data-ttu-id="e7702-197">Vyvolat<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="e7702-197">Throw<sup>3</sup></span></span>|<span data-ttu-id="e7702-198">Vyvolat<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="e7702-198">Throw<sup>3</sup></span></span>|<span data-ttu-id="e7702-199">Vyvolat<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="e7702-199">Throw<sup>3</sup></span></span>|  
  
 <span data-ttu-id="e7702-200"><sup>1</sup>odkazy na danou entitu typu instance jsou implicitně porovnání, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="e7702-200"><sup>1</sup>The references of the given entity type instances are implicitly compared, as shown in the following example:</span></span>  
  
```  
SELECT p1, p2   
FROM AdventureWorksEntities.Product AS p1   
     JOIN AdventureWorksEntities.Product AS p2   
WHERE p1 != p2 OR p1 IS NULL  
```  
  
 <span data-ttu-id="e7702-201">Na explicitní odkaz nelze porovnat instanci entity.</span><span class="sxs-lookup"><span data-stu-id="e7702-201">An entity instance cannot be compared to an explicit reference.</span></span> <span data-ttu-id="e7702-202">Pokud se pokus o, je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="e7702-202">If this is attempted, an exception is thrown.</span></span> <span data-ttu-id="e7702-203">Například následující dotaz vyvolá výjimku:</span><span class="sxs-lookup"><span data-stu-id="e7702-203">For example, the following query will throw an exception:</span></span>  
  
```  
SELECT p1, p2   
FROM AdventureWorksEntities.Product AS p1   
     JOIN AdventureWorksEntities.Product AS p2   
WHERE p1 != REF(p2)  
```  
  
 <span data-ttu-id="e7702-204"><sup>2</sup>komplexní typy vlastností se sloučí před odesláním do úložiště, takže budou srovnatelné (za předpokladu, jejich vlastnosti jsou srovnatelné).</span><span class="sxs-lookup"><span data-stu-id="e7702-204"><sup>2</sup>Properties of complex types are flattened out before being sent to the store, so they become comparable (as long as all their properties are comparable).</span></span> <span data-ttu-id="e7702-205">Viz také <sup>4.</sup></span><span class="sxs-lookup"><span data-stu-id="e7702-205">Also see <sup>4.</sup></span></span>  
  
 <span data-ttu-id="e7702-206"><sup>3</sup>modul runtime rozhraní Entity Framework detekuje nepodporované případ a vyvolá výjimky na smysluplný bez zapojení zprostředkovatele nebo úložiště.</span><span class="sxs-lookup"><span data-stu-id="e7702-206"><sup>3</sup>The Entity Framework runtime detects the unsupported case and throws a meaningful exception without engaging the provider/store.</span></span>  
  
 <span data-ttu-id="e7702-207"><sup>4</sup>je proveden pokus o porovnání všech vlastností.</span><span class="sxs-lookup"><span data-stu-id="e7702-207"><sup>4</sup>An attempt is made to compare all properties.</span></span> <span data-ttu-id="e7702-208">Pokud je vlastnost, která není porovnatelný z hlediska typu, jako je například text, ntext nebo image, může být vyvolána výjimka serveru.</span><span class="sxs-lookup"><span data-stu-id="e7702-208">If there is a property that is of a non-comparable type, such as text, ntext, or image, a server exception might be thrown.</span></span>  
  
 <span data-ttu-id="e7702-209"><sup>5</sup>z odkazů na všechny jednotlivé prvky jsou porovnány (to zahrnuje název sady entit a všechny vlastnosti klíče typu entity).</span><span class="sxs-lookup"><span data-stu-id="e7702-209"><sup>5</sup>All individual elements of the references are compared (this includes the entity set name and all the key properties of the entity type).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7702-210">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e7702-210">See also</span></span>

- [<span data-ttu-id="e7702-211">Přehled Entity SQL</span><span class="sxs-lookup"><span data-stu-id="e7702-211">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
