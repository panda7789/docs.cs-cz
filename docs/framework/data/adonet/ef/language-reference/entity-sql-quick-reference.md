---
title: Stručná referenční příručka Entity SQL
ms.date: 03/30/2017
ms.assetid: e53dad9e-5e83-426e-abb4-be3e78e3d6dc
ms.openlocfilehash: 20d8d1cb1e4b5cbf37dffcce6a7e79c2a4c265d3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54539400"
---
# <a name="entity-sql-quick-reference"></a><span data-ttu-id="74e87-102">Stručná referenční příručka Entity SQL</span><span class="sxs-lookup"><span data-stu-id="74e87-102">Entity SQL Quick Reference</span></span>
<span data-ttu-id="74e87-103">Toto téma poskytuje rychlý odkaz na [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dotazy.</span><span class="sxs-lookup"><span data-stu-id="74e87-103">This topic provides a quick reference to [!INCLUDE[esql](../../../../../../includes/esql-md.md)] queries.</span></span> <span data-ttu-id="74e87-104">Dotazy v tomto tématu jsou založeny na modelu AdventureWorks Sales.</span><span class="sxs-lookup"><span data-stu-id="74e87-104">The queries in this topic are based on the AdventureWorks Sales model.</span></span>  
  
## <a name="literals"></a><span data-ttu-id="74e87-105">Literály</span><span class="sxs-lookup"><span data-stu-id="74e87-105">Literals</span></span>  
  
### <a name="string"></a><span data-ttu-id="74e87-106">String</span><span class="sxs-lookup"><span data-stu-id="74e87-106">String</span></span>  
 <span data-ttu-id="74e87-107">Existují řetězcové literály znaků Unicode a kódování Unicode.</span><span class="sxs-lookup"><span data-stu-id="74e87-107">There are Unicode and non-Unicode character string literals.</span></span> <span data-ttu-id="74e87-108">Řetězce Unicode jsou předponou N. Například `N'hello'`.</span><span class="sxs-lookup"><span data-stu-id="74e87-108">Unicode strings are prepended with N. For example, `N'hello'`.</span></span>  
  
 <span data-ttu-id="74e87-109">Následuje příklad Non-Unicode řetězcového literálu:</span><span class="sxs-lookup"><span data-stu-id="74e87-109">The following is an example of a Non-Unicode string literal:</span></span>  
  
```  
'hello'  
--same as  
"hello"  
```  
  
 <span data-ttu-id="74e87-110">Výstup:</span><span class="sxs-lookup"><span data-stu-id="74e87-110">Output:</span></span>  
  
|<span data-ttu-id="74e87-111">Hodnota</span><span class="sxs-lookup"><span data-stu-id="74e87-111">Value</span></span>|  
|-----------|  
|<span data-ttu-id="74e87-112">Dobrý den</span><span class="sxs-lookup"><span data-stu-id="74e87-112">hello</span></span>|  
  
### <a name="datetime"></a><span data-ttu-id="74e87-113">DateTime</span><span class="sxs-lookup"><span data-stu-id="74e87-113">DateTime</span></span>  
 <span data-ttu-id="74e87-114">V literálech datum a čas datum a čas části jsou povinné.</span><span class="sxs-lookup"><span data-stu-id="74e87-114">In DateTime literals, both date and time parts are mandatory.</span></span> <span data-ttu-id="74e87-115">Neexistují žádné výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="74e87-115">There are no default values.</span></span>  
  
 <span data-ttu-id="74e87-116">Příklad:</span><span class="sxs-lookup"><span data-stu-id="74e87-116">Example:</span></span>  
  
```  
DATETIME '2006-12-25 01:01:00.000'   
--same as  
DATETIME '2006-12-25 01:01'  
```  
  
 <span data-ttu-id="74e87-117">Výstup:</span><span class="sxs-lookup"><span data-stu-id="74e87-117">Output:</span></span>  
  
|<span data-ttu-id="74e87-118">Hodnota</span><span class="sxs-lookup"><span data-stu-id="74e87-118">Value</span></span>|  
|-----------|  
|<span data-ttu-id="74e87-119">12/25/2006 1:01:00: 00</span><span class="sxs-lookup"><span data-stu-id="74e87-119">12/25/2006 1:01:00 AM</span></span>|  
  
### <a name="integer"></a><span data-ttu-id="74e87-120">Integer</span><span class="sxs-lookup"><span data-stu-id="74e87-120">Integer</span></span>  
 <span data-ttu-id="74e87-121">Literály celých čísel může být typu Int32 (123), UInt32 (123U), Int64 (123L) a UInt64 (123UL).</span><span class="sxs-lookup"><span data-stu-id="74e87-121">Integer literals can be of type Int32 (123), UInt32 (123U), Int64 (123L), and UInt64 (123UL).</span></span>  
  
 <span data-ttu-id="74e87-122">Příklad:</span><span class="sxs-lookup"><span data-stu-id="74e87-122">Example:</span></span>  
  
```  
--a collection of integers  
{1, 2, 3}  
```  
  
 <span data-ttu-id="74e87-123">Výstup:</span><span class="sxs-lookup"><span data-stu-id="74e87-123">Output:</span></span>  
  
|<span data-ttu-id="74e87-124">Hodnota</span><span class="sxs-lookup"><span data-stu-id="74e87-124">Value</span></span>|  
|-----------|  
|<span data-ttu-id="74e87-125">1</span><span class="sxs-lookup"><span data-stu-id="74e87-125">1</span></span>|  
|<span data-ttu-id="74e87-126">2</span><span class="sxs-lookup"><span data-stu-id="74e87-126">2</span></span>|  
|<span data-ttu-id="74e87-127">3</span><span class="sxs-lookup"><span data-stu-id="74e87-127">3</span></span>|  
  
### <a name="other"></a><span data-ttu-id="74e87-128">Ostatní</span><span class="sxs-lookup"><span data-stu-id="74e87-128">Other</span></span>  
 <span data-ttu-id="74e87-129">Ostatní literály, které podporuje [!INCLUDE[esql](../../../../../../includes/esql-md.md)] jsou identifikátor Guid, binární soubor, Float nebo Double, Decimal, a `null`.</span><span class="sxs-lookup"><span data-stu-id="74e87-129">Other literals supported by [!INCLUDE[esql](../../../../../../includes/esql-md.md)] are Guid, Binary, Float/Double, Decimal, and `null`.</span></span> <span data-ttu-id="74e87-130">Hodnota Null, literály v [!INCLUDE[esql](../../../../../../includes/esql-md.md)] jsou považovány za kompatibilní se každý jiný typ v konceptuálním modelu.</span><span class="sxs-lookup"><span data-stu-id="74e87-130">Null literals in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] are considered to be compatible with every other type in the conceptual model.</span></span>  
  
