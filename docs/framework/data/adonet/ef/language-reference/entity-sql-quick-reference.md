---
title: Stručná referenční entity SQL
ms.date: 03/30/2017
ms.assetid: e53dad9e-5e83-426e-abb4-be3e78e3d6dc
ms.openlocfilehash: 0617ce96acaf5a6eafb2658cfe218cc8f4135f6e
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32765851"
---
# <a name="entity-sql-quick-reference"></a><span data-ttu-id="5f8fd-102">Stručná referenční entity SQL</span><span class="sxs-lookup"><span data-stu-id="5f8fd-102">Entity SQL Quick Reference</span></span>
<span data-ttu-id="5f8fd-103">Toto téma obsahuje Stručná referenční příručka pro [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dotazy.</span><span class="sxs-lookup"><span data-stu-id="5f8fd-103">This topic provides a quick reference to [!INCLUDE[esql](../../../../../../includes/esql-md.md)] queries.</span></span> <span data-ttu-id="5f8fd-104">Dotazy v tomto tématu jsou založené na modelu prodeje společnosti AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="5f8fd-104">The queries in this topic are based on the AdventureWorks Sales model.</span></span>  
  
## <a name="literals"></a><span data-ttu-id="5f8fd-105">Literály</span><span class="sxs-lookup"><span data-stu-id="5f8fd-105">Literals</span></span>  
  
### <a name="string"></a><span data-ttu-id="5f8fd-106">String</span><span class="sxs-lookup"><span data-stu-id="5f8fd-106">String</span></span>  
 <span data-ttu-id="5f8fd-107">Existují textové literály znak Unicode a kódování Unicode.</span><span class="sxs-lookup"><span data-stu-id="5f8fd-107">There are Unicode and non-Unicode character string literals.</span></span> <span data-ttu-id="5f8fd-108">Řetězců v kódu Unicode se přidá jako předpona s N. Například `N'hello'`.</span><span class="sxs-lookup"><span data-stu-id="5f8fd-108">Unicode strings are prepended with N. For example, `N'hello'`.</span></span>  
  
 <span data-ttu-id="5f8fd-109">Následuje příklad než Unicode řetězcový literál:</span><span class="sxs-lookup"><span data-stu-id="5f8fd-109">The following is an example of a Non-Unicode string literal:</span></span>  
  
```  
'hello'  
--same as  
"hello"  
```  
  
 <span data-ttu-id="5f8fd-110">Výstup:</span><span class="sxs-lookup"><span data-stu-id="5f8fd-110">Output:</span></span>  
  
|<span data-ttu-id="5f8fd-111">Hodnota</span><span class="sxs-lookup"><span data-stu-id="5f8fd-111">Value</span></span>|  
|-----------|  
|<span data-ttu-id="5f8fd-112">Dobrý den</span><span class="sxs-lookup"><span data-stu-id="5f8fd-112">hello</span></span>|  
  
### <a name="datetime"></a><span data-ttu-id="5f8fd-113">DateTime</span><span class="sxs-lookup"><span data-stu-id="5f8fd-113">DateTime</span></span>  
 <span data-ttu-id="5f8fd-114">V literálech datum a čas datum a čas části jsou povinné.</span><span class="sxs-lookup"><span data-stu-id="5f8fd-114">In DateTime literals, both date and time parts are mandatory.</span></span> <span data-ttu-id="5f8fd-115">Neexistují žádné výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="5f8fd-115">There are no default values.</span></span>  
  
 <span data-ttu-id="5f8fd-116">Příklad:</span><span class="sxs-lookup"><span data-stu-id="5f8fd-116">Example:</span></span>  
  
```  
DATETIME '2006-12-25 01:01:00.000'   
--same as  
DATETIME '2006-12-25 01:01'  
```  
  
 <span data-ttu-id="5f8fd-117">Výstup:</span><span class="sxs-lookup"><span data-stu-id="5f8fd-117">Output:</span></span>  
  
|<span data-ttu-id="5f8fd-118">Hodnota</span><span class="sxs-lookup"><span data-stu-id="5f8fd-118">Value</span></span>|  
|-----------|  
|<span data-ttu-id="5f8fd-119">12/25/2006 1:01:00: 00</span><span class="sxs-lookup"><span data-stu-id="5f8fd-119">12/25/2006 1:01:00 AM</span></span>|  
  
### <a name="integer"></a><span data-ttu-id="5f8fd-120">Integer</span><span class="sxs-lookup"><span data-stu-id="5f8fd-120">Integer</span></span>  
 <span data-ttu-id="5f8fd-121">Můžou být celé číslo literály typu Int32 (123) UInt32 (123U), Int64 (123L) a UInt64 (123UL).</span><span class="sxs-lookup"><span data-stu-id="5f8fd-121">Integer literals can be of type Int32 (123), UInt32 (123U), Int64 (123L), and UInt64 (123UL).</span></span>  
  
 <span data-ttu-id="5f8fd-122">Příklad:</span><span class="sxs-lookup"><span data-stu-id="5f8fd-122">Example:</span></span>  
  
```  
--a collection of integers  
{1, 2, 3}  
```  
  
 <span data-ttu-id="5f8fd-123">Výstup:</span><span class="sxs-lookup"><span data-stu-id="5f8fd-123">Output:</span></span>  
  
|<span data-ttu-id="5f8fd-124">Hodnota</span><span class="sxs-lookup"><span data-stu-id="5f8fd-124">Value</span></span>|  
|-----------|  
|<span data-ttu-id="5f8fd-125">1</span><span class="sxs-lookup"><span data-stu-id="5f8fd-125">1</span></span>|  
|<span data-ttu-id="5f8fd-126">2</span><span class="sxs-lookup"><span data-stu-id="5f8fd-126">2</span></span>|  
|<span data-ttu-id="5f8fd-127">3</span><span class="sxs-lookup"><span data-stu-id="5f8fd-127">3</span></span>|  
  
### <a name="other"></a><span data-ttu-id="5f8fd-128">Ostatní</span><span class="sxs-lookup"><span data-stu-id="5f8fd-128">Other</span></span>  
 <span data-ttu-id="5f8fd-129">Další literály nepodporuje [!INCLUDE[esql](../../../../../../includes/esql-md.md)] jsou identifikátor Guid, binární, typu Float/Double, Decimal, a `null`.</span><span class="sxs-lookup"><span data-stu-id="5f8fd-129">Other literals supported by [!INCLUDE[esql](../../../../../../includes/esql-md.md)] are Guid, Binary, Float/Double, Decimal, and `null`.</span></span> <span data-ttu-id="5f8fd-130">Hodnota Null, literály v [!INCLUDE[esql](../../../../../../includes/esql-md.md)] se považují za kompatibilní s každou další typu v konceptuálním modelu.</span><span class="sxs-lookup"><span data-stu-id="5f8fd-130">Null literals in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] are considered to be compatible with every other type in the conceptual model.</span></span>  
  
