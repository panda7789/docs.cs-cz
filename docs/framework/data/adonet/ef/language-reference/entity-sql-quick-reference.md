---
title: Stručné reference k Entity SQL
ms.date: 03/30/2017
ms.assetid: e53dad9e-5e83-426e-abb4-be3e78e3d6dc
ms.openlocfilehash: b4e3eaf8abd82b63fa2663b47f878ecfa9584897
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59207068"
---
# <a name="entity-sql-quick-reference"></a><span data-ttu-id="6a078-102">Stručné reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="6a078-102">Entity SQL Quick Reference</span></span>
<span data-ttu-id="6a078-103">Toto téma poskytuje rychlý odkaz na [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dotazy.</span><span class="sxs-lookup"><span data-stu-id="6a078-103">This topic provides a quick reference to [!INCLUDE[esql](../../../../../../includes/esql-md.md)] queries.</span></span> <span data-ttu-id="6a078-104">Dotazy v tomto tématu jsou založeny na modelu AdventureWorks Sales.</span><span class="sxs-lookup"><span data-stu-id="6a078-104">The queries in this topic are based on the AdventureWorks Sales model.</span></span>  
  
## <a name="literals"></a><span data-ttu-id="6a078-105">Literály</span><span class="sxs-lookup"><span data-stu-id="6a078-105">Literals</span></span>  
  
### <a name="string"></a><span data-ttu-id="6a078-106">String</span><span class="sxs-lookup"><span data-stu-id="6a078-106">String</span></span>  
 <span data-ttu-id="6a078-107">Existují řetězcové literály znaků Unicode a kódování Unicode.</span><span class="sxs-lookup"><span data-stu-id="6a078-107">There are Unicode and non-Unicode character string literals.</span></span> <span data-ttu-id="6a078-108">Řetězce Unicode jsou předponou N. Například `N'hello'`.</span><span class="sxs-lookup"><span data-stu-id="6a078-108">Unicode strings are prepended with N. For example, `N'hello'`.</span></span>  
  
 <span data-ttu-id="6a078-109">Následuje příklad Non-Unicode řetězcového literálu:</span><span class="sxs-lookup"><span data-stu-id="6a078-109">The following is an example of a Non-Unicode string literal:</span></span>  
  
```  
'hello'  
--same as  
"hello"  
```  
  
 <span data-ttu-id="6a078-110">Výstup:</span><span class="sxs-lookup"><span data-stu-id="6a078-110">Output:</span></span>  
  
|<span data-ttu-id="6a078-111">Value</span><span class="sxs-lookup"><span data-stu-id="6a078-111">Value</span></span>|  
|-----------|  
|<span data-ttu-id="6a078-112">Dobrý den</span><span class="sxs-lookup"><span data-stu-id="6a078-112">hello</span></span>|  
  
### <a name="datetime"></a><span data-ttu-id="6a078-113">DateTime</span><span class="sxs-lookup"><span data-stu-id="6a078-113">DateTime</span></span>  
 <span data-ttu-id="6a078-114">V literálech datum a čas datum a čas části jsou povinné.</span><span class="sxs-lookup"><span data-stu-id="6a078-114">In DateTime literals, both date and time parts are mandatory.</span></span> <span data-ttu-id="6a078-115">Neexistují žádné výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="6a078-115">There are no default values.</span></span>  
  
 <span data-ttu-id="6a078-116">Příklad:</span><span class="sxs-lookup"><span data-stu-id="6a078-116">Example:</span></span>  
  
```  
DATETIME '2006-12-25 01:01:00.000'   
--same as  
DATETIME '2006-12-25 01:01'  
```  
  
 <span data-ttu-id="6a078-117">Výstup:</span><span class="sxs-lookup"><span data-stu-id="6a078-117">Output:</span></span>  
  
|<span data-ttu-id="6a078-118">Hodnota</span><span class="sxs-lookup"><span data-stu-id="6a078-118">Value</span></span>|  
|-----------|  
|<span data-ttu-id="6a078-119">12/25/2006 1:01:00: 00</span><span class="sxs-lookup"><span data-stu-id="6a078-119">12/25/2006 1:01:00 AM</span></span>|  
  
### <a name="integer"></a><span data-ttu-id="6a078-120">Integer</span><span class="sxs-lookup"><span data-stu-id="6a078-120">Integer</span></span>  
 <span data-ttu-id="6a078-121">Literály celých čísel může být typu Int32 (123), UInt32 (123U), Int64 (123L) a UInt64 (123UL).</span><span class="sxs-lookup"><span data-stu-id="6a078-121">Integer literals can be of type Int32 (123), UInt32 (123U), Int64 (123L), and UInt64 (123UL).</span></span>  
  
 <span data-ttu-id="6a078-122">Příklad:</span><span class="sxs-lookup"><span data-stu-id="6a078-122">Example:</span></span>  
  
```  
--a collection of integers  
{1, 2, 3}  
```  
  
 <span data-ttu-id="6a078-123">Výstup:</span><span class="sxs-lookup"><span data-stu-id="6a078-123">Output:</span></span>  
  
|<span data-ttu-id="6a078-124">Value</span><span class="sxs-lookup"><span data-stu-id="6a078-124">Value</span></span>|  
|-----------|  
|<span data-ttu-id="6a078-125">1</span><span class="sxs-lookup"><span data-stu-id="6a078-125">1</span></span>|  
|<span data-ttu-id="6a078-126">2</span><span class="sxs-lookup"><span data-stu-id="6a078-126">2</span></span>|  
|<span data-ttu-id="6a078-127">3</span><span class="sxs-lookup"><span data-stu-id="6a078-127">3</span></span>|  
  
### <a name="other"></a><span data-ttu-id="6a078-128">Ostatní</span><span class="sxs-lookup"><span data-stu-id="6a078-128">Other</span></span>  
 <span data-ttu-id="6a078-129">Ostatní literály, které podporuje [!INCLUDE[esql](../../../../../../includes/esql-md.md)] jsou identifikátor Guid, binární soubor, Float nebo Double, Decimal, a `null`.</span><span class="sxs-lookup"><span data-stu-id="6a078-129">Other literals supported by [!INCLUDE[esql](../../../../../../includes/esql-md.md)] are Guid, Binary, Float/Double, Decimal, and `null`.</span></span> <span data-ttu-id="6a078-130">Hodnota Null, literály v [!INCLUDE[esql](../../../../../../includes/esql-md.md)] jsou považovány za kompatibilní se každý jiný typ v konceptuálním modelu.</span><span class="sxs-lookup"><span data-stu-id="6a078-130">Null literals in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] are considered to be compatible with every other type in the conceptual model.</span></span>  
  