## <a name="type-constructors"></a><span data-ttu-id="74e87-131">Konstruktory typu</span><span class="sxs-lookup"><span data-stu-id="74e87-131">Type Constructors</span></span>  
  
### <a name="row"></a><span data-ttu-id="74e87-132">ŘÁDEK</span><span class="sxs-lookup"><span data-stu-id="74e87-132">ROW</span></span>  
 <span data-ttu-id="74e87-133">[ŘÁDEK](../../../../../../docs/framework/data/adonet/ef/language-reference/row-entity-sql.md) vytvoří anonymní, typované strukturálně (záznamů) hodnotu jako v: `ROW(1 AS myNumber, ‘Name’ AS myName).`</span><span class="sxs-lookup"><span data-stu-id="74e87-133">[ROW](../../../../../../docs/framework/data/adonet/ef/language-reference/row-entity-sql.md) constructs an anonymous, structurally-typed (record) value as in: `ROW(1 AS myNumber, ‘Name’ AS myName).`</span></span>  
  
 <span data-ttu-id="74e87-134">Příklad:</span><span class="sxs-lookup"><span data-stu-id="74e87-134">Example:</span></span>  
  
```  
SELECT VALUE row (product.ProductID as ProductID, product.Name   
    as ProductName) FROM AdventureWorksEntities.Product AS product  
```  
  
 <span data-ttu-id="74e87-135">Výstup:</span><span class="sxs-lookup"><span data-stu-id="74e87-135">Output:</span></span>  
  
|<span data-ttu-id="74e87-136">ProductID</span><span class="sxs-lookup"><span data-stu-id="74e87-136">ProductID</span></span>|<span data-ttu-id="74e87-137">Název</span><span class="sxs-lookup"><span data-stu-id="74e87-137">Name</span></span>|  
|---------------|----------|  
|<span data-ttu-id="74e87-138">1</span><span class="sxs-lookup"><span data-stu-id="74e87-138">1</span></span>|<span data-ttu-id="74e87-139">Měnitelné závodu</span><span class="sxs-lookup"><span data-stu-id="74e87-139">Adjustable Race</span></span>|  
|<span data-ttu-id="74e87-140">879</span><span class="sxs-lookup"><span data-stu-id="74e87-140">879</span></span>|<span data-ttu-id="74e87-141">Univerzální kol samostatné</span><span class="sxs-lookup"><span data-stu-id="74e87-141">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="74e87-142">712</span><span class="sxs-lookup"><span data-stu-id="74e87-142">712</span></span>|<span data-ttu-id="74e87-143">AWC Logo zakončení</span><span class="sxs-lookup"><span data-stu-id="74e87-143">AWC Logo Cap</span></span>|  
|<span data-ttu-id="74e87-144">...</span><span class="sxs-lookup"><span data-stu-id="74e87-144">...</span></span>|<span data-ttu-id="74e87-145">...</span><span class="sxs-lookup"><span data-stu-id="74e87-145">...</span></span>|  
  
### <a name="multiset"></a><span data-ttu-id="74e87-146">MULTISET</span><span class="sxs-lookup"><span data-stu-id="74e87-146">MULTISET</span></span>  
 <span data-ttu-id="74e87-147">[MULTISET](../../../../../../docs/framework/data/adonet/ef/language-reference/multiset-entity-sql.md) konstrukce kolekcí, jako například:</span><span class="sxs-lookup"><span data-stu-id="74e87-147">[MULTISET](../../../../../../docs/framework/data/adonet/ef/language-reference/multiset-entity-sql.md) constructs collections, such as:</span></span>  
  
 <span data-ttu-id="74e87-148">`MULTISET(1,2,2,3)` `--same as`-`{1,2,2,3}.`</span><span class="sxs-lookup"><span data-stu-id="74e87-148">`MULTISET(1,2,2,3)` `--same as`-`{1,2,2,3}.`</span></span>  
  
 <span data-ttu-id="74e87-149">Příklad:</span><span class="sxs-lookup"><span data-stu-id="74e87-149">Example:</span></span>  
  
```  
SELECT VALUE product FROM AdventureWorksEntities.Product AS product WHERE product.ListPrice IN MultiSet (125, 300)  
```  
  
 <span data-ttu-id="74e87-150">Výstup:</span><span class="sxs-lookup"><span data-stu-id="74e87-150">Output:</span></span>  
  