## <a name="type-constructors"></a><span data-ttu-id="5f8fd-131">Konstruktory typu</span><span class="sxs-lookup"><span data-stu-id="5f8fd-131">Type Constructors</span></span>  
  
### <a name="row"></a><span data-ttu-id="5f8fd-132">ŘÁDEK</span><span class="sxs-lookup"><span data-stu-id="5f8fd-132">ROW</span></span>  
 <span data-ttu-id="5f8fd-133">[ŘÁDEK](../../../../../../docs/framework/data/adonet/ef/language-reference/row-entity-sql.md) vytvoří anonymní, strukturálně typované (záznamů) hodnotu jako v: `ROW(1 AS myNumber, ‘Name’ AS myName).`</span><span class="sxs-lookup"><span data-stu-id="5f8fd-133">[ROW](../../../../../../docs/framework/data/adonet/ef/language-reference/row-entity-sql.md) constructs an anonymous, structurally-typed (record) value as in: `ROW(1 AS myNumber, ‘Name’ AS myName).`</span></span>  
  
 <span data-ttu-id="5f8fd-134">Příklad:</span><span class="sxs-lookup"><span data-stu-id="5f8fd-134">Example:</span></span>  
  
```  
SELECT VALUE row (product.ProductID as ProductID, product.Name   
    as ProductName) FROM AdventureWorksEntities.Product AS product  
```  
  
 <span data-ttu-id="5f8fd-135">Výstup:</span><span class="sxs-lookup"><span data-stu-id="5f8fd-135">Output:</span></span>  
  
|<span data-ttu-id="5f8fd-136">ProductID</span><span class="sxs-lookup"><span data-stu-id="5f8fd-136">ProductID</span></span>|<span data-ttu-id="5f8fd-137">Název</span><span class="sxs-lookup"><span data-stu-id="5f8fd-137">Name</span></span>|  
|---------------|----------|  
|<span data-ttu-id="5f8fd-138">1</span><span class="sxs-lookup"><span data-stu-id="5f8fd-138">1</span></span>|<span data-ttu-id="5f8fd-139">Upravit soupeření</span><span class="sxs-lookup"><span data-stu-id="5f8fd-139">Adjustable Race</span></span>|  
|<span data-ttu-id="5f8fd-140">879</span><span class="sxs-lookup"><span data-stu-id="5f8fd-140">879</span></span>|<span data-ttu-id="5f8fd-141">Všechny účely kolo úsporný režim</span><span class="sxs-lookup"><span data-stu-id="5f8fd-141">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="5f8fd-142">712</span><span class="sxs-lookup"><span data-stu-id="5f8fd-142">712</span></span>|<span data-ttu-id="5f8fd-143">AWC Logo zakončení</span><span class="sxs-lookup"><span data-stu-id="5f8fd-143">AWC Logo Cap</span></span>|  
|<span data-ttu-id="5f8fd-144">...</span><span class="sxs-lookup"><span data-stu-id="5f8fd-144">...</span></span>|<span data-ttu-id="5f8fd-145">...</span><span class="sxs-lookup"><span data-stu-id="5f8fd-145">...</span></span>|  
  
### <a name="multiset"></a><span data-ttu-id="5f8fd-146">MULTIMNOŽINA</span><span class="sxs-lookup"><span data-stu-id="5f8fd-146">MULTISET</span></span>  
 <span data-ttu-id="5f8fd-147">[MULTIMNOŽINA](../../../../../../docs/framework/data/adonet/ef/language-reference/multiset-entity-sql.md) vytvoří kolekcí, jako například:</span><span class="sxs-lookup"><span data-stu-id="5f8fd-147">[MULTISET](../../../../../../docs/framework/data/adonet/ef/language-reference/multiset-entity-sql.md) constructs collections, such as:</span></span>  
  
 <span data-ttu-id="5f8fd-148">`MULTISET(1,2,2,3)` `--same as`-`{1,2,2,3}.`</span><span class="sxs-lookup"><span data-stu-id="5f8fd-148">`MULTISET(1,2,2,3)` `--same as`-`{1,2,2,3}.`</span></span>  
  
 <span data-ttu-id="5f8fd-149">Příklad:</span><span class="sxs-lookup"><span data-stu-id="5f8fd-149">Example:</span></span>  
  
```  
SELECT VALUE product FROM AdventureWorksEntities.Product AS product WHERE product.ListPrice IN MultiSet (125, 300)  
```  
  
 <span data-ttu-id="5f8fd-150">Výstup:</span><span class="sxs-lookup"><span data-stu-id="5f8fd-150">Output:</span></span>  
  