## <a name="type-constructors"></a><span data-ttu-id="6a078-131">Konstruktory typu</span><span class="sxs-lookup"><span data-stu-id="6a078-131">Type Constructors</span></span>  
  
### <a name="row"></a><span data-ttu-id="6a078-132">ROW</span><span class="sxs-lookup"><span data-stu-id="6a078-132">ROW</span></span>  
 <span data-ttu-id="6a078-133">[ŘÁDEK](../../../../../../docs/framework/data/adonet/ef/language-reference/row-entity-sql.md) vytvoří anonymní, typované strukturálně (záznamů) hodnotu jako v:</span><span class="sxs-lookup"><span data-stu-id="6a078-133">[ROW](../../../../../../docs/framework/data/adonet/ef/language-reference/row-entity-sql.md) constructs an anonymous, structurally-typed (record) value as in:</span></span> `ROW(1 AS myNumber, ‘Name’ AS myName).`  
  
 <span data-ttu-id="6a078-134">Příklad:</span><span class="sxs-lookup"><span data-stu-id="6a078-134">Example:</span></span>  
  
```  
SELECT VALUE row (product.ProductID as ProductID, product.Name   
    as ProductName) FROM AdventureWorksEntities.Product AS product  
```  
  
 <span data-ttu-id="6a078-135">Výstup:</span><span class="sxs-lookup"><span data-stu-id="6a078-135">Output:</span></span>  
  
|<span data-ttu-id="6a078-136">ProductID</span><span class="sxs-lookup"><span data-stu-id="6a078-136">ProductID</span></span>|<span data-ttu-id="6a078-137">Name</span><span class="sxs-lookup"><span data-stu-id="6a078-137">Name</span></span>|  
|---------------|----------|  
|<span data-ttu-id="6a078-138">1</span><span class="sxs-lookup"><span data-stu-id="6a078-138">1</span></span>|<span data-ttu-id="6a078-139">Měnitelné závodu</span><span class="sxs-lookup"><span data-stu-id="6a078-139">Adjustable Race</span></span>|  
|<span data-ttu-id="6a078-140">879</span><span class="sxs-lookup"><span data-stu-id="6a078-140">879</span></span>|<span data-ttu-id="6a078-141">Univerzální kol samostatné</span><span class="sxs-lookup"><span data-stu-id="6a078-141">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="6a078-142">712</span><span class="sxs-lookup"><span data-stu-id="6a078-142">712</span></span>|<span data-ttu-id="6a078-143">AWC Logo zakončení</span><span class="sxs-lookup"><span data-stu-id="6a078-143">AWC Logo Cap</span></span>|  
|<span data-ttu-id="6a078-144">...</span><span class="sxs-lookup"><span data-stu-id="6a078-144">...</span></span>|<span data-ttu-id="6a078-145">...</span><span class="sxs-lookup"><span data-stu-id="6a078-145">...</span></span>|  
  
### <a name="multiset"></a><span data-ttu-id="6a078-146">MULTISET</span><span class="sxs-lookup"><span data-stu-id="6a078-146">MULTISET</span></span>  
 <span data-ttu-id="6a078-147">[MULTISET](../../../../../../docs/framework/data/adonet/ef/language-reference/multiset-entity-sql.md) konstrukce kolekcí, jako například:</span><span class="sxs-lookup"><span data-stu-id="6a078-147">[MULTISET](../../../../../../docs/framework/data/adonet/ef/language-reference/multiset-entity-sql.md) constructs collections, such as:</span></span>  
  
 `MULTISET(1,2,2,3)` `--same as`-`{1,2,2,3}.`  
  
 <span data-ttu-id="6a078-148">Příklad:</span><span class="sxs-lookup"><span data-stu-id="6a078-148">Example:</span></span>  
  
```  
SELECT VALUE product FROM AdventureWorksEntities.Product AS product WHERE product.ListPrice IN MultiSet (125, 300)  
```  
  
 <span data-ttu-id="6a078-149">Výstup:</span><span class="sxs-lookup"><span data-stu-id="6a078-149">Output:</span></span>  
  