|<span data-ttu-id="74e87-151">ProductID</span><span class="sxs-lookup"><span data-stu-id="74e87-151">ProductID</span></span>|<span data-ttu-id="74e87-152">Název</span><span class="sxs-lookup"><span data-stu-id="74e87-152">Name</span></span>|<span data-ttu-id="74e87-153">ProductNumber</span><span class="sxs-lookup"><span data-stu-id="74e87-153">ProductNumber</span></span>|<span data-ttu-id="74e87-154">…</span><span class="sxs-lookup"><span data-stu-id="74e87-154">…</span></span>|  
|---------------|----------|-------------------|-------|  
|<span data-ttu-id="74e87-155">842</span><span class="sxs-lookup"><span data-stu-id="74e87-155">842</span></span>|<span data-ttu-id="74e87-156">Touring-Panniers, Large</span><span class="sxs-lookup"><span data-stu-id="74e87-156">Touring-Panniers, Large</span></span>|<span data-ttu-id="74e87-157">PA-T100</span><span class="sxs-lookup"><span data-stu-id="74e87-157">PA-T100</span></span>|<span data-ttu-id="74e87-158">…</span><span class="sxs-lookup"><span data-stu-id="74e87-158">…</span></span>|  
  
### <a name="object"></a><span data-ttu-id="74e87-159">Objekt</span><span class="sxs-lookup"><span data-stu-id="74e87-159">Object</span></span>  
 <span data-ttu-id="74e87-160">[Konstruktor typu s názvem](../../../../../../docs/framework/data/adonet/ef/language-reference/named-type-constructor-entity-sql.md) vytvoří (pojmenované) uživatelem definované objekty, jako například `person("abc", 12)`.</span><span class="sxs-lookup"><span data-stu-id="74e87-160">[Named Type Constructor](../../../../../../docs/framework/data/adonet/ef/language-reference/named-type-constructor-entity-sql.md) constructs (named) user-defined objects, such as `person("abc", 12)`.</span></span>  
  
 <span data-ttu-id="74e87-161">Příklad:</span><span class="sxs-lookup"><span data-stu-id="74e87-161">Example:</span></span>  
  
```  
SELECT VALUE AdventureWorksModel.SalesOrderDetail (o.SalesOrderDetailID, o.CarrierTrackingNumber, o.OrderQty,   
o.ProductID, o.SpecialOfferID, o.UnitPrice, o.UnitPriceDiscount,   
o.rowguid, o.ModifiedDate) FROM AdventureWorksEntities.SalesOrderDetail   
AS o  
```  
  
 <span data-ttu-id="74e87-162">Výstup:</span><span class="sxs-lookup"><span data-stu-id="74e87-162">Output:</span></span>  
  
|<span data-ttu-id="74e87-163">SalesOrderDetailID</span><span class="sxs-lookup"><span data-stu-id="74e87-163">SalesOrderDetailID</span></span>|<span data-ttu-id="74e87-164">CarrierTrackingNumber</span><span class="sxs-lookup"><span data-stu-id="74e87-164">CarrierTrackingNumber</span></span>|<span data-ttu-id="74e87-165">OrderQty</span><span class="sxs-lookup"><span data-stu-id="74e87-165">OrderQty</span></span>|<span data-ttu-id="74e87-166">ProductID</span><span class="sxs-lookup"><span data-stu-id="74e87-166">ProductID</span></span>|<span data-ttu-id="74e87-167">...</span><span class="sxs-lookup"><span data-stu-id="74e87-167">...</span></span>|  
|------------------------|---------------------------|--------------|---------------|---------|  
|<span data-ttu-id="74e87-168">1</span><span class="sxs-lookup"><span data-stu-id="74e87-168">1</span></span>|<span data-ttu-id="74e87-169">4911-403C-98</span><span class="sxs-lookup"><span data-stu-id="74e87-169">4911-403C-98</span></span>|<span data-ttu-id="74e87-170">1</span><span class="sxs-lookup"><span data-stu-id="74e87-170">1</span></span>|<span data-ttu-id="74e87-171">776</span><span class="sxs-lookup"><span data-stu-id="74e87-171">776</span></span>|<span data-ttu-id="74e87-172">...</span><span class="sxs-lookup"><span data-stu-id="74e87-172">...</span></span>|  
|<span data-ttu-id="74e87-173">2</span><span class="sxs-lookup"><span data-stu-id="74e87-173">2</span></span>|<span data-ttu-id="74e87-174">4911-403C-98</span><span class="sxs-lookup"><span data-stu-id="74e87-174">4911-403C-98</span></span>|<span data-ttu-id="74e87-175">3</span><span class="sxs-lookup"><span data-stu-id="74e87-175">3</span></span>|<span data-ttu-id="74e87-176">777</span><span class="sxs-lookup"><span data-stu-id="74e87-176">777</span></span>|<span data-ttu-id="74e87-177">...</span><span class="sxs-lookup"><span data-stu-id="74e87-177">...</span></span>|  
|<span data-ttu-id="74e87-178">...</span><span class="sxs-lookup"><span data-stu-id="74e87-178">...</span></span>|<span data-ttu-id="74e87-179">...</span><span class="sxs-lookup"><span data-stu-id="74e87-179">...</span></span>|<span data-ttu-id="74e87-180">...</span><span class="sxs-lookup"><span data-stu-id="74e87-180">...</span></span>|<span data-ttu-id="74e87-181">...</span><span class="sxs-lookup"><span data-stu-id="74e87-181">...</span></span>|<span data-ttu-id="74e87-182">...</span><span class="sxs-lookup"><span data-stu-id="74e87-182">...</span></span>|  
  