|<span data-ttu-id="5f8fd-151">ProductID</span><span class="sxs-lookup"><span data-stu-id="5f8fd-151">ProductID</span></span>|<span data-ttu-id="5f8fd-152">Název</span><span class="sxs-lookup"><span data-stu-id="5f8fd-152">Name</span></span>|<span data-ttu-id="5f8fd-153">ProductNumber</span><span class="sxs-lookup"><span data-stu-id="5f8fd-153">ProductNumber</span></span>|<span data-ttu-id="5f8fd-154">…</span><span class="sxs-lookup"><span data-stu-id="5f8fd-154">…</span></span>|  
|---------------|----------|-------------------|-------|  
|<span data-ttu-id="5f8fd-155">842</span><span class="sxs-lookup"><span data-stu-id="5f8fd-155">842</span></span>|<span data-ttu-id="5f8fd-156">Jízdních Panniers, velké</span><span class="sxs-lookup"><span data-stu-id="5f8fd-156">Touring-Panniers, Large</span></span>|<span data-ttu-id="5f8fd-157">PA-T100</span><span class="sxs-lookup"><span data-stu-id="5f8fd-157">PA-T100</span></span>|<span data-ttu-id="5f8fd-158">…</span><span class="sxs-lookup"><span data-stu-id="5f8fd-158">…</span></span>|  
  
### <a name="object"></a><span data-ttu-id="5f8fd-159">Objekt</span><span class="sxs-lookup"><span data-stu-id="5f8fd-159">Object</span></span>  
 <span data-ttu-id="5f8fd-160">[Konstruktor typu s názvem](../../../../../../docs/framework/data/adonet/ef/language-reference/named-type-constructor-entity-sql.md) vytvoří (s názvem) uživatelem definované objekty, například `person("abc", 12)`.</span><span class="sxs-lookup"><span data-stu-id="5f8fd-160">[Named Type Constructor](../../../../../../docs/framework/data/adonet/ef/language-reference/named-type-constructor-entity-sql.md) constructs (named) user-defined objects, such as `person("abc", 12)`.</span></span>  
  
 <span data-ttu-id="5f8fd-161">Příklad:</span><span class="sxs-lookup"><span data-stu-id="5f8fd-161">Example:</span></span>  
  
```  
SELECT VALUE AdventureWorksModel.SalesOrderDetail (o.SalesOrderDetailID, o.CarrierTrackingNumber, o.OrderQty,   
o.ProductID, o.SpecialOfferID, o.UnitPrice, o.UnitPriceDiscount,   
o.rowguid, o.ModifiedDate) FROM AdventureWorksEntities.SalesOrderDetail   
AS o  
```  
  
 <span data-ttu-id="5f8fd-162">Výstup:</span><span class="sxs-lookup"><span data-stu-id="5f8fd-162">Output:</span></span>  
  
|<span data-ttu-id="5f8fd-163">SalesOrderDetailID</span><span class="sxs-lookup"><span data-stu-id="5f8fd-163">SalesOrderDetailID</span></span>|<span data-ttu-id="5f8fd-164">CarrierTrackingNumber</span><span class="sxs-lookup"><span data-stu-id="5f8fd-164">CarrierTrackingNumber</span></span>|<span data-ttu-id="5f8fd-165">OrderQty</span><span class="sxs-lookup"><span data-stu-id="5f8fd-165">OrderQty</span></span>|<span data-ttu-id="5f8fd-166">ProductID</span><span class="sxs-lookup"><span data-stu-id="5f8fd-166">ProductID</span></span>|<span data-ttu-id="5f8fd-167">...</span><span class="sxs-lookup"><span data-stu-id="5f8fd-167">...</span></span>|  
|------------------------|---------------------------|--------------|---------------|---------|  
|<span data-ttu-id="5f8fd-168">1</span><span class="sxs-lookup"><span data-stu-id="5f8fd-168">1</span></span>|<span data-ttu-id="5f8fd-169">4911-403C-98</span><span class="sxs-lookup"><span data-stu-id="5f8fd-169">4911-403C-98</span></span>|<span data-ttu-id="5f8fd-170">1</span><span class="sxs-lookup"><span data-stu-id="5f8fd-170">1</span></span>|<span data-ttu-id="5f8fd-171">776</span><span class="sxs-lookup"><span data-stu-id="5f8fd-171">776</span></span>|<span data-ttu-id="5f8fd-172">...</span><span class="sxs-lookup"><span data-stu-id="5f8fd-172">...</span></span>|  
|<span data-ttu-id="5f8fd-173">2</span><span class="sxs-lookup"><span data-stu-id="5f8fd-173">2</span></span>|<span data-ttu-id="5f8fd-174">4911-403C-98</span><span class="sxs-lookup"><span data-stu-id="5f8fd-174">4911-403C-98</span></span>|<span data-ttu-id="5f8fd-175">3</span><span class="sxs-lookup"><span data-stu-id="5f8fd-175">3</span></span>|<span data-ttu-id="5f8fd-176">777</span><span class="sxs-lookup"><span data-stu-id="5f8fd-176">777</span></span>|<span data-ttu-id="5f8fd-177">...</span><span class="sxs-lookup"><span data-stu-id="5f8fd-177">...</span></span>|  
|<span data-ttu-id="5f8fd-178">...</span><span class="sxs-lookup"><span data-stu-id="5f8fd-178">...</span></span>|<span data-ttu-id="5f8fd-179">...</span><span class="sxs-lookup"><span data-stu-id="5f8fd-179">...</span></span>|<span data-ttu-id="5f8fd-180">...</span><span class="sxs-lookup"><span data-stu-id="5f8fd-180">...</span></span>|<span data-ttu-id="5f8fd-181">...</span><span class="sxs-lookup"><span data-stu-id="5f8fd-181">...</span></span>|<span data-ttu-id="5f8fd-182">...</span><span class="sxs-lookup"><span data-stu-id="5f8fd-182">...</span></span>|  
  