|<span data-ttu-id="6a078-150">ProductID</span><span class="sxs-lookup"><span data-stu-id="6a078-150">ProductID</span></span>|<span data-ttu-id="6a078-151">Název</span><span class="sxs-lookup"><span data-stu-id="6a078-151">Name</span></span>|<span data-ttu-id="6a078-152">ProductNumber</span><span class="sxs-lookup"><span data-stu-id="6a078-152">ProductNumber</span></span>|<span data-ttu-id="6a078-153">…</span><span class="sxs-lookup"><span data-stu-id="6a078-153">…</span></span>|  
|---------------|----------|-------------------|-------|  
|<span data-ttu-id="6a078-154">842</span><span class="sxs-lookup"><span data-stu-id="6a078-154">842</span></span>|<span data-ttu-id="6a078-155">Touring-Panniers, Large</span><span class="sxs-lookup"><span data-stu-id="6a078-155">Touring-Panniers, Large</span></span>|<span data-ttu-id="6a078-156">PA-T100</span><span class="sxs-lookup"><span data-stu-id="6a078-156">PA-T100</span></span>|<span data-ttu-id="6a078-157">…</span><span class="sxs-lookup"><span data-stu-id="6a078-157">…</span></span>|  
  
### <a name="object"></a><span data-ttu-id="6a078-158">Objekt</span><span class="sxs-lookup"><span data-stu-id="6a078-158">Object</span></span>  
 <span data-ttu-id="6a078-159">[Konstruktor typu s názvem](../../../../../../docs/framework/data/adonet/ef/language-reference/named-type-constructor-entity-sql.md) vytvoří (pojmenované) uživatelem definované objekty, jako například `person("abc", 12)`.</span><span class="sxs-lookup"><span data-stu-id="6a078-159">[Named Type Constructor](../../../../../../docs/framework/data/adonet/ef/language-reference/named-type-constructor-entity-sql.md) constructs (named) user-defined objects, such as `person("abc", 12)`.</span></span>  
  
 <span data-ttu-id="6a078-160">Příklad:</span><span class="sxs-lookup"><span data-stu-id="6a078-160">Example:</span></span>  
  
```  
SELECT VALUE AdventureWorksModel.SalesOrderDetail (o.SalesOrderDetailID, o.CarrierTrackingNumber, o.OrderQty,   
o.ProductID, o.SpecialOfferID, o.UnitPrice, o.UnitPriceDiscount,   
o.rowguid, o.ModifiedDate) FROM AdventureWorksEntities.SalesOrderDetail   
AS o  
```  
  
 <span data-ttu-id="6a078-161">Výstup:</span><span class="sxs-lookup"><span data-stu-id="6a078-161">Output:</span></span>  
  
|<span data-ttu-id="6a078-162">SalesOrderDetailID</span><span class="sxs-lookup"><span data-stu-id="6a078-162">SalesOrderDetailID</span></span>|<span data-ttu-id="6a078-163">CarrierTrackingNumber</span><span class="sxs-lookup"><span data-stu-id="6a078-163">CarrierTrackingNumber</span></span>|<span data-ttu-id="6a078-164">OrderQty</span><span class="sxs-lookup"><span data-stu-id="6a078-164">OrderQty</span></span>|<span data-ttu-id="6a078-165">ProductID</span><span class="sxs-lookup"><span data-stu-id="6a078-165">ProductID</span></span>|<span data-ttu-id="6a078-166">...</span><span class="sxs-lookup"><span data-stu-id="6a078-166">...</span></span>|  
|------------------------|---------------------------|--------------|---------------|---------|  
|<span data-ttu-id="6a078-167">1</span><span class="sxs-lookup"><span data-stu-id="6a078-167">1</span></span>|<span data-ttu-id="6a078-168">4911-403C-98</span><span class="sxs-lookup"><span data-stu-id="6a078-168">4911-403C-98</span></span>|<span data-ttu-id="6a078-169">1</span><span class="sxs-lookup"><span data-stu-id="6a078-169">1</span></span>|<span data-ttu-id="6a078-170">776</span><span class="sxs-lookup"><span data-stu-id="6a078-170">776</span></span>|<span data-ttu-id="6a078-171">...</span><span class="sxs-lookup"><span data-stu-id="6a078-171">...</span></span>|  
|<span data-ttu-id="6a078-172">2</span><span class="sxs-lookup"><span data-stu-id="6a078-172">2</span></span>|<span data-ttu-id="6a078-173">4911-403C-98</span><span class="sxs-lookup"><span data-stu-id="6a078-173">4911-403C-98</span></span>|<span data-ttu-id="6a078-174">3</span><span class="sxs-lookup"><span data-stu-id="6a078-174">3</span></span>|<span data-ttu-id="6a078-175">777</span><span class="sxs-lookup"><span data-stu-id="6a078-175">777</span></span>|<span data-ttu-id="6a078-176">...</span><span class="sxs-lookup"><span data-stu-id="6a078-176">...</span></span>|  
|<span data-ttu-id="6a078-177">...</span><span class="sxs-lookup"><span data-stu-id="6a078-177">...</span></span>|<span data-ttu-id="6a078-178">...</span><span class="sxs-lookup"><span data-stu-id="6a078-178">...</span></span>|<span data-ttu-id="6a078-179">...</span><span class="sxs-lookup"><span data-stu-id="6a078-179">...</span></span>|<span data-ttu-id="6a078-180">...</span><span class="sxs-lookup"><span data-stu-id="6a078-180">...</span></span>|<span data-ttu-id="6a078-181">...</span><span class="sxs-lookup"><span data-stu-id="6a078-181">...</span></span>|  
  
## <a name="references"></a><span data-ttu-id="6a078-182">Odkazy</span><span class="sxs-lookup"><span data-stu-id="6a078-182">References</span></span>  
  