## <a name="references"></a><span data-ttu-id="74e87-183">Odkazy</span><span class="sxs-lookup"><span data-stu-id="74e87-183">References</span></span>  
  
### <a name="ref"></a><span data-ttu-id="74e87-184">REF</span><span class="sxs-lookup"><span data-stu-id="74e87-184">REF</span></span>  
 <span data-ttu-id="74e87-185">[REF](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md) vytvoří odkaz na instanci typu entity.</span><span class="sxs-lookup"><span data-stu-id="74e87-185">[REF](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md) creates a reference to an entity type instance.</span></span> <span data-ttu-id="74e87-186">Například následující dotaz vrátí odkazy na jednotlivé entity pořadí v sadě entit objednávky:</span><span class="sxs-lookup"><span data-stu-id="74e87-186">For example, the following query returns references to each Order entity in the Orders entity set:</span></span>  
  
```  
SELECT REF(o) AS OrderID FROM Orders AS o  
```  
  
 <span data-ttu-id="74e87-187">Výstup:</span><span class="sxs-lookup"><span data-stu-id="74e87-187">Output:</span></span>  
  
|<span data-ttu-id="74e87-188">Hodnota</span><span class="sxs-lookup"><span data-stu-id="74e87-188">Value</span></span>|  
|-----------|  
|<span data-ttu-id="74e87-189">1</span><span class="sxs-lookup"><span data-stu-id="74e87-189">1</span></span>|  
|<span data-ttu-id="74e87-190">2</span><span class="sxs-lookup"><span data-stu-id="74e87-190">2</span></span>|  
|<span data-ttu-id="74e87-191">3</span><span class="sxs-lookup"><span data-stu-id="74e87-191">3</span></span>|  
|<span data-ttu-id="74e87-192">...</span><span class="sxs-lookup"><span data-stu-id="74e87-192">...</span></span>|  
  
 <span data-ttu-id="74e87-193">Následující příklad používá vlastnost extrakce – operátor (.) pro přístup k vlastnosti entity.</span><span class="sxs-lookup"><span data-stu-id="74e87-193">The following example uses the property extraction operator (.) to access a property of an entity.</span></span> <span data-ttu-id="74e87-194">Při extrakci operátor vlastnost se používá, odkaz je automaticky přes ukazatel.</span><span class="sxs-lookup"><span data-stu-id="74e87-194">When the property extraction operator is used, the reference is automatically dereferenced.</span></span>  
  
 <span data-ttu-id="74e87-195">Příklad:</span><span class="sxs-lookup"><span data-stu-id="74e87-195">Example:</span></span>  
  
```  
SELECT VALUE REF(p).Name FROM   
    AdventureWorksEntities.Product as p  
```  
  
 <span data-ttu-id="74e87-196">Výstup:</span><span class="sxs-lookup"><span data-stu-id="74e87-196">Output:</span></span>  
  
|<span data-ttu-id="74e87-197">Hodnota</span><span class="sxs-lookup"><span data-stu-id="74e87-197">Value</span></span>|  
|-----------|  
|<span data-ttu-id="74e87-198">Měnitelné závodu</span><span class="sxs-lookup"><span data-stu-id="74e87-198">Adjustable Race</span></span>|  
|<span data-ttu-id="74e87-199">Univerzální kol samostatné</span><span class="sxs-lookup"><span data-stu-id="74e87-199">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="74e87-200">AWC Logo zakončení</span><span class="sxs-lookup"><span data-stu-id="74e87-200">AWC Logo Cap</span></span>|  
|<span data-ttu-id="74e87-201">...</span><span class="sxs-lookup"><span data-stu-id="74e87-201">...</span></span>|  
  
### <a name="deref"></a><span data-ttu-id="74e87-202">DEREF</span><span class="sxs-lookup"><span data-stu-id="74e87-202">DEREF</span></span>  
 <span data-ttu-id="74e87-203">[DEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md) přístupů přes ukazatel, hodnota odkazu a vytváří výsledek, který přístup přes ukazatel.</span><span class="sxs-lookup"><span data-stu-id="74e87-203">[DEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md) dereferences a reference value and produces the result of that dereference.</span></span> <span data-ttu-id="74e87-204">Například následující dotaz vyprodukuje entity pořadí pro každé pořadí v sadě entit objednávky: `SELECT DEREF(o2.r) FROM (SELECT REF(o) AS r FROM LOB.Orders AS o) AS o2`...</span><span class="sxs-lookup"><span data-stu-id="74e87-204">For example, the following query produces the Order entities for each Order in the Orders entity set: `SELECT DEREF(o2.r) FROM (SELECT REF(o) AS r FROM LOB.Orders AS o) AS o2`..</span></span>  
  
 <span data-ttu-id="74e87-205">Příklad:</span><span class="sxs-lookup"><span data-stu-id="74e87-205">Example:</span></span>  
  
```  
SELECT VALUE DEREF(REF(p)).Name FROM   
    AdventureWorksEntities.Product as p  
```  
  
 <span data-ttu-id="74e87-206">Výstup:</span><span class="sxs-lookup"><span data-stu-id="74e87-206">Output:</span></span>  
  