## <a name="references"></a><span data-ttu-id="5f8fd-183">Odkazy</span><span class="sxs-lookup"><span data-stu-id="5f8fd-183">References</span></span>  
  
### <a name="ref"></a><span data-ttu-id="5f8fd-184">REF</span><span class="sxs-lookup"><span data-stu-id="5f8fd-184">REF</span></span>  
 <span data-ttu-id="5f8fd-185">[REF](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md) vytvoří odkaz na typ instance entity.</span><span class="sxs-lookup"><span data-stu-id="5f8fd-185">[REF](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md) creates a reference to an entity type instance.</span></span> <span data-ttu-id="5f8fd-186">Například následující dotaz vrátí odkazy na každé pořadí entity v sadě entit objednávky:</span><span class="sxs-lookup"><span data-stu-id="5f8fd-186">For example, the following query returns references to each Order entity in the Orders entity set:</span></span>  
  
```  
SELECT REF(o) AS OrderID FROM Orders AS o  
```  
  
 <span data-ttu-id="5f8fd-187">Výstup:</span><span class="sxs-lookup"><span data-stu-id="5f8fd-187">Output:</span></span>  
  
|<span data-ttu-id="5f8fd-188">Hodnota</span><span class="sxs-lookup"><span data-stu-id="5f8fd-188">Value</span></span>|  
|-----------|  
|<span data-ttu-id="5f8fd-189">1</span><span class="sxs-lookup"><span data-stu-id="5f8fd-189">1</span></span>|  
|<span data-ttu-id="5f8fd-190">2</span><span class="sxs-lookup"><span data-stu-id="5f8fd-190">2</span></span>|  
|<span data-ttu-id="5f8fd-191">3</span><span class="sxs-lookup"><span data-stu-id="5f8fd-191">3</span></span>|  
|<span data-ttu-id="5f8fd-192">...</span><span class="sxs-lookup"><span data-stu-id="5f8fd-192">...</span></span>|  
  
 <span data-ttu-id="5f8fd-193">Následující příklad používá operátor extrakce vlastnost (.) pro přístup k vlastnosti entity.</span><span class="sxs-lookup"><span data-stu-id="5f8fd-193">The following example uses the property extraction operator (.) to access a property of an entity.</span></span> <span data-ttu-id="5f8fd-194">Pokud operátor extrakce vlastnost se používá, je automaticky dereferenced odkaz.</span><span class="sxs-lookup"><span data-stu-id="5f8fd-194">When the property extraction operator is used, the reference is automatically dereferenced.</span></span>  
  
 <span data-ttu-id="5f8fd-195">Příklad:</span><span class="sxs-lookup"><span data-stu-id="5f8fd-195">Example:</span></span>  
  
```  
SELECT VALUE REF(p).Name FROM   
    AdventureWorksEntities.Product as p  
```  
  
 <span data-ttu-id="5f8fd-196">Výstup:</span><span class="sxs-lookup"><span data-stu-id="5f8fd-196">Output:</span></span>  
  
|<span data-ttu-id="5f8fd-197">Hodnota</span><span class="sxs-lookup"><span data-stu-id="5f8fd-197">Value</span></span>|  
|-----------|  
|<span data-ttu-id="5f8fd-198">Upravit soupeření</span><span class="sxs-lookup"><span data-stu-id="5f8fd-198">Adjustable Race</span></span>|  
|<span data-ttu-id="5f8fd-199">Všechny účely kolo úsporný režim</span><span class="sxs-lookup"><span data-stu-id="5f8fd-199">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="5f8fd-200">AWC Logo zakončení</span><span class="sxs-lookup"><span data-stu-id="5f8fd-200">AWC Logo Cap</span></span>|  
|<span data-ttu-id="5f8fd-201">...</span><span class="sxs-lookup"><span data-stu-id="5f8fd-201">...</span></span>|  
  
### <a name="deref"></a><span data-ttu-id="5f8fd-202">DEREF</span><span class="sxs-lookup"><span data-stu-id="5f8fd-202">DEREF</span></span>  
 <span data-ttu-id="5f8fd-203">[DEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md) dereferences hodnota odkazu a vytváří výsledek této dereference.</span><span class="sxs-lookup"><span data-stu-id="5f8fd-203">[DEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md) dereferences a reference value and produces the result of that dereference.</span></span> <span data-ttu-id="5f8fd-204">Například následující dotaz vytváří pořadí entity pro každé pořadí v sadě entit objednávky: `SELECT DEREF(o2.r) FROM (SELECT REF(o) AS r FROM LOB.Orders AS o) AS o2`...</span><span class="sxs-lookup"><span data-stu-id="5f8fd-204">For example, the following query produces the Order entities for each Order in the Orders entity set: `SELECT DEREF(o2.r) FROM (SELECT REF(o) AS r FROM LOB.Orders AS o) AS o2`..</span></span>  
  
 <span data-ttu-id="5f8fd-205">Příklad:</span><span class="sxs-lookup"><span data-stu-id="5f8fd-205">Example:</span></span>  
  
```  
SELECT VALUE DEREF(REF(p)).Name FROM   
    AdventureWorksEntities.Product as p  
```  
  
 <span data-ttu-id="5f8fd-206">Výstup:</span><span class="sxs-lookup"><span data-stu-id="5f8fd-206">Output:</span></span>  
  