### <a name="ref"></a><span data-ttu-id="6a078-183">REF</span><span class="sxs-lookup"><span data-stu-id="6a078-183">REF</span></span>  
 <span data-ttu-id="6a078-184">[REF](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md) vytvoří odkaz na instanci typu entity.</span><span class="sxs-lookup"><span data-stu-id="6a078-184">[REF](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md) creates a reference to an entity type instance.</span></span> <span data-ttu-id="6a078-185">Například následující dotaz vrátí odkazy na jednotlivé entity pořadí v sadě entit objednávky:</span><span class="sxs-lookup"><span data-stu-id="6a078-185">For example, the following query returns references to each Order entity in the Orders entity set:</span></span>  
  
```  
SELECT REF(o) AS OrderID FROM Orders AS o  
```  
  
 <span data-ttu-id="6a078-186">Výstup:</span><span class="sxs-lookup"><span data-stu-id="6a078-186">Output:</span></span>  
  
|<span data-ttu-id="6a078-187">Hodnota</span><span class="sxs-lookup"><span data-stu-id="6a078-187">Value</span></span>|  
|-----------|  
|<span data-ttu-id="6a078-188">1</span><span class="sxs-lookup"><span data-stu-id="6a078-188">1</span></span>|  
|<span data-ttu-id="6a078-189">2</span><span class="sxs-lookup"><span data-stu-id="6a078-189">2</span></span>|  
|<span data-ttu-id="6a078-190">3</span><span class="sxs-lookup"><span data-stu-id="6a078-190">3</span></span>|  
|<span data-ttu-id="6a078-191">...</span><span class="sxs-lookup"><span data-stu-id="6a078-191">...</span></span>|  
  
 <span data-ttu-id="6a078-192">Následující příklad používá vlastnost extrakce – operátor (.) pro přístup k vlastnosti entity.</span><span class="sxs-lookup"><span data-stu-id="6a078-192">The following example uses the property extraction operator (.) to access a property of an entity.</span></span> <span data-ttu-id="6a078-193">Při extrakci operátor vlastnost se používá, odkaz je automaticky přes ukazatel.</span><span class="sxs-lookup"><span data-stu-id="6a078-193">When the property extraction operator is used, the reference is automatically dereferenced.</span></span>  
  
 <span data-ttu-id="6a078-194">Příklad:</span><span class="sxs-lookup"><span data-stu-id="6a078-194">Example:</span></span>  
  
```  
SELECT VALUE REF(p).Name FROM   
    AdventureWorksEntities.Product as p  
```  
  
 <span data-ttu-id="6a078-195">Výstup:</span><span class="sxs-lookup"><span data-stu-id="6a078-195">Output:</span></span>  
  
|<span data-ttu-id="6a078-196">Value</span><span class="sxs-lookup"><span data-stu-id="6a078-196">Value</span></span>|  
|-----------|  
|<span data-ttu-id="6a078-197">Měnitelné závodu</span><span class="sxs-lookup"><span data-stu-id="6a078-197">Adjustable Race</span></span>|  
|<span data-ttu-id="6a078-198">Univerzální kol samostatné</span><span class="sxs-lookup"><span data-stu-id="6a078-198">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="6a078-199">AWC Logo zakončení</span><span class="sxs-lookup"><span data-stu-id="6a078-199">AWC Logo Cap</span></span>|  
|<span data-ttu-id="6a078-200">...</span><span class="sxs-lookup"><span data-stu-id="6a078-200">...</span></span>|  
  
### <a name="deref"></a><span data-ttu-id="6a078-201">DEREF</span><span class="sxs-lookup"><span data-stu-id="6a078-201">DEREF</span></span>  
 <span data-ttu-id="6a078-202">[DEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md) přístupů přes ukazatel, hodnota odkazu a vytváří výsledek, který přístup přes ukazatel.</span><span class="sxs-lookup"><span data-stu-id="6a078-202">[DEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md) dereferences a reference value and produces the result of that dereference.</span></span> <span data-ttu-id="6a078-203">Například následující dotaz vyprodukuje entity pořadí pro každé pořadí v sadě entit objednávky: `SELECT DEREF(o2.r) FROM (SELECT REF(o) AS r FROM LOB.Orders AS o) AS o2`...</span><span class="sxs-lookup"><span data-stu-id="6a078-203">For example, the following query produces the Order entities for each Order in the Orders entity set: `SELECT DEREF(o2.r) FROM (SELECT REF(o) AS r FROM LOB.Orders AS o) AS o2`..</span></span>  
  
 <span data-ttu-id="6a078-204">Příklad:</span><span class="sxs-lookup"><span data-stu-id="6a078-204">Example:</span></span>  
  
```  
SELECT VALUE DEREF(REF(p)).Name FROM   
    AdventureWorksEntities.Product as p  
```  
  
 <span data-ttu-id="6a078-205">Výstup:</span><span class="sxs-lookup"><span data-stu-id="6a078-205">Output:</span></span>  
  
|<span data-ttu-id="6a078-206">Value</span><span class="sxs-lookup"><span data-stu-id="6a078-206">Value</span></span>|  
|-----------|  
|<span data-ttu-id="6a078-207">Měnitelné závodu</span><span class="sxs-lookup"><span data-stu-id="6a078-207">Adjustable Race</span></span>|  
|<span data-ttu-id="6a078-208">Univerzální kol samostatné</span><span class="sxs-lookup"><span data-stu-id="6a078-208">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="6a078-209">AWC Logo zakončení</span><span class="sxs-lookup"><span data-stu-id="6a078-209">AWC Logo Cap</span></span>|  
|<span data-ttu-id="6a078-210">...</span><span class="sxs-lookup"><span data-stu-id="6a078-210">...</span></span>|  
  