|<span data-ttu-id="74e87-207">Hodnota</span><span class="sxs-lookup"><span data-stu-id="74e87-207">Value</span></span>|  
|-----------|  
|<span data-ttu-id="74e87-208">Měnitelné závodu</span><span class="sxs-lookup"><span data-stu-id="74e87-208">Adjustable Race</span></span>|  
|<span data-ttu-id="74e87-209">Univerzální kol samostatné</span><span class="sxs-lookup"><span data-stu-id="74e87-209">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="74e87-210">AWC Logo zakončení</span><span class="sxs-lookup"><span data-stu-id="74e87-210">AWC Logo Cap</span></span>|  
|<span data-ttu-id="74e87-211">...</span><span class="sxs-lookup"><span data-stu-id="74e87-211">...</span></span>|  
  
### <a name="createref-and-key"></a><span data-ttu-id="74e87-212">CREATEREF A KLÍČ</span><span class="sxs-lookup"><span data-stu-id="74e87-212">CREATEREF AND KEY</span></span>  
 <span data-ttu-id="74e87-213">[CREATEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md) vytvoří odkaz předáním klíče.</span><span class="sxs-lookup"><span data-stu-id="74e87-213">[CREATEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md) creates a reference passing a key.</span></span> <span data-ttu-id="74e87-214">[KLÍČ](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md) extrahuje část výraz s odkaz na typ klíče.</span><span class="sxs-lookup"><span data-stu-id="74e87-214">[KEY](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md) extracts the key portion of an expression with type reference.</span></span>  
  
 <span data-ttu-id="74e87-215">Příklad:</span><span class="sxs-lookup"><span data-stu-id="74e87-215">Example:</span></span>  
  
```  
SELECT VALUE Key(CreateRef(AdventureWorksEntities.Product, row(p.ProductID)))   
    FROM AdventureWorksEntities.Product as p  
```  
  
 <span data-ttu-id="74e87-216">Výstup:</span><span class="sxs-lookup"><span data-stu-id="74e87-216">Output:</span></span>  
  
|<span data-ttu-id="74e87-217">ProductID</span><span class="sxs-lookup"><span data-stu-id="74e87-217">ProductID</span></span>|  
|---------------|  
|<span data-ttu-id="74e87-218">980</span><span class="sxs-lookup"><span data-stu-id="74e87-218">980</span></span>|  
|<span data-ttu-id="74e87-219">365</span><span class="sxs-lookup"><span data-stu-id="74e87-219">365</span></span>|  
|<span data-ttu-id="74e87-220">771</span><span class="sxs-lookup"><span data-stu-id="74e87-220">771</span></span>|  
|<span data-ttu-id="74e87-221">...</span><span class="sxs-lookup"><span data-stu-id="74e87-221">...</span></span>|  
  
## <a name="functions"></a><span data-ttu-id="74e87-222">Funkce</span><span class="sxs-lookup"><span data-stu-id="74e87-222">Functions</span></span>  
  
### <a name="canonical"></a><span data-ttu-id="74e87-223">Canonical</span><span class="sxs-lookup"><span data-stu-id="74e87-223">Canonical</span></span>  
 <span data-ttu-id="74e87-224">Obor názvů pro [kanonické funkce](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md) je Edm, stejně jako v `Edm.Length("string")`.</span><span class="sxs-lookup"><span data-stu-id="74e87-224">The namespace for [canonical functions](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md) is Edm, as in `Edm.Length("string")`.</span></span> <span data-ttu-id="74e87-225">Není nutné zadat obor názvů, pokud jiný obor názvů se importuje, který obsahuje funkce se stejným názvem jako kanonické funkce.</span><span class="sxs-lookup"><span data-stu-id="74e87-225">You do not have to specify the namespace unless another namespace is imported that contains a function with the same name as a canonical function.</span></span> <span data-ttu-id="74e87-226">Pokud dva obory názvů mají stejnou funkci, uživatel by měl konkrétní úplný název.</span><span class="sxs-lookup"><span data-stu-id="74e87-226">If two namespaces have the same function, the user should specific the full name.</span></span>  
  
 <span data-ttu-id="74e87-227">Příklad:</span><span class="sxs-lookup"><span data-stu-id="74e87-227">Example:</span></span>  
  
```  
SELECT Length(c. FirstName) As NameLen FROM   
    AdventureWorksEntities.Contact AS c   
    WHERE c.ContactID BETWEEN 10 AND 12  
```  
  
 <span data-ttu-id="74e87-228">Výstup:</span><span class="sxs-lookup"><span data-stu-id="74e87-228">Output:</span></span>  
  
|<span data-ttu-id="74e87-229">NameLen</span><span class="sxs-lookup"><span data-stu-id="74e87-229">NameLen</span></span>|  
|-------------|  
|<span data-ttu-id="74e87-230">6</span><span class="sxs-lookup"><span data-stu-id="74e87-230">6</span></span>|  
|<span data-ttu-id="74e87-231">6</span><span class="sxs-lookup"><span data-stu-id="74e87-231">6</span></span>|  
|<span data-ttu-id="74e87-232">5</span><span class="sxs-lookup"><span data-stu-id="74e87-232">5</span></span>|  
  
### <a name="microsoft-provider-specific"></a><span data-ttu-id="74e87-233">Specifické pro společnost Microsoft poskytovatele</span><span class="sxs-lookup"><span data-stu-id="74e87-233">Microsoft Provider-Specific</span></span>  
 <span data-ttu-id="74e87-234">[Funkce specifické pro zprostředkovatele Microsoft](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md) v `SqlServer` oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="74e87-234">[Microsoft provider-specific functions](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md) are in the `SqlServer` namespace.</span></span>  
  
 <span data-ttu-id="74e87-235">Příklad:</span><span class="sxs-lookup"><span data-stu-id="74e87-235">Example:</span></span>  
  