|<span data-ttu-id="5f8fd-207">Hodnota</span><span class="sxs-lookup"><span data-stu-id="5f8fd-207">Value</span></span>|  
|-----------|  
|<span data-ttu-id="5f8fd-208">Upravit soupeření</span><span class="sxs-lookup"><span data-stu-id="5f8fd-208">Adjustable Race</span></span>|  
|<span data-ttu-id="5f8fd-209">Všechny účely kolo úsporný režim</span><span class="sxs-lookup"><span data-stu-id="5f8fd-209">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="5f8fd-210">AWC Logo zakončení</span><span class="sxs-lookup"><span data-stu-id="5f8fd-210">AWC Logo Cap</span></span>|  
|<span data-ttu-id="5f8fd-211">...</span><span class="sxs-lookup"><span data-stu-id="5f8fd-211">...</span></span>|  
  
### <a name="createref-and-key"></a><span data-ttu-id="5f8fd-212">CREATEREF A KLÍČ</span><span class="sxs-lookup"><span data-stu-id="5f8fd-212">CREATEREF AND KEY</span></span>  
 <span data-ttu-id="5f8fd-213">[CREATEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md) vytvoří odkaz předávání klíč.</span><span class="sxs-lookup"><span data-stu-id="5f8fd-213">[CREATEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md) creates a reference passing a key.</span></span> <span data-ttu-id="5f8fd-214">[KLÍČ](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md) extrahuje část výraz obsahující odkaz na typ klíče.</span><span class="sxs-lookup"><span data-stu-id="5f8fd-214">[KEY](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md) extracts the key portion of an expression with type reference.</span></span>  
  
 <span data-ttu-id="5f8fd-215">Příklad:</span><span class="sxs-lookup"><span data-stu-id="5f8fd-215">Example:</span></span>  
  
```  
SELECT VALUE Key(CreateRef(AdventureWorksEntities.Product, row(p.ProductID)))   
    FROM AdventureWorksEntities.Product as p  
```  
  
 <span data-ttu-id="5f8fd-216">Výstup:</span><span class="sxs-lookup"><span data-stu-id="5f8fd-216">Output:</span></span>  
  
|<span data-ttu-id="5f8fd-217">ProductID</span><span class="sxs-lookup"><span data-stu-id="5f8fd-217">ProductID</span></span>|  
|---------------|  
|<span data-ttu-id="5f8fd-218">980</span><span class="sxs-lookup"><span data-stu-id="5f8fd-218">980</span></span>|  
|<span data-ttu-id="5f8fd-219">365</span><span class="sxs-lookup"><span data-stu-id="5f8fd-219">365</span></span>|  
|<span data-ttu-id="5f8fd-220">771</span><span class="sxs-lookup"><span data-stu-id="5f8fd-220">771</span></span>|  
|<span data-ttu-id="5f8fd-221">...</span><span class="sxs-lookup"><span data-stu-id="5f8fd-221">...</span></span>|  
  
## <a name="functions"></a><span data-ttu-id="5f8fd-222">Funkce</span><span class="sxs-lookup"><span data-stu-id="5f8fd-222">Functions</span></span>  
  
### <a name="canonical"></a><span data-ttu-id="5f8fd-223">Kanonickém tvaru</span><span class="sxs-lookup"><span data-stu-id="5f8fd-223">Canonical</span></span>  
 <span data-ttu-id="5f8fd-224">Obor názvů pro [kanonické funkce](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md) je Edm, jako v `Edm.Length("string")`.</span><span class="sxs-lookup"><span data-stu-id="5f8fd-224">The namespace for [canonical functions](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md) is Edm, as in `Edm.Length("string")`.</span></span> <span data-ttu-id="5f8fd-225">Nemáte zadejte obor názvů, pokud jiný obor názvů je naimportována obsahující funkci se stejným názvem jako kanonické funkce.</span><span class="sxs-lookup"><span data-stu-id="5f8fd-225">You do not have to specify the namespace unless another namespace is imported that contains a function with the same name as a canonical function.</span></span> <span data-ttu-id="5f8fd-226">Pokud dva obory názvů mají stejnou funkci, uživatel má konkrétní úplný název.</span><span class="sxs-lookup"><span data-stu-id="5f8fd-226">If two namespaces have the same function, the user should specific the full name.</span></span>  
  
 <span data-ttu-id="5f8fd-227">Příklad:</span><span class="sxs-lookup"><span data-stu-id="5f8fd-227">Example:</span></span>  
  
```  
SELECT Length(c. FirstName) As NameLen FROM   
    AdventureWorksEntities.Contact AS c   
    WHERE c.ContactID BETWEEN 10 AND 12  
```  
  
 <span data-ttu-id="5f8fd-228">Výstup:</span><span class="sxs-lookup"><span data-stu-id="5f8fd-228">Output:</span></span>  
  
|<span data-ttu-id="5f8fd-229">NameLen</span><span class="sxs-lookup"><span data-stu-id="5f8fd-229">NameLen</span></span>|  
|-------------|  
|<span data-ttu-id="5f8fd-230">6</span><span class="sxs-lookup"><span data-stu-id="5f8fd-230">6</span></span>|  
|<span data-ttu-id="5f8fd-231">6</span><span class="sxs-lookup"><span data-stu-id="5f8fd-231">6</span></span>|  
|<span data-ttu-id="5f8fd-232">5</span><span class="sxs-lookup"><span data-stu-id="5f8fd-232">5</span></span>|  
  
### <a name="microsoft-provider-specific"></a><span data-ttu-id="5f8fd-233">Zprostředkovatel specifické pro společnost Microsoft</span><span class="sxs-lookup"><span data-stu-id="5f8fd-233">Microsoft Provider-Specific</span></span>  
 <span data-ttu-id="5f8fd-234">[Funkce specifické pro zprostředkovatele Microsoft](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md) v `SqlServer` oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="5f8fd-234">[Microsoft provider-specific functions](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md) are in the `SqlServer` namespace.</span></span>  
  
 <span data-ttu-id="5f8fd-235">Příklad:</span><span class="sxs-lookup"><span data-stu-id="5f8fd-235">Example:</span></span>  
  