### <a name="createref-and-key"></a><span data-ttu-id="6a078-211">CREATEREF A KLÍČ</span><span class="sxs-lookup"><span data-stu-id="6a078-211">CREATEREF AND KEY</span></span>  
 <span data-ttu-id="6a078-212">[CREATEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md) vytvoří odkaz předáním klíče.</span><span class="sxs-lookup"><span data-stu-id="6a078-212">[CREATEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md) creates a reference passing a key.</span></span> <span data-ttu-id="6a078-213">[KLÍČ](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md) extrahuje část výraz s odkaz na typ klíče.</span><span class="sxs-lookup"><span data-stu-id="6a078-213">[KEY](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md) extracts the key portion of an expression with type reference.</span></span>  
  
 <span data-ttu-id="6a078-214">Příklad:</span><span class="sxs-lookup"><span data-stu-id="6a078-214">Example:</span></span>  
  
```  
SELECT VALUE Key(CreateRef(AdventureWorksEntities.Product, row(p.ProductID)))   
    FROM AdventureWorksEntities.Product as p  
```  
  
 <span data-ttu-id="6a078-215">Výstup:</span><span class="sxs-lookup"><span data-stu-id="6a078-215">Output:</span></span>  
  
|<span data-ttu-id="6a078-216">ProductID</span><span class="sxs-lookup"><span data-stu-id="6a078-216">ProductID</span></span>|  
|---------------|  
|<span data-ttu-id="6a078-217">980</span><span class="sxs-lookup"><span data-stu-id="6a078-217">980</span></span>|  
|<span data-ttu-id="6a078-218">365</span><span class="sxs-lookup"><span data-stu-id="6a078-218">365</span></span>|  
|<span data-ttu-id="6a078-219">771</span><span class="sxs-lookup"><span data-stu-id="6a078-219">771</span></span>|  
|<span data-ttu-id="6a078-220">...</span><span class="sxs-lookup"><span data-stu-id="6a078-220">...</span></span>|  
  
## <a name="functions"></a><span data-ttu-id="6a078-221">Funkce</span><span class="sxs-lookup"><span data-stu-id="6a078-221">Functions</span></span>  
  
### <a name="canonical"></a><span data-ttu-id="6a078-222">Canonical</span><span class="sxs-lookup"><span data-stu-id="6a078-222">Canonical</span></span>  
 <span data-ttu-id="6a078-223">Obor názvů pro [kanonické funkce](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md) je Edm, stejně jako v `Edm.Length("string")`.</span><span class="sxs-lookup"><span data-stu-id="6a078-223">The namespace for [canonical functions](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md) is Edm, as in `Edm.Length("string")`.</span></span> <span data-ttu-id="6a078-224">Není nutné zadat obor názvů, pokud jiný obor názvů se importuje, který obsahuje funkce se stejným názvem jako kanonické funkce.</span><span class="sxs-lookup"><span data-stu-id="6a078-224">You do not have to specify the namespace unless another namespace is imported that contains a function with the same name as a canonical function.</span></span> <span data-ttu-id="6a078-225">Pokud dva obory názvů mají stejnou funkci, uživatel by měl konkrétní úplný název.</span><span class="sxs-lookup"><span data-stu-id="6a078-225">If two namespaces have the same function, the user should specific the full name.</span></span>  
  
 <span data-ttu-id="6a078-226">Příklad:</span><span class="sxs-lookup"><span data-stu-id="6a078-226">Example:</span></span>  
  
```  
SELECT Length(c. FirstName) As NameLen FROM   
    AdventureWorksEntities.Contact AS c   
    WHERE c.ContactID BETWEEN 10 AND 12  
```  
  
 <span data-ttu-id="6a078-227">Výstup:</span><span class="sxs-lookup"><span data-stu-id="6a078-227">Output:</span></span>  
  
|<span data-ttu-id="6a078-228">NameLen</span><span class="sxs-lookup"><span data-stu-id="6a078-228">NameLen</span></span>|  
|-------------|  
|<span data-ttu-id="6a078-229">6</span><span class="sxs-lookup"><span data-stu-id="6a078-229">6</span></span>|  
|<span data-ttu-id="6a078-230">6</span><span class="sxs-lookup"><span data-stu-id="6a078-230">6</span></span>|  
|<span data-ttu-id="6a078-231">5</span><span class="sxs-lookup"><span data-stu-id="6a078-231">5</span></span>|  
  
### <a name="microsoft-provider-specific"></a><span data-ttu-id="6a078-232">Specifické pro společnost Microsoft poskytovatele</span><span class="sxs-lookup"><span data-stu-id="6a078-232">Microsoft Provider-Specific</span></span>  
 <span data-ttu-id="6a078-233">[Funkce specifické pro zprostředkovatele Microsoft](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md) v `SqlServer` oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="6a078-233">[Microsoft provider-specific functions](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md) are in the `SqlServer` namespace.</span></span>  
  
 <span data-ttu-id="6a078-234">Příklad:</span><span class="sxs-lookup"><span data-stu-id="6a078-234">Example:</span></span>  
  