```  
SELECT SqlServer.LEN(c.EmailAddress) As EmailLen FROM   
    AdventureWorksEntities.Contact AS c WHERE   
    c.ContactID BETWEEN 10 AND 12  
```  
  
 <span data-ttu-id="74e87-236">Výstup:</span><span class="sxs-lookup"><span data-stu-id="74e87-236">Output:</span></span>  
  
|<span data-ttu-id="74e87-237">EmailLen</span><span class="sxs-lookup"><span data-stu-id="74e87-237">EmailLen</span></span>|  
|--------------|  
|<span data-ttu-id="74e87-238">27</span><span class="sxs-lookup"><span data-stu-id="74e87-238">27</span></span>|  
|<span data-ttu-id="74e87-239">27</span><span class="sxs-lookup"><span data-stu-id="74e87-239">27</span></span>|  
|<span data-ttu-id="74e87-240">26</span><span class="sxs-lookup"><span data-stu-id="74e87-240">26</span></span>|  
  
## <a name="namespaces"></a><span data-ttu-id="74e87-241">Jmenné prostory</span><span class="sxs-lookup"><span data-stu-id="74e87-241">Namespaces</span></span>  
 <span data-ttu-id="74e87-242">[POMOCÍ](../../../../../../docs/framework/data/adonet/ef/language-reference/using-entity-sql.md) určuje oborů názvů používaných ve výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="74e87-242">[USING](../../../../../../docs/framework/data/adonet/ef/language-reference/using-entity-sql.md) specifies namespaces used in a query expression.</span></span>  
  
 <span data-ttu-id="74e87-243">Příklad:</span><span class="sxs-lookup"><span data-stu-id="74e87-243">Example:</span></span>  
  
```  
using SqlServer; LOWER('AA');  
```  
  
 <span data-ttu-id="74e87-244">Výstup:</span><span class="sxs-lookup"><span data-stu-id="74e87-244">Output:</span></span>  
  
|<span data-ttu-id="74e87-245">Hodnota</span><span class="sxs-lookup"><span data-stu-id="74e87-245">Value</span></span>|  
|-----------|  
|<span data-ttu-id="74e87-246">aa</span><span class="sxs-lookup"><span data-stu-id="74e87-246">aa</span></span>|  
  
## <a name="paging"></a><span data-ttu-id="74e87-247">Stránkování</span><span class="sxs-lookup"><span data-stu-id="74e87-247">Paging</span></span>  
 <span data-ttu-id="74e87-248">Stránkování může být vyjádřena pomocí deklarace [přeskočit](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md) a [LIMIT](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md) dílčí klauzule [klauzule ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) klauzuli.</span><span class="sxs-lookup"><span data-stu-id="74e87-248">Paging can be expressed by declaring a [SKIP](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md) and [LIMIT](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md) sub-clauses to the [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) clause.</span></span>  
  
 <span data-ttu-id="74e87-249">Příklad:</span><span class="sxs-lookup"><span data-stu-id="74e87-249">Example:</span></span>  
  
```  
SELECT c.ContactID as ID, c.LastName as Name FROM   
    AdventureWorks.Contact AS c ORDER BY c.ContactID SKIP 9 LIMIT 3;  
```  
  
 <span data-ttu-id="74e87-250">Výstup:</span><span class="sxs-lookup"><span data-stu-id="74e87-250">Output:</span></span>  
  
|<span data-ttu-id="74e87-251">ID</span><span class="sxs-lookup"><span data-stu-id="74e87-251">ID</span></span>|<span data-ttu-id="74e87-252">Název</span><span class="sxs-lookup"><span data-stu-id="74e87-252">Name</span></span>|  
|--------|----------|  
|<span data-ttu-id="74e87-253">10</span><span class="sxs-lookup"><span data-stu-id="74e87-253">10</span></span>|<span data-ttu-id="74e87-254">Adina</span><span class="sxs-lookup"><span data-stu-id="74e87-254">Adina</span></span>|  
|<span data-ttu-id="74e87-255">11</span><span class="sxs-lookup"><span data-stu-id="74e87-255">11</span></span>|<span data-ttu-id="74e87-256">Agcaoili</span><span class="sxs-lookup"><span data-stu-id="74e87-256">Agcaoili</span></span>|  
|<span data-ttu-id="74e87-257">12</span><span class="sxs-lookup"><span data-stu-id="74e87-257">12</span></span>|<span data-ttu-id="74e87-258">Aguilar</span><span class="sxs-lookup"><span data-stu-id="74e87-258">Aguilar</span></span>|  
  
## <a name="grouping"></a><span data-ttu-id="74e87-259">Seskupování</span><span class="sxs-lookup"><span data-stu-id="74e87-259">Grouping</span></span>  
 <span data-ttu-id="74e87-260">[SESKUPENÍ podle](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md) Určuje skupiny, do které objektů vrácených dotazem ([vyberte](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)) výrazu mají být umístěny.</span><span class="sxs-lookup"><span data-stu-id="74e87-260">[GROUPING BY](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md) specifies groups into which objects returned by a query ([SELECT](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)) expression are to be placed.</span></span>  
  
 <span data-ttu-id="74e87-261">Příklad:</span><span class="sxs-lookup"><span data-stu-id="74e87-261">Example:</span></span>  
  
```  
SELECT VALUE name FROM AdventureWorksEntities.Product as P   
    GROUP BY P.Name HAVING MAX(P.ListPrice) > 5  
```  
  
 <span data-ttu-id="74e87-262">Výstup:</span><span class="sxs-lookup"><span data-stu-id="74e87-262">Output:</span></span>  
  