```  
SELECT SqlServer.LEN(c.EmailAddress) As EmailLen FROM   
    AdventureWorksEntities.Contact AS c WHERE   
    c.ContactID BETWEEN 10 AND 12  
```  
  
 <span data-ttu-id="5f8fd-236">Výstup:</span><span class="sxs-lookup"><span data-stu-id="5f8fd-236">Output:</span></span>  
  
|<span data-ttu-id="5f8fd-237">EmailLen</span><span class="sxs-lookup"><span data-stu-id="5f8fd-237">EmailLen</span></span>|  
|--------------|  
|<span data-ttu-id="5f8fd-238">27</span><span class="sxs-lookup"><span data-stu-id="5f8fd-238">27</span></span>|  
|<span data-ttu-id="5f8fd-239">27</span><span class="sxs-lookup"><span data-stu-id="5f8fd-239">27</span></span>|  
|<span data-ttu-id="5f8fd-240">26</span><span class="sxs-lookup"><span data-stu-id="5f8fd-240">26</span></span>|  
  
## <a name="namespaces"></a><span data-ttu-id="5f8fd-241">Jmenné prostory</span><span class="sxs-lookup"><span data-stu-id="5f8fd-241">Namespaces</span></span>  
 <span data-ttu-id="5f8fd-242">[POMOCÍ](../../../../../../docs/framework/data/adonet/ef/language-reference/using-entity-sql.md) určuje oborů názvů používaných ve výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="5f8fd-242">[USING](../../../../../../docs/framework/data/adonet/ef/language-reference/using-entity-sql.md) specifies namespaces used in a query expression.</span></span>  
  
 <span data-ttu-id="5f8fd-243">Příklad:</span><span class="sxs-lookup"><span data-stu-id="5f8fd-243">Example:</span></span>  
  
```  
using SqlServer; LOWER('AA');  
```  
  
 <span data-ttu-id="5f8fd-244">Výstup:</span><span class="sxs-lookup"><span data-stu-id="5f8fd-244">Output:</span></span>  
  
|<span data-ttu-id="5f8fd-245">Hodnota</span><span class="sxs-lookup"><span data-stu-id="5f8fd-245">Value</span></span>|  
|-----------|  
|<span data-ttu-id="5f8fd-246">aa</span><span class="sxs-lookup"><span data-stu-id="5f8fd-246">aa</span></span>|  
  
## <a name="paging"></a><span data-ttu-id="5f8fd-247">Stránkování</span><span class="sxs-lookup"><span data-stu-id="5f8fd-247">Paging</span></span>  
 <span data-ttu-id="5f8fd-248">Stránkování rozdíl lze vyjádřit pomocí deklarace [přeskočit](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md) a [LIMIT](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md) dílčí klauzule k [Order](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) klauzule.</span><span class="sxs-lookup"><span data-stu-id="5f8fd-248">Paging can be expressed by declaring a [SKIP](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md) and [LIMIT](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md) sub-clauses to the [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) clause.</span></span>  
  
 <span data-ttu-id="5f8fd-249">Příklad:</span><span class="sxs-lookup"><span data-stu-id="5f8fd-249">Example:</span></span>  
  
```  
SELECT c.ContactID as ID, c.LastName as Name FROM   
    AdventureWorks.Contact AS c ORDER BY c.ContactID SKIP 9 LIMIT 3;  
```  
  
 <span data-ttu-id="5f8fd-250">Výstup:</span><span class="sxs-lookup"><span data-stu-id="5f8fd-250">Output:</span></span>  
  
|<span data-ttu-id="5f8fd-251">ID</span><span class="sxs-lookup"><span data-stu-id="5f8fd-251">ID</span></span>|<span data-ttu-id="5f8fd-252">Název</span><span class="sxs-lookup"><span data-stu-id="5f8fd-252">Name</span></span>|  
|--------|----------|  
|<span data-ttu-id="5f8fd-253">10</span><span class="sxs-lookup"><span data-stu-id="5f8fd-253">10</span></span>|<span data-ttu-id="5f8fd-254">Adina</span><span class="sxs-lookup"><span data-stu-id="5f8fd-254">Adina</span></span>|  
|<span data-ttu-id="5f8fd-255">11</span><span class="sxs-lookup"><span data-stu-id="5f8fd-255">11</span></span>|<span data-ttu-id="5f8fd-256">Agcaoili</span><span class="sxs-lookup"><span data-stu-id="5f8fd-256">Agcaoili</span></span>|  
|<span data-ttu-id="5f8fd-257">12</span><span class="sxs-lookup"><span data-stu-id="5f8fd-257">12</span></span>|<span data-ttu-id="5f8fd-258">Aguilar</span><span class="sxs-lookup"><span data-stu-id="5f8fd-258">Aguilar</span></span>|  
  
## <a name="grouping"></a><span data-ttu-id="5f8fd-259">Seskupování</span><span class="sxs-lookup"><span data-stu-id="5f8fd-259">Grouping</span></span>  
 <span data-ttu-id="5f8fd-260">[SESKUPENÍ podle](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md) Určuje skupiny, do které objektů vrácených dotazem ([vyberte](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)) výrazu mají být umístěny.</span><span class="sxs-lookup"><span data-stu-id="5f8fd-260">[GROUPING BY](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md) specifies groups into which objects returned by a query ([SELECT](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)) expression are to be placed.</span></span>  
  
 <span data-ttu-id="5f8fd-261">Příklad:</span><span class="sxs-lookup"><span data-stu-id="5f8fd-261">Example:</span></span>  
  
```  
SELECT VALUE name FROM AdventureWorksEntities.Product as P   
    GROUP BY P.Name HAVING MAX(P.ListPrice) > 5  
```  
  
 <span data-ttu-id="5f8fd-262">Výstup:</span><span class="sxs-lookup"><span data-stu-id="5f8fd-262">Output:</span></span>  
  