```  
SELECT SqlServer.LEN(c.EmailAddress) As EmailLen FROM   
    AdventureWorksEntities.Contact AS c WHERE   
    c.ContactID BETWEEN 10 AND 12  
```  
  
 <span data-ttu-id="6a078-235">Výstup:</span><span class="sxs-lookup"><span data-stu-id="6a078-235">Output:</span></span>  
  
|<span data-ttu-id="6a078-236">EmailLen</span><span class="sxs-lookup"><span data-stu-id="6a078-236">EmailLen</span></span>|  
|--------------|  
|<span data-ttu-id="6a078-237">27</span><span class="sxs-lookup"><span data-stu-id="6a078-237">27</span></span>|  
|<span data-ttu-id="6a078-238">27</span><span class="sxs-lookup"><span data-stu-id="6a078-238">27</span></span>|  
|<span data-ttu-id="6a078-239">26</span><span class="sxs-lookup"><span data-stu-id="6a078-239">26</span></span>|  
  
## <a name="namespaces"></a><span data-ttu-id="6a078-240">Jmenné prostory</span><span class="sxs-lookup"><span data-stu-id="6a078-240">Namespaces</span></span>  
 <span data-ttu-id="6a078-241">[POMOCÍ](../../../../../../docs/framework/data/adonet/ef/language-reference/using-entity-sql.md) určuje oborů názvů používaných ve výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="6a078-241">[USING](../../../../../../docs/framework/data/adonet/ef/language-reference/using-entity-sql.md) specifies namespaces used in a query expression.</span></span>  
  
 <span data-ttu-id="6a078-242">Příklad:</span><span class="sxs-lookup"><span data-stu-id="6a078-242">Example:</span></span>  
  
```  
using SqlServer; LOWER('AA');  
```  
  
 <span data-ttu-id="6a078-243">Výstup:</span><span class="sxs-lookup"><span data-stu-id="6a078-243">Output:</span></span>  
  
|<span data-ttu-id="6a078-244">Value</span><span class="sxs-lookup"><span data-stu-id="6a078-244">Value</span></span>|  
|-----------|  
|<span data-ttu-id="6a078-245">aa</span><span class="sxs-lookup"><span data-stu-id="6a078-245">aa</span></span>|  
  
## <a name="paging"></a><span data-ttu-id="6a078-246">Stránkování</span><span class="sxs-lookup"><span data-stu-id="6a078-246">Paging</span></span>  
 <span data-ttu-id="6a078-247">Stránkování může být vyjádřena pomocí deklarace [přeskočit](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md) a [LIMIT](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md) dílčí klauzule [klauzule ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) klauzuli.</span><span class="sxs-lookup"><span data-stu-id="6a078-247">Paging can be expressed by declaring a [SKIP](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md) and [LIMIT](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md) sub-clauses to the [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) clause.</span></span>  
  
 <span data-ttu-id="6a078-248">Příklad:</span><span class="sxs-lookup"><span data-stu-id="6a078-248">Example:</span></span>  
  
```  
SELECT c.ContactID as ID, c.LastName as Name FROM   
    AdventureWorks.Contact AS c ORDER BY c.ContactID SKIP 9 LIMIT 3;  
```  
  
 <span data-ttu-id="6a078-249">Výstup:</span><span class="sxs-lookup"><span data-stu-id="6a078-249">Output:</span></span>  
  
|<span data-ttu-id="6a078-250">ID</span><span class="sxs-lookup"><span data-stu-id="6a078-250">ID</span></span>|<span data-ttu-id="6a078-251">Name</span><span class="sxs-lookup"><span data-stu-id="6a078-251">Name</span></span>|  
|--------|----------|  
|<span data-ttu-id="6a078-252">10</span><span class="sxs-lookup"><span data-stu-id="6a078-252">10</span></span>|<span data-ttu-id="6a078-253">Adina</span><span class="sxs-lookup"><span data-stu-id="6a078-253">Adina</span></span>|  
|<span data-ttu-id="6a078-254">11</span><span class="sxs-lookup"><span data-stu-id="6a078-254">11</span></span>|<span data-ttu-id="6a078-255">Agcaoili</span><span class="sxs-lookup"><span data-stu-id="6a078-255">Agcaoili</span></span>|  
|<span data-ttu-id="6a078-256">12</span><span class="sxs-lookup"><span data-stu-id="6a078-256">12</span></span>|<span data-ttu-id="6a078-257">Aguilar</span><span class="sxs-lookup"><span data-stu-id="6a078-257">Aguilar</span></span>|  
  
## <a name="grouping"></a><span data-ttu-id="6a078-258">Seskupování</span><span class="sxs-lookup"><span data-stu-id="6a078-258">Grouping</span></span>  
 <span data-ttu-id="6a078-259">[SESKUPENÍ podle](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md) Určuje skupiny, do které objektů vrácených dotazem ([vyberte](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)) výrazu mají být umístěny.</span><span class="sxs-lookup"><span data-stu-id="6a078-259">[GROUPING BY](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md) specifies groups into which objects returned by a query ([SELECT](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)) expression are to be placed.</span></span>  
  
 <span data-ttu-id="6a078-260">Příklad:</span><span class="sxs-lookup"><span data-stu-id="6a078-260">Example:</span></span>  
  
```  
SELECT VALUE name FROM AdventureWorksEntities.Product as P   
    GROUP BY P.Name HAVING MAX(P.ListPrice) > 5  
```  
  
 <span data-ttu-id="6a078-261">Výstup:</span><span class="sxs-lookup"><span data-stu-id="6a078-261">Output:</span></span>  
  