|<span data-ttu-id="74e87-263">name</span><span class="sxs-lookup"><span data-stu-id="74e87-263">name</span></span>|  
|----------|  
|<span data-ttu-id="74e87-264">Sestavení místo LL Horská oblast</span><span class="sxs-lookup"><span data-stu-id="74e87-264">LL Mountain Seat Assembly</span></span>|  
|<span data-ttu-id="74e87-265">Sestavení licence ML Horská oblast</span><span class="sxs-lookup"><span data-stu-id="74e87-265">ML Mountain Seat Assembly</span></span>|  
|<span data-ttu-id="74e87-266">HL Mountain místo sestavení</span><span class="sxs-lookup"><span data-stu-id="74e87-266">HL Mountain Seat Assembly</span></span>|  
|<span data-ttu-id="74e87-267">...</span><span class="sxs-lookup"><span data-stu-id="74e87-267">...</span></span>|  
  
## <a name="navigation"></a><span data-ttu-id="74e87-268">Navigace</span><span class="sxs-lookup"><span data-stu-id="74e87-268">Navigation</span></span>  
 <span data-ttu-id="74e87-269">Operátor navigace vztah umožňuje přejít nad vztah z entit (od konce) do jiného (Chcete-li ukončit).</span><span class="sxs-lookup"><span data-stu-id="74e87-269">The relationship navigation operator allows you to navigate over the relationship from one entity (from end) to another (to end).</span></span> <span data-ttu-id="74e87-270">[NAVIGOVAT](../../../../../../docs/framework/data/adonet/ef/language-reference/navigate-entity-sql.md) přijímá typ vztahu kvalifikovány jako \<oboru názvů >.\< Název typu vztahu >.</span><span class="sxs-lookup"><span data-stu-id="74e87-270">[NAVIGATE](../../../../../../docs/framework/data/adonet/ef/language-reference/navigate-entity-sql.md) takes the relationship type qualified as \<namespace>.\<relationship type name>.</span></span> <span data-ttu-id="74e87-271">Přejděte vrátí Ref\<T > Pokud Kardinalita do konce je 1.</span><span class="sxs-lookup"><span data-stu-id="74e87-271">Navigate returns Ref\<T> if the cardinality of the to end is 1.</span></span> <span data-ttu-id="74e87-272">Pokud Kardinalita do konce je n, kolekce < Ref\<T >> bude vrácen.</span><span class="sxs-lookup"><span data-stu-id="74e87-272">If the cardinality of the to end is n, the Collection<Ref\<T>> will be returned.</span></span>  
  
 <span data-ttu-id="74e87-273">Příklad:</span><span class="sxs-lookup"><span data-stu-id="74e87-273">Example:</span></span>  
  
```  
SELECT a.AddressID, (SELECT VALUE DEREF(v) FROM   
    NAVIGATE(a, AdventureWorksModel.FK_SalesOrderHeader_Address_BillToAddressID) AS v)   
    FROM AdventureWorksEntities.Address AS a  
```  
  
 <span data-ttu-id="74e87-274">Výstup:</span><span class="sxs-lookup"><span data-stu-id="74e87-274">Output:</span></span>  
  
|<span data-ttu-id="74e87-275">AddressID</span><span class="sxs-lookup"><span data-stu-id="74e87-275">AddressID</span></span>|  
|---------------|  
|<span data-ttu-id="74e87-276">1</span><span class="sxs-lookup"><span data-stu-id="74e87-276">1</span></span>|  
|<span data-ttu-id="74e87-277">2</span><span class="sxs-lookup"><span data-stu-id="74e87-277">2</span></span>|  
|<span data-ttu-id="74e87-278">3</span><span class="sxs-lookup"><span data-stu-id="74e87-278">3</span></span>|  
|<span data-ttu-id="74e87-279">...</span><span class="sxs-lookup"><span data-stu-id="74e87-279">...</span></span>|  
  
## <a name="select-value-and-select"></a><span data-ttu-id="74e87-280">VYBERTE HODNOTU A VYBERTE</span><span class="sxs-lookup"><span data-stu-id="74e87-280">SELECT VALUE AND SELECT</span></span>  
  
### <a name="select-value"></a><span data-ttu-id="74e87-281">VYBERTE HODNOTU</span><span class="sxs-lookup"><span data-stu-id="74e87-281">SELECT VALUE</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="74e87-282">poskytuje klauzule SELECT VALUE pro přeskočení konstrukce implicitní řádek.</span><span class="sxs-lookup"><span data-stu-id="74e87-282">provides the SELECT VALUE clause to skip the implicit row construction.</span></span> <span data-ttu-id="74e87-283">V klauzuli SELECT VALUE lze zadat pouze jednu položku.</span><span class="sxs-lookup"><span data-stu-id="74e87-283">Only one item can be specified in a SELECT VALUE clause.</span></span> <span data-ttu-id="74e87-284">Při těchto klauzulí se používá, je vytvořen žádný řádek obálku kolem položek v klauzuli SELECT a kolekce na požadovaný tvar je možné vytvořit, například: `SELECT VALUE a`.</span><span class="sxs-lookup"><span data-stu-id="74e87-284">When such a clause is used, no row wrapper is constructed around the items in the SELECT clause, and a collection of the desired shape can be produced, for example: `SELECT VALUE a`.</span></span>  
  
 <span data-ttu-id="74e87-285">Příklad:</span><span class="sxs-lookup"><span data-stu-id="74e87-285">Example:</span></span>  
  