|<span data-ttu-id="5f8fd-263">name</span><span class="sxs-lookup"><span data-stu-id="5f8fd-263">name</span></span>|  
|----------|  
|<span data-ttu-id="5f8fd-264">Le Horská stanici sestavení</span><span class="sxs-lookup"><span data-stu-id="5f8fd-264">LL Mountain Seat Assembly</span></span>|  
|<span data-ttu-id="5f8fd-265">ML Horská stanici sestavení</span><span class="sxs-lookup"><span data-stu-id="5f8fd-265">ML Mountain Seat Assembly</span></span>|  
|<span data-ttu-id="5f8fd-266">HL Horská stanici sestavení</span><span class="sxs-lookup"><span data-stu-id="5f8fd-266">HL Mountain Seat Assembly</span></span>|  
|<span data-ttu-id="5f8fd-267">...</span><span class="sxs-lookup"><span data-stu-id="5f8fd-267">...</span></span>|  
  
## <a name="navigation"></a><span data-ttu-id="5f8fd-268">Navigace</span><span class="sxs-lookup"><span data-stu-id="5f8fd-268">Navigation</span></span>  
 <span data-ttu-id="5f8fd-269">Operátor navigační vztah můžete přejít přes vztah z jedné entity (od konce) na jiný (na konec).</span><span class="sxs-lookup"><span data-stu-id="5f8fd-269">The relationship navigation operator allows you to navigate over the relationship from one entity (from end) to another (to end).</span></span> <span data-ttu-id="5f8fd-270">[NAVIGOVAT](../../../../../../docs/framework/data/adonet/ef/language-reference/navigate-entity-sql.md) trvá kvalifikovaný typ vztahu jako \<obor názvů >.\< Název typu vztahu >.</span><span class="sxs-lookup"><span data-stu-id="5f8fd-270">[NAVIGATE](../../../../../../docs/framework/data/adonet/ef/language-reference/navigate-entity-sql.md) takes the relationship type qualified as \<namespace>.\<relationship type name>.</span></span> <span data-ttu-id="5f8fd-271">Přejděte vrátí Ref\<T > Pokud mohutnost pro ukončení je 1.</span><span class="sxs-lookup"><span data-stu-id="5f8fd-271">Navigate returns Ref\<T> if the cardinality of the to end is 1.</span></span> <span data-ttu-id="5f8fd-272">Pokud na kardinalitu pro ukončení je n, kolekce < Ref\<T >> bude vrácen.</span><span class="sxs-lookup"><span data-stu-id="5f8fd-272">If the cardinality of the to end is n, the Collection<Ref\<T>> will be returned.</span></span>  
  
 <span data-ttu-id="5f8fd-273">Příklad:</span><span class="sxs-lookup"><span data-stu-id="5f8fd-273">Example:</span></span>  
  
```  
SELECT a.AddressID, (SELECT VALUE DEREF(v) FROM   
    NAVIGATE(a, AdventureWorksModel.FK_SalesOrderHeader_Address_BillToAddressID) AS v)   
    FROM AdventureWorksEntities.Address AS a  
```  
  
 <span data-ttu-id="5f8fd-274">Výstup:</span><span class="sxs-lookup"><span data-stu-id="5f8fd-274">Output:</span></span>  
  
|<span data-ttu-id="5f8fd-275">AddressID</span><span class="sxs-lookup"><span data-stu-id="5f8fd-275">AddressID</span></span>|  
|---------------|  
|<span data-ttu-id="5f8fd-276">1</span><span class="sxs-lookup"><span data-stu-id="5f8fd-276">1</span></span>|  
|<span data-ttu-id="5f8fd-277">2</span><span class="sxs-lookup"><span data-stu-id="5f8fd-277">2</span></span>|  
|<span data-ttu-id="5f8fd-278">3</span><span class="sxs-lookup"><span data-stu-id="5f8fd-278">3</span></span>|  
|<span data-ttu-id="5f8fd-279">...</span><span class="sxs-lookup"><span data-stu-id="5f8fd-279">...</span></span>|  
  
## <a name="select-value-and-select"></a><span data-ttu-id="5f8fd-280">VYBERTE HODNOTU A VYBERTE</span><span class="sxs-lookup"><span data-stu-id="5f8fd-280">SELECT VALUE AND SELECT</span></span>  
  
### <a name="select-value"></a><span data-ttu-id="5f8fd-281">VYBERTE HODNOTU</span><span class="sxs-lookup"><span data-stu-id="5f8fd-281">SELECT VALUE</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="5f8fd-282"> poskytuje v klauzuli SELECT VALUE tak, aby přeskočil konstrukce implicitní řádek.</span><span class="sxs-lookup"><span data-stu-id="5f8fd-282"> provides the SELECT VALUE clause to skip the implicit row construction.</span></span> <span data-ttu-id="5f8fd-283">V klauzuli SELECT VALUE lze zadat pouze jednu položku.</span><span class="sxs-lookup"><span data-stu-id="5f8fd-283">Only one item can be specified in a SELECT VALUE clause.</span></span> <span data-ttu-id="5f8fd-284">Když se používá tato klauzule, sestavený žádný řádek obálku kolem položky v klauzuli SELECT a kolekce požadovaný tvar je možné vytvořit, například: `SELECT VALUE a`.</span><span class="sxs-lookup"><span data-stu-id="5f8fd-284">When such a clause is used, no row wrapper is constructed around the items in the SELECT clause, and a collection of the desired shape can be produced, for example: `SELECT VALUE a`.</span></span>  
  
 <span data-ttu-id="5f8fd-285">Příklad:</span><span class="sxs-lookup"><span data-stu-id="5f8fd-285">Example:</span></span>  
  