|<span data-ttu-id="6a078-262">name</span><span class="sxs-lookup"><span data-stu-id="6a078-262">name</span></span>|  
|----------|  
|<span data-ttu-id="6a078-263">Sestavení místo LL Horská oblast</span><span class="sxs-lookup"><span data-stu-id="6a078-263">LL Mountain Seat Assembly</span></span>|  
|<span data-ttu-id="6a078-264">Sestavení licence ML Horská oblast</span><span class="sxs-lookup"><span data-stu-id="6a078-264">ML Mountain Seat Assembly</span></span>|  
|<span data-ttu-id="6a078-265">HL Mountain místo sestavení</span><span class="sxs-lookup"><span data-stu-id="6a078-265">HL Mountain Seat Assembly</span></span>|  
|<span data-ttu-id="6a078-266">...</span><span class="sxs-lookup"><span data-stu-id="6a078-266">...</span></span>|  
  
## <a name="navigation"></a><span data-ttu-id="6a078-267">Navigace</span><span class="sxs-lookup"><span data-stu-id="6a078-267">Navigation</span></span>  
 <span data-ttu-id="6a078-268">Operátor navigace vztah umožňuje přejít nad vztah z entit (od konce) do jiného (Chcete-li ukončit).</span><span class="sxs-lookup"><span data-stu-id="6a078-268">The relationship navigation operator allows you to navigate over the relationship from one entity (from end) to another (to end).</span></span> <span data-ttu-id="6a078-269">[NAVIGOVAT](../../../../../../docs/framework/data/adonet/ef/language-reference/navigate-entity-sql.md) přijímá typ vztahu kvalifikovány jako \<oboru názvů >.\< Název typu vztahu >.</span><span class="sxs-lookup"><span data-stu-id="6a078-269">[NAVIGATE](../../../../../../docs/framework/data/adonet/ef/language-reference/navigate-entity-sql.md) takes the relationship type qualified as \<namespace>.\<relationship type name>.</span></span> <span data-ttu-id="6a078-270">Přejděte vrátí Ref\<T > Pokud Kardinalita do konce je 1.</span><span class="sxs-lookup"><span data-stu-id="6a078-270">Navigate returns Ref\<T> if the cardinality of the to end is 1.</span></span> <span data-ttu-id="6a078-271">Pokud Kardinalita do konce je n, kolekce < Ref\<T >> bude vrácen.</span><span class="sxs-lookup"><span data-stu-id="6a078-271">If the cardinality of the to end is n, the Collection<Ref\<T>> will be returned.</span></span>  
  
 <span data-ttu-id="6a078-272">Příklad:</span><span class="sxs-lookup"><span data-stu-id="6a078-272">Example:</span></span>  
  
```  
SELECT a.AddressID, (SELECT VALUE DEREF(v) FROM   
    NAVIGATE(a, AdventureWorksModel.FK_SalesOrderHeader_Address_BillToAddressID) AS v)   
    FROM AdventureWorksEntities.Address AS a  
```  
  
 <span data-ttu-id="6a078-273">Výstup:</span><span class="sxs-lookup"><span data-stu-id="6a078-273">Output:</span></span>  
  
|<span data-ttu-id="6a078-274">AddressID</span><span class="sxs-lookup"><span data-stu-id="6a078-274">AddressID</span></span>|  
|---------------|  
|<span data-ttu-id="6a078-275">1</span><span class="sxs-lookup"><span data-stu-id="6a078-275">1</span></span>|  
|<span data-ttu-id="6a078-276">2</span><span class="sxs-lookup"><span data-stu-id="6a078-276">2</span></span>|  
|<span data-ttu-id="6a078-277">3</span><span class="sxs-lookup"><span data-stu-id="6a078-277">3</span></span>|  
|<span data-ttu-id="6a078-278">...</span><span class="sxs-lookup"><span data-stu-id="6a078-278">...</span></span>|  
  
## <a name="select-value-and-select"></a><span data-ttu-id="6a078-279">VYBERTE HODNOTU A VYBERTE</span><span class="sxs-lookup"><span data-stu-id="6a078-279">SELECT VALUE AND SELECT</span></span>  
  
### <a name="select-value"></a><span data-ttu-id="6a078-280">VYBERTE HODNOTU</span><span class="sxs-lookup"><span data-stu-id="6a078-280">SELECT VALUE</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="6a078-281">poskytuje klauzule SELECT VALUE pro přeskočení konstrukce implicitní řádek.</span><span class="sxs-lookup"><span data-stu-id="6a078-281">provides the SELECT VALUE clause to skip the implicit row construction.</span></span> <span data-ttu-id="6a078-282">V klauzuli SELECT VALUE lze zadat pouze jednu položku.</span><span class="sxs-lookup"><span data-stu-id="6a078-282">Only one item can be specified in a SELECT VALUE clause.</span></span> <span data-ttu-id="6a078-283">Při těchto klauzulí se používá, je vytvořen žádný řádek obálku kolem položek v klauzuli SELECT a kolekce na požadovaný tvar je možné vytvořit, například: `SELECT VALUE a`.</span><span class="sxs-lookup"><span data-stu-id="6a078-283">When such a clause is used, no row wrapper is constructed around the items in the SELECT clause, and a collection of the desired shape can be produced, for example: `SELECT VALUE a`.</span></span>  
  
 <span data-ttu-id="6a078-284">Příklad:</span><span class="sxs-lookup"><span data-stu-id="6a078-284">Example:</span></span>  
  