```  
SELECT VALUE p.Name FROM AdventureWorksEntities.Product as p  
```  
  
 <span data-ttu-id="74e87-286">Výstup:</span><span class="sxs-lookup"><span data-stu-id="74e87-286">Output:</span></span>  
  
|<span data-ttu-id="74e87-287">Název</span><span class="sxs-lookup"><span data-stu-id="74e87-287">Name</span></span>|  
|----------|  
|<span data-ttu-id="74e87-288">Měnitelné závodu</span><span class="sxs-lookup"><span data-stu-id="74e87-288">Adjustable Race</span></span>|  
|<span data-ttu-id="74e87-289">Univerzální kol samostatné</span><span class="sxs-lookup"><span data-stu-id="74e87-289">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="74e87-290">AWC Logo zakončení</span><span class="sxs-lookup"><span data-stu-id="74e87-290">AWC Logo Cap</span></span>|  
|<span data-ttu-id="74e87-291">...</span><span class="sxs-lookup"><span data-stu-id="74e87-291">...</span></span>|  
  
### <a name="select"></a><span data-ttu-id="74e87-292">SELECT</span><span class="sxs-lookup"><span data-stu-id="74e87-292">SELECT</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="74e87-293">také poskytuje konstruktoru řádku k vytvoření libovolné řádky.</span><span class="sxs-lookup"><span data-stu-id="74e87-293">also provides the row constructor to construct arbitrary rows.</span></span> <span data-ttu-id="74e87-294">Vyberte použije jeden nebo více prvků v projekci a výsledky datového záznamu vložením polí, například: `SELECT a, b, c`.</span><span class="sxs-lookup"><span data-stu-id="74e87-294">SELECT takes one or more elements in the projection and results in a data record with fields, for example: `SELECT a, b, c`.</span></span>  
  
 <span data-ttu-id="74e87-295">Příklad:</span><span class="sxs-lookup"><span data-stu-id="74e87-295">Example:</span></span>  
  
 <span data-ttu-id="74e87-296">Vyberte p.Name, p.ProductID z AdventureWorksEntities.Product jako p výstup:</span><span class="sxs-lookup"><span data-stu-id="74e87-296">SELECT p.Name, p.ProductID FROM AdventureWorksEntities.Product as p Output:</span></span>  
  
|<span data-ttu-id="74e87-297">Název</span><span class="sxs-lookup"><span data-stu-id="74e87-297">Name</span></span>|<span data-ttu-id="74e87-298">ProductID</span><span class="sxs-lookup"><span data-stu-id="74e87-298">ProductID</span></span>|  
|----------|---------------|  
|<span data-ttu-id="74e87-299">Měnitelné závodu</span><span class="sxs-lookup"><span data-stu-id="74e87-299">Adjustable Race</span></span>|<span data-ttu-id="74e87-300">1</span><span class="sxs-lookup"><span data-stu-id="74e87-300">1</span></span>|  
|<span data-ttu-id="74e87-301">Univerzální kol samostatné</span><span class="sxs-lookup"><span data-stu-id="74e87-301">All-Purpose Bike Stand</span></span>|<span data-ttu-id="74e87-302">879</span><span class="sxs-lookup"><span data-stu-id="74e87-302">879</span></span>|  
|<span data-ttu-id="74e87-303">AWC Logo zakončení</span><span class="sxs-lookup"><span data-stu-id="74e87-303">AWC Logo Cap</span></span>|<span data-ttu-id="74e87-304">712</span><span class="sxs-lookup"><span data-stu-id="74e87-304">712</span></span>|  
|<span data-ttu-id="74e87-305">...</span><span class="sxs-lookup"><span data-stu-id="74e87-305">...</span></span>|<span data-ttu-id="74e87-306">...</span><span class="sxs-lookup"><span data-stu-id="74e87-306">...</span></span>|  
  
## <a name="case-expression"></a><span data-ttu-id="74e87-307">VÝRAZ CASE</span><span class="sxs-lookup"><span data-stu-id="74e87-307">CASE EXPRESSION</span></span>  
 <span data-ttu-id="74e87-308">[Výraz malá a velká](../../../../../../docs/framework/data/adonet/ef/language-reference/case-entity-sql.md) vyhodnotí sadu logických výrazů k určení výsledků.</span><span class="sxs-lookup"><span data-stu-id="74e87-308">The [case expression](../../../../../../docs/framework/data/adonet/ef/language-reference/case-entity-sql.md) evaluates a set of Boolean expressions to determine the result.</span></span>  
  
 <span data-ttu-id="74e87-309">Příklad:</span><span class="sxs-lookup"><span data-stu-id="74e87-309">Example:</span></span>  
  
```  
CASE WHEN AVG({25,12,11}) < 100 THEN TRUE ELSE FALSE END  
```  
  
 <span data-ttu-id="74e87-310">Výstup:</span><span class="sxs-lookup"><span data-stu-id="74e87-310">Output:</span></span>  
  
|<span data-ttu-id="74e87-311">Hodnota</span><span class="sxs-lookup"><span data-stu-id="74e87-311">Value</span></span>|  
|-----------|  
|<span data-ttu-id="74e87-312">HODNOTA TRUE</span><span class="sxs-lookup"><span data-stu-id="74e87-312">TRUE</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="74e87-313">Viz také:</span><span class="sxs-lookup"><span data-stu-id="74e87-313">See also</span></span>
- [<span data-ttu-id="74e87-314">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="74e87-314">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [<span data-ttu-id="74e87-315">Přehled Entity SQL</span><span class="sxs-lookup"><span data-stu-id="74e87-315">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