```  
SELECT VALUE p.Name FROM AdventureWorksEntities.Product as p  
```  
  
 <span data-ttu-id="5f8fd-286">Výstup:</span><span class="sxs-lookup"><span data-stu-id="5f8fd-286">Output:</span></span>  
  
|<span data-ttu-id="5f8fd-287">Název</span><span class="sxs-lookup"><span data-stu-id="5f8fd-287">Name</span></span>|  
|----------|  
|<span data-ttu-id="5f8fd-288">Upravit soupeření</span><span class="sxs-lookup"><span data-stu-id="5f8fd-288">Adjustable Race</span></span>|  
|<span data-ttu-id="5f8fd-289">Všechny účely kolo úsporný režim</span><span class="sxs-lookup"><span data-stu-id="5f8fd-289">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="5f8fd-290">AWC Logo zakončení</span><span class="sxs-lookup"><span data-stu-id="5f8fd-290">AWC Logo Cap</span></span>|  
|<span data-ttu-id="5f8fd-291">...</span><span class="sxs-lookup"><span data-stu-id="5f8fd-291">...</span></span>|  
  
### <a name="select"></a><span data-ttu-id="5f8fd-292">VYBERTE</span><span class="sxs-lookup"><span data-stu-id="5f8fd-292">SELECT</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="5f8fd-293"> také poskytuje konstruktor row můžete vytvořit libovolný řádků.</span><span class="sxs-lookup"><span data-stu-id="5f8fd-293"> also provides the row constructor to construct arbitrary rows.</span></span> <span data-ttu-id="5f8fd-294">Vyberte trvá jeden či více elementů v projekci a má za následek záznam dat s poli, například: `SELECT a, b, c`.</span><span class="sxs-lookup"><span data-stu-id="5f8fd-294">SELECT takes one or more elements in the projection and results in a data record with fields, for example: `SELECT a, b, c`.</span></span>  
  
 <span data-ttu-id="5f8fd-295">Příklad:</span><span class="sxs-lookup"><span data-stu-id="5f8fd-295">Example:</span></span>  
  
 <span data-ttu-id="5f8fd-296">Vyberte p.Name, p.ProductID z AdventureWorksEntities.Product jako p výstup:</span><span class="sxs-lookup"><span data-stu-id="5f8fd-296">SELECT p.Name, p.ProductID FROM AdventureWorksEntities.Product as p Output:</span></span>  
  
|<span data-ttu-id="5f8fd-297">Název</span><span class="sxs-lookup"><span data-stu-id="5f8fd-297">Name</span></span>|<span data-ttu-id="5f8fd-298">ProductID</span><span class="sxs-lookup"><span data-stu-id="5f8fd-298">ProductID</span></span>|  
|----------|---------------|  
|<span data-ttu-id="5f8fd-299">Upravit soupeření</span><span class="sxs-lookup"><span data-stu-id="5f8fd-299">Adjustable Race</span></span>|<span data-ttu-id="5f8fd-300">1</span><span class="sxs-lookup"><span data-stu-id="5f8fd-300">1</span></span>|  
|<span data-ttu-id="5f8fd-301">Všechny účely kolo úsporný režim</span><span class="sxs-lookup"><span data-stu-id="5f8fd-301">All-Purpose Bike Stand</span></span>|<span data-ttu-id="5f8fd-302">879</span><span class="sxs-lookup"><span data-stu-id="5f8fd-302">879</span></span>|  
|<span data-ttu-id="5f8fd-303">AWC Logo zakončení</span><span class="sxs-lookup"><span data-stu-id="5f8fd-303">AWC Logo Cap</span></span>|<span data-ttu-id="5f8fd-304">712</span><span class="sxs-lookup"><span data-stu-id="5f8fd-304">712</span></span>|  
|<span data-ttu-id="5f8fd-305">...</span><span class="sxs-lookup"><span data-stu-id="5f8fd-305">...</span></span>|<span data-ttu-id="5f8fd-306">...</span><span class="sxs-lookup"><span data-stu-id="5f8fd-306">...</span></span>|  
  
## <a name="case-expression"></a><span data-ttu-id="5f8fd-307">VÝRAZ CASE</span><span class="sxs-lookup"><span data-stu-id="5f8fd-307">CASE EXPRESSION</span></span>  
 <span data-ttu-id="5f8fd-308">[Případ výraz](../../../../../../docs/framework/data/adonet/ef/language-reference/case-entity-sql.md) vyhodnotí sadu logických výrazů k určení výsledku.</span><span class="sxs-lookup"><span data-stu-id="5f8fd-308">The [case expression](../../../../../../docs/framework/data/adonet/ef/language-reference/case-entity-sql.md) evaluates a set of Boolean expressions to determine the result.</span></span>  
  
 <span data-ttu-id="5f8fd-309">Příklad:</span><span class="sxs-lookup"><span data-stu-id="5f8fd-309">Example:</span></span>  
  
```  
CASE WHEN AVG({25,12,11}) < 100 THEN TRUE ELSE FALSE END  
```  
  
 <span data-ttu-id="5f8fd-310">Výstup:</span><span class="sxs-lookup"><span data-stu-id="5f8fd-310">Output:</span></span>  
  
|<span data-ttu-id="5f8fd-311">Hodnota</span><span class="sxs-lookup"><span data-stu-id="5f8fd-311">Value</span></span>|  
|-----------|  
|<span data-ttu-id="5f8fd-312">HODNOTA TRUE</span><span class="sxs-lookup"><span data-stu-id="5f8fd-312">TRUE</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5f8fd-313">Viz také</span><span class="sxs-lookup"><span data-stu-id="5f8fd-313">See Also</span></span>  
 [<span data-ttu-id="5f8fd-314">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="5f8fd-314">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="5f8fd-315">Přehled Entity SQL</span><span class="sxs-lookup"><span data-stu-id="5f8fd-315">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