```  
SELECT VALUE p.Name FROM AdventureWorksEntities.Product as p  
```  
  
 <span data-ttu-id="6a078-285">Výstup:</span><span class="sxs-lookup"><span data-stu-id="6a078-285">Output:</span></span>  
  
|<span data-ttu-id="6a078-286">Name</span><span class="sxs-lookup"><span data-stu-id="6a078-286">Name</span></span>|  
|----------|  
|<span data-ttu-id="6a078-287">Měnitelné závodu</span><span class="sxs-lookup"><span data-stu-id="6a078-287">Adjustable Race</span></span>|  
|<span data-ttu-id="6a078-288">Univerzální kol samostatné</span><span class="sxs-lookup"><span data-stu-id="6a078-288">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="6a078-289">AWC Logo zakončení</span><span class="sxs-lookup"><span data-stu-id="6a078-289">AWC Logo Cap</span></span>|  
|<span data-ttu-id="6a078-290">...</span><span class="sxs-lookup"><span data-stu-id="6a078-290">...</span></span>|  
  
### <a name="select"></a><span data-ttu-id="6a078-291">SELECT</span><span class="sxs-lookup"><span data-stu-id="6a078-291">SELECT</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="6a078-292">také poskytuje konstruktoru řádku k vytvoření libovolné řádky.</span><span class="sxs-lookup"><span data-stu-id="6a078-292">also provides the row constructor to construct arbitrary rows.</span></span> <span data-ttu-id="6a078-293">Vyberte použije jeden nebo více prvků v projekci a výsledky datového záznamu vložením polí, například: `SELECT a, b, c`.</span><span class="sxs-lookup"><span data-stu-id="6a078-293">SELECT takes one or more elements in the projection and results in a data record with fields, for example: `SELECT a, b, c`.</span></span>  
  
 <span data-ttu-id="6a078-294">Příklad:</span><span class="sxs-lookup"><span data-stu-id="6a078-294">Example:</span></span>  
  
 <span data-ttu-id="6a078-295">Vyberte p.Name, p.ProductID z AdventureWorksEntities.Product jako p výstup:</span><span class="sxs-lookup"><span data-stu-id="6a078-295">SELECT p.Name, p.ProductID FROM AdventureWorksEntities.Product as p Output:</span></span>  
  
|<span data-ttu-id="6a078-296">Name</span><span class="sxs-lookup"><span data-stu-id="6a078-296">Name</span></span>|<span data-ttu-id="6a078-297">ProductID</span><span class="sxs-lookup"><span data-stu-id="6a078-297">ProductID</span></span>|  
|----------|---------------|  
|<span data-ttu-id="6a078-298">Měnitelné závodu</span><span class="sxs-lookup"><span data-stu-id="6a078-298">Adjustable Race</span></span>|<span data-ttu-id="6a078-299">1</span><span class="sxs-lookup"><span data-stu-id="6a078-299">1</span></span>|  
|<span data-ttu-id="6a078-300">Univerzální kol samostatné</span><span class="sxs-lookup"><span data-stu-id="6a078-300">All-Purpose Bike Stand</span></span>|<span data-ttu-id="6a078-301">879</span><span class="sxs-lookup"><span data-stu-id="6a078-301">879</span></span>|  
|<span data-ttu-id="6a078-302">AWC Logo zakončení</span><span class="sxs-lookup"><span data-stu-id="6a078-302">AWC Logo Cap</span></span>|<span data-ttu-id="6a078-303">712</span><span class="sxs-lookup"><span data-stu-id="6a078-303">712</span></span>|  
|<span data-ttu-id="6a078-304">...</span><span class="sxs-lookup"><span data-stu-id="6a078-304">...</span></span>|<span data-ttu-id="6a078-305">...</span><span class="sxs-lookup"><span data-stu-id="6a078-305">...</span></span>|  
  
## <a name="case-expression"></a><span data-ttu-id="6a078-306">VÝRAZ CASE</span><span class="sxs-lookup"><span data-stu-id="6a078-306">CASE EXPRESSION</span></span>  
 <span data-ttu-id="6a078-307">[Výraz malá a velká](../../../../../../docs/framework/data/adonet/ef/language-reference/case-entity-sql.md) vyhodnotí sadu logických výrazů k určení výsledků.</span><span class="sxs-lookup"><span data-stu-id="6a078-307">The [case expression](../../../../../../docs/framework/data/adonet/ef/language-reference/case-entity-sql.md) evaluates a set of Boolean expressions to determine the result.</span></span>  
  
 <span data-ttu-id="6a078-308">Příklad:</span><span class="sxs-lookup"><span data-stu-id="6a078-308">Example:</span></span>  
  
```  
CASE WHEN AVG({25,12,11}) < 100 THEN TRUE ELSE FALSE END  
```  
  
 <span data-ttu-id="6a078-309">Výstup:</span><span class="sxs-lookup"><span data-stu-id="6a078-309">Output:</span></span>  
  
|<span data-ttu-id="6a078-310">Value</span><span class="sxs-lookup"><span data-stu-id="6a078-310">Value</span></span>|  
|-----------|  
|<span data-ttu-id="6a078-311">HODNOTA TRUE</span><span class="sxs-lookup"><span data-stu-id="6a078-311">TRUE</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6a078-312">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6a078-312">See also</span></span>

- [<span data-ttu-id="6a078-313">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="6a078-313">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [<span data-ttu-id="6a078-314">Přehled Entity SQL</span><span class="sxs-lookup"><span data-stu-id="6a078-314">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
