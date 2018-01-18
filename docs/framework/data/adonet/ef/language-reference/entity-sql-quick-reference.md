---
title: "Stručná referenční entity SQL"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e53dad9e-5e83-426e-abb4-be3e78e3d6dc
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 81fd76d09f9cc02e89ac34d5f8fa74bd7f9d92f9
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="entity-sql-quick-reference"></a><span data-ttu-id="4529a-102">Stručná referenční entity SQL</span><span class="sxs-lookup"><span data-stu-id="4529a-102">Entity SQL Quick Reference</span></span>
<span data-ttu-id="4529a-103">Toto téma obsahuje Stručná referenční příručka pro [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dotazy.</span><span class="sxs-lookup"><span data-stu-id="4529a-103">This topic provides a quick reference to [!INCLUDE[esql](../../../../../../includes/esql-md.md)] queries.</span></span> <span data-ttu-id="4529a-104">Dotazy v tomto tématu jsou založené na modelu prodeje společnosti AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="4529a-104">The queries in this topic are based on the AdventureWorks Sales model.</span></span>  
  
## <a name="literals"></a><span data-ttu-id="4529a-105">Literály</span><span class="sxs-lookup"><span data-stu-id="4529a-105">Literals</span></span>  
  
### <a name="string"></a><span data-ttu-id="4529a-106">String</span><span class="sxs-lookup"><span data-stu-id="4529a-106">String</span></span>  
 <span data-ttu-id="4529a-107">Existují textové literály znak Unicode a kódování Unicode.</span><span class="sxs-lookup"><span data-stu-id="4529a-107">There are Unicode and non-Unicode character string literals.</span></span> <span data-ttu-id="4529a-108">Řetězců v kódu Unicode se přidá jako předpona s N. Například `N'hello'`.</span><span class="sxs-lookup"><span data-stu-id="4529a-108">Unicode strings are prepended with N. For example, `N'hello'`.</span></span>  
  
 <span data-ttu-id="4529a-109">Následuje příklad než Unicode řetězcový literál:</span><span class="sxs-lookup"><span data-stu-id="4529a-109">The following is an example of a Non-Unicode string literal:</span></span>  
  
```  
'hello'  
--same as  
"hello"  
```  
  
 <span data-ttu-id="4529a-110">Výstup:</span><span class="sxs-lookup"><span data-stu-id="4529a-110">Output:</span></span>  
  
|<span data-ttu-id="4529a-111">Hodnota</span><span class="sxs-lookup"><span data-stu-id="4529a-111">Value</span></span>|  
|-----------|  
|<span data-ttu-id="4529a-112">Dobrý den</span><span class="sxs-lookup"><span data-stu-id="4529a-112">hello</span></span>|  
  
### <a name="datetime"></a><span data-ttu-id="4529a-113">DateTime</span><span class="sxs-lookup"><span data-stu-id="4529a-113">DateTime</span></span>  
 <span data-ttu-id="4529a-114">V literálech datum a čas datum a čas části jsou povinné.</span><span class="sxs-lookup"><span data-stu-id="4529a-114">In DateTime literals, both date and time parts are mandatory.</span></span> <span data-ttu-id="4529a-115">Neexistují žádné výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="4529a-115">There are no default values.</span></span>  
  
 <span data-ttu-id="4529a-116">Příklad:</span><span class="sxs-lookup"><span data-stu-id="4529a-116">Example:</span></span>  
  
```  
DATETIME '2006-12-25 01:01:00.000'   
--same as  
DATETIME '2006-12-25 01:01'  
```  
  
 <span data-ttu-id="4529a-117">Výstup:</span><span class="sxs-lookup"><span data-stu-id="4529a-117">Output:</span></span>  
  
|<span data-ttu-id="4529a-118">Hodnota</span><span class="sxs-lookup"><span data-stu-id="4529a-118">Value</span></span>|  
|-----------|  
|<span data-ttu-id="4529a-119">12/25/2006 1:01:00: 00</span><span class="sxs-lookup"><span data-stu-id="4529a-119">12/25/2006 1:01:00 AM</span></span>|  
  
### <a name="integer"></a><span data-ttu-id="4529a-120">Integer</span><span class="sxs-lookup"><span data-stu-id="4529a-120">Integer</span></span>  
 <span data-ttu-id="4529a-121">Můžou být celé číslo literály typu Int32 (123) UInt32 (123U), Int64 (123L) a UInt64 (123UL).</span><span class="sxs-lookup"><span data-stu-id="4529a-121">Integer literals can be of type Int32 (123), UInt32 (123U), Int64 (123L), and UInt64 (123UL).</span></span>  
  
 <span data-ttu-id="4529a-122">Příklad:</span><span class="sxs-lookup"><span data-stu-id="4529a-122">Example:</span></span>  
  
```  
--a collection of integers  
{1, 2, 3}  
```  
  
 <span data-ttu-id="4529a-123">Výstup:</span><span class="sxs-lookup"><span data-stu-id="4529a-123">Output:</span></span>  
  
|<span data-ttu-id="4529a-124">Hodnota</span><span class="sxs-lookup"><span data-stu-id="4529a-124">Value</span></span>|  
|-----------|  
|<span data-ttu-id="4529a-125">1</span><span class="sxs-lookup"><span data-stu-id="4529a-125">1</span></span>|  
|<span data-ttu-id="4529a-126">2</span><span class="sxs-lookup"><span data-stu-id="4529a-126">2</span></span>|  
|<span data-ttu-id="4529a-127">3</span><span class="sxs-lookup"><span data-stu-id="4529a-127">3</span></span>|  
  
### <a name="other"></a><span data-ttu-id="4529a-128">Ostatní</span><span class="sxs-lookup"><span data-stu-id="4529a-128">Other</span></span>  
 <span data-ttu-id="4529a-129">Další literály nepodporuje [!INCLUDE[esql](../../../../../../includes/esql-md.md)] jsou identifikátor Guid, binární, typu Float/Double, Decimal, a `null`.</span><span class="sxs-lookup"><span data-stu-id="4529a-129">Other literals supported by [!INCLUDE[esql](../../../../../../includes/esql-md.md)] are Guid, Binary, Float/Double, Decimal, and `null`.</span></span> <span data-ttu-id="4529a-130">Hodnota Null, literály v [!INCLUDE[esql](../../../../../../includes/esql-md.md)] se považují za kompatibilní s každou další typu v konceptuálním modelu.</span><span class="sxs-lookup"><span data-stu-id="4529a-130">Null literals in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] are considered to be compatible with every other type in the conceptual model.</span></span>  
  
## <a name="type-constructors"></a><span data-ttu-id="4529a-131">Konstruktory typu</span><span class="sxs-lookup"><span data-stu-id="4529a-131">Type Constructors</span></span>  
  
### <a name="row"></a><span data-ttu-id="4529a-132">ŘÁDEK</span><span class="sxs-lookup"><span data-stu-id="4529a-132">ROW</span></span>  
 <span data-ttu-id="4529a-133">[ŘÁDEK](../../../../../../docs/framework/data/adonet/ef/language-reference/row-entity-sql.md) vytvoří anonymní, strukturálně typované (záznamů) hodnotu jako v:`ROW(1 AS myNumber, ‘Name’ AS myName).`</span><span class="sxs-lookup"><span data-stu-id="4529a-133">[ROW](../../../../../../docs/framework/data/adonet/ef/language-reference/row-entity-sql.md) constructs an anonymous, structurally-typed (record) value as in: `ROW(1 AS myNumber, ‘Name’ AS myName).`</span></span>  
  
 <span data-ttu-id="4529a-134">Příklad:</span><span class="sxs-lookup"><span data-stu-id="4529a-134">Example:</span></span>  
  
```  
SELECT VALUE row (product.ProductID as ProductID, product.Name   
    as ProductName) FROM AdventureWorksEntities.Product AS product  
```  
  
 <span data-ttu-id="4529a-135">Výstup:</span><span class="sxs-lookup"><span data-stu-id="4529a-135">Output:</span></span>  
  
|<span data-ttu-id="4529a-136">ProductID</span><span class="sxs-lookup"><span data-stu-id="4529a-136">ProductID</span></span>|<span data-ttu-id="4529a-137">Název</span><span class="sxs-lookup"><span data-stu-id="4529a-137">Name</span></span>|  
|---------------|----------|  
|<span data-ttu-id="4529a-138">1</span><span class="sxs-lookup"><span data-stu-id="4529a-138">1</span></span>|<span data-ttu-id="4529a-139">Upravit soupeření</span><span class="sxs-lookup"><span data-stu-id="4529a-139">Adjustable Race</span></span>|  
|<span data-ttu-id="4529a-140">879</span><span class="sxs-lookup"><span data-stu-id="4529a-140">879</span></span>|<span data-ttu-id="4529a-141">Všechny účely kolo úsporný režim</span><span class="sxs-lookup"><span data-stu-id="4529a-141">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="4529a-142">712</span><span class="sxs-lookup"><span data-stu-id="4529a-142">712</span></span>|<span data-ttu-id="4529a-143">AWC Logo Cap</span><span class="sxs-lookup"><span data-stu-id="4529a-143">AWC Logo Cap</span></span>|  
|<span data-ttu-id="4529a-144">...</span><span class="sxs-lookup"><span data-stu-id="4529a-144">...</span></span>|<span data-ttu-id="4529a-145">...</span><span class="sxs-lookup"><span data-stu-id="4529a-145">...</span></span>|  
  
### <a name="multiset"></a><span data-ttu-id="4529a-146">MULTIMNOŽINA</span><span class="sxs-lookup"><span data-stu-id="4529a-146">MULTISET</span></span>  
 <span data-ttu-id="4529a-147">[MULTIMNOŽINA](../../../../../../docs/framework/data/adonet/ef/language-reference/multiset-entity-sql.md) vytvoří kolekcí, jako například:</span><span class="sxs-lookup"><span data-stu-id="4529a-147">[MULTISET](../../../../../../docs/framework/data/adonet/ef/language-reference/multiset-entity-sql.md) constructs collections, such as:</span></span>  
  
 <span data-ttu-id="4529a-148">`MULTISET(1,2,2,3)` `--same as`-`{1,2,2,3}.`</span><span class="sxs-lookup"><span data-stu-id="4529a-148">`MULTISET(1,2,2,3)` `--same as`-`{1,2,2,3}.`</span></span>  
  
 <span data-ttu-id="4529a-149">Příklad:</span><span class="sxs-lookup"><span data-stu-id="4529a-149">Example:</span></span>  
  
```  
SELECT VALUE product FROM AdventureWorksEntities.Product AS product WHERE product.ListPrice IN MultiSet (125, 300)  
```  
  
 <span data-ttu-id="4529a-150">Výstup:</span><span class="sxs-lookup"><span data-stu-id="4529a-150">Output:</span></span>  
  
|<span data-ttu-id="4529a-151">ProductID</span><span class="sxs-lookup"><span data-stu-id="4529a-151">ProductID</span></span>|<span data-ttu-id="4529a-152">Název</span><span class="sxs-lookup"><span data-stu-id="4529a-152">Name</span></span>|<span data-ttu-id="4529a-153">ProductNumber</span><span class="sxs-lookup"><span data-stu-id="4529a-153">ProductNumber</span></span>|<span data-ttu-id="4529a-154">…</span><span class="sxs-lookup"><span data-stu-id="4529a-154">…</span></span>|  
|---------------|----------|-------------------|-------|  
|<span data-ttu-id="4529a-155">842</span><span class="sxs-lookup"><span data-stu-id="4529a-155">842</span></span>|<span data-ttu-id="4529a-156">Jízdních Panniers, velké</span><span class="sxs-lookup"><span data-stu-id="4529a-156">Touring-Panniers, Large</span></span>|<span data-ttu-id="4529a-157">PA-T100</span><span class="sxs-lookup"><span data-stu-id="4529a-157">PA-T100</span></span>|<span data-ttu-id="4529a-158">…</span><span class="sxs-lookup"><span data-stu-id="4529a-158">…</span></span>|  
  
### <a name="object"></a><span data-ttu-id="4529a-159">Objekt</span><span class="sxs-lookup"><span data-stu-id="4529a-159">Object</span></span>  
 <span data-ttu-id="4529a-160">[Konstruktor typu s názvem](../../../../../../docs/framework/data/adonet/ef/language-reference/named-type-constructor-entity-sql.md) vytvoří (s názvem) uživatelem definované objekty, například `person("abc", 12)`.</span><span class="sxs-lookup"><span data-stu-id="4529a-160">[Named Type Constructor](../../../../../../docs/framework/data/adonet/ef/language-reference/named-type-constructor-entity-sql.md) constructs (named) user-defined objects, such as `person("abc", 12)`.</span></span>  
  
 <span data-ttu-id="4529a-161">Příklad:</span><span class="sxs-lookup"><span data-stu-id="4529a-161">Example:</span></span>  
  
```  
SELECT VALUE AdventureWorksModel.SalesOrderDetail (o.SalesOrderDetailID, o.CarrierTrackingNumber, o.OrderQty,   
o.ProductID, o.SpecialOfferID, o.UnitPrice, o.UnitPriceDiscount,   
o.rowguid, o.ModifiedDate) FROM AdventureWorksEntities.SalesOrderDetail   
AS o  
```  
  
 <span data-ttu-id="4529a-162">Výstup:</span><span class="sxs-lookup"><span data-stu-id="4529a-162">Output:</span></span>  
  
|<span data-ttu-id="4529a-163">SalesOrderDetailID</span><span class="sxs-lookup"><span data-stu-id="4529a-163">SalesOrderDetailID</span></span>|<span data-ttu-id="4529a-164">CarrierTrackingNumber</span><span class="sxs-lookup"><span data-stu-id="4529a-164">CarrierTrackingNumber</span></span>|<span data-ttu-id="4529a-165">OrderQty</span><span class="sxs-lookup"><span data-stu-id="4529a-165">OrderQty</span></span>|<span data-ttu-id="4529a-166">ProductID</span><span class="sxs-lookup"><span data-stu-id="4529a-166">ProductID</span></span>|<span data-ttu-id="4529a-167">...</span><span class="sxs-lookup"><span data-stu-id="4529a-167">...</span></span>|  
|------------------------|---------------------------|--------------|---------------|---------|  
|<span data-ttu-id="4529a-168">1</span><span class="sxs-lookup"><span data-stu-id="4529a-168">1</span></span>|<span data-ttu-id="4529a-169">4911-403C-98</span><span class="sxs-lookup"><span data-stu-id="4529a-169">4911-403C-98</span></span>|<span data-ttu-id="4529a-170">1</span><span class="sxs-lookup"><span data-stu-id="4529a-170">1</span></span>|<span data-ttu-id="4529a-171">776</span><span class="sxs-lookup"><span data-stu-id="4529a-171">776</span></span>|<span data-ttu-id="4529a-172">...</span><span class="sxs-lookup"><span data-stu-id="4529a-172">...</span></span>|  
|<span data-ttu-id="4529a-173">2</span><span class="sxs-lookup"><span data-stu-id="4529a-173">2</span></span>|<span data-ttu-id="4529a-174">4911-403C-98</span><span class="sxs-lookup"><span data-stu-id="4529a-174">4911-403C-98</span></span>|<span data-ttu-id="4529a-175">3</span><span class="sxs-lookup"><span data-stu-id="4529a-175">3</span></span>|<span data-ttu-id="4529a-176">777</span><span class="sxs-lookup"><span data-stu-id="4529a-176">777</span></span>|<span data-ttu-id="4529a-177">...</span><span class="sxs-lookup"><span data-stu-id="4529a-177">...</span></span>|  
|<span data-ttu-id="4529a-178">...</span><span class="sxs-lookup"><span data-stu-id="4529a-178">...</span></span>|<span data-ttu-id="4529a-179">...</span><span class="sxs-lookup"><span data-stu-id="4529a-179">...</span></span>|<span data-ttu-id="4529a-180">...</span><span class="sxs-lookup"><span data-stu-id="4529a-180">...</span></span>|<span data-ttu-id="4529a-181">...</span><span class="sxs-lookup"><span data-stu-id="4529a-181">...</span></span>|<span data-ttu-id="4529a-182">...</span><span class="sxs-lookup"><span data-stu-id="4529a-182">...</span></span>|  
  
## <a name="references"></a><span data-ttu-id="4529a-183">Odkazy</span><span class="sxs-lookup"><span data-stu-id="4529a-183">References</span></span>  
  
### <a name="ref"></a><span data-ttu-id="4529a-184">REF</span><span class="sxs-lookup"><span data-stu-id="4529a-184">REF</span></span>  
 <span data-ttu-id="4529a-185">[REF](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md) vytvoří odkaz na typ instance entity.</span><span class="sxs-lookup"><span data-stu-id="4529a-185">[REF](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md) creates a reference to an entity type instance.</span></span> <span data-ttu-id="4529a-186">Například následující dotaz vrátí odkazy na každé pořadí entity v sadě entit objednávky:</span><span class="sxs-lookup"><span data-stu-id="4529a-186">For example, the following query returns references to each Order entity in the Orders entity set:</span></span>  
  
```  
SELECT REF(o) AS OrderID FROM Orders AS o  
```  
  
 <span data-ttu-id="4529a-187">Výstup:</span><span class="sxs-lookup"><span data-stu-id="4529a-187">Output:</span></span>  
  
|<span data-ttu-id="4529a-188">Hodnota</span><span class="sxs-lookup"><span data-stu-id="4529a-188">Value</span></span>|  
|-----------|  
|<span data-ttu-id="4529a-189">1</span><span class="sxs-lookup"><span data-stu-id="4529a-189">1</span></span>|  
|<span data-ttu-id="4529a-190">2</span><span class="sxs-lookup"><span data-stu-id="4529a-190">2</span></span>|  
|<span data-ttu-id="4529a-191">3</span><span class="sxs-lookup"><span data-stu-id="4529a-191">3</span></span>|  
|<span data-ttu-id="4529a-192">...</span><span class="sxs-lookup"><span data-stu-id="4529a-192">...</span></span>|  
  
 <span data-ttu-id="4529a-193">Následující příklad používá operátor extrakce vlastnost (.) pro přístup k vlastnosti entity.</span><span class="sxs-lookup"><span data-stu-id="4529a-193">The following example uses the property extraction operator (.) to access a property of an entity.</span></span> <span data-ttu-id="4529a-194">Pokud operátor extrakce vlastnost se používá, je automaticky dereferenced odkaz.</span><span class="sxs-lookup"><span data-stu-id="4529a-194">When the property extraction operator is used, the reference is automatically dereferenced.</span></span>  
  
 <span data-ttu-id="4529a-195">Příklad:</span><span class="sxs-lookup"><span data-stu-id="4529a-195">Example:</span></span>  
  
```  
SELECT VALUE REF(p).Name FROM   
    AdventureWorksEntities.Product as p  
```  
  
 <span data-ttu-id="4529a-196">Výstup:</span><span class="sxs-lookup"><span data-stu-id="4529a-196">Output:</span></span>  
  
|<span data-ttu-id="4529a-197">Hodnota</span><span class="sxs-lookup"><span data-stu-id="4529a-197">Value</span></span>|  
|-----------|  
|<span data-ttu-id="4529a-198">Upravit soupeření</span><span class="sxs-lookup"><span data-stu-id="4529a-198">Adjustable Race</span></span>|  
|<span data-ttu-id="4529a-199">Všechny účely kolo úsporný režim</span><span class="sxs-lookup"><span data-stu-id="4529a-199">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="4529a-200">AWC Logo Cap</span><span class="sxs-lookup"><span data-stu-id="4529a-200">AWC Logo Cap</span></span>|  
|<span data-ttu-id="4529a-201">...</span><span class="sxs-lookup"><span data-stu-id="4529a-201">...</span></span>|  
  
### <a name="deref"></a><span data-ttu-id="4529a-202">DEREF</span><span class="sxs-lookup"><span data-stu-id="4529a-202">DEREF</span></span>  
 <span data-ttu-id="4529a-203">[DEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md) dereferences hodnota odkazu a vytváří výsledek této dereference.</span><span class="sxs-lookup"><span data-stu-id="4529a-203">[DEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md) dereferences a reference value and produces the result of that dereference.</span></span> <span data-ttu-id="4529a-204">Například následující dotaz vytváří pořadí entity pro každé pořadí v sadě entit objednávky: `SELECT DEREF(o2.r) FROM (SELECT REF(o) AS r FROM LOB.Orders AS o) AS o2`...</span><span class="sxs-lookup"><span data-stu-id="4529a-204">For example, the following query produces the Order entities for each Order in the Orders entity set: `SELECT DEREF(o2.r) FROM (SELECT REF(o) AS r FROM LOB.Orders AS o) AS o2`..</span></span>  
  
 <span data-ttu-id="4529a-205">Příklad:</span><span class="sxs-lookup"><span data-stu-id="4529a-205">Example:</span></span>  
  
```  
SELECT VALUE DEREF(REF(p)).Name FROM   
    AdventureWorksEntities.Product as p  
```  
  
 <span data-ttu-id="4529a-206">Výstup:</span><span class="sxs-lookup"><span data-stu-id="4529a-206">Output:</span></span>  
  
|<span data-ttu-id="4529a-207">Hodnota</span><span class="sxs-lookup"><span data-stu-id="4529a-207">Value</span></span>|  
|-----------|  
|<span data-ttu-id="4529a-208">Upravit soupeření</span><span class="sxs-lookup"><span data-stu-id="4529a-208">Adjustable Race</span></span>|  
|<span data-ttu-id="4529a-209">Všechny účely kolo úsporný režim</span><span class="sxs-lookup"><span data-stu-id="4529a-209">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="4529a-210">AWC Logo Cap</span><span class="sxs-lookup"><span data-stu-id="4529a-210">AWC Logo Cap</span></span>|  
|<span data-ttu-id="4529a-211">...</span><span class="sxs-lookup"><span data-stu-id="4529a-211">...</span></span>|  
  
### <a name="createref-and-key"></a><span data-ttu-id="4529a-212">CREATEREF A KLÍČ</span><span class="sxs-lookup"><span data-stu-id="4529a-212">CREATEREF AND KEY</span></span>  
 <span data-ttu-id="4529a-213">[CREATEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md) vytvoří odkaz předávání klíč.</span><span class="sxs-lookup"><span data-stu-id="4529a-213">[CREATEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md) creates a reference passing a key.</span></span> <span data-ttu-id="4529a-214">[KLÍČ](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md) extrahuje část výraz obsahující odkaz na typ klíče.</span><span class="sxs-lookup"><span data-stu-id="4529a-214">[KEY](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md) extracts the key portion of an expression with type reference.</span></span>  
  
 <span data-ttu-id="4529a-215">Příklad:</span><span class="sxs-lookup"><span data-stu-id="4529a-215">Example:</span></span>  
  
```  
SELECT VALUE Key(CreateRef(AdventureWorksEntities.Product, row(p.ProductID)))   
    FROM AdventureWorksEntities.Product as p  
```  
  
 <span data-ttu-id="4529a-216">Výstup:</span><span class="sxs-lookup"><span data-stu-id="4529a-216">Output:</span></span>  
  
|<span data-ttu-id="4529a-217">ProductID</span><span class="sxs-lookup"><span data-stu-id="4529a-217">ProductID</span></span>|  
|---------------|  
|<span data-ttu-id="4529a-218">980</span><span class="sxs-lookup"><span data-stu-id="4529a-218">980</span></span>|  
|<span data-ttu-id="4529a-219">365</span><span class="sxs-lookup"><span data-stu-id="4529a-219">365</span></span>|  
|<span data-ttu-id="4529a-220">771</span><span class="sxs-lookup"><span data-stu-id="4529a-220">771</span></span>|  
|<span data-ttu-id="4529a-221">...</span><span class="sxs-lookup"><span data-stu-id="4529a-221">...</span></span>|  
  
## <a name="functions"></a><span data-ttu-id="4529a-222">Funkce</span><span class="sxs-lookup"><span data-stu-id="4529a-222">Functions</span></span>  
  
### <a name="canonical"></a><span data-ttu-id="4529a-223">Kanonickém tvaru</span><span class="sxs-lookup"><span data-stu-id="4529a-223">Canonical</span></span>  
 <span data-ttu-id="4529a-224">Obor názvů pro [kanonické funkce](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md) je Edm, jako v `Edm.Length("string")`.</span><span class="sxs-lookup"><span data-stu-id="4529a-224">The namespace for [canonical functions](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md) is Edm, as in `Edm.Length("string")`.</span></span> <span data-ttu-id="4529a-225">Nemáte zadejte obor názvů, pokud jiný obor názvů je naimportována obsahující funkci se stejným názvem jako kanonické funkce.</span><span class="sxs-lookup"><span data-stu-id="4529a-225">You do not have to specify the namespace unless another namespace is imported that contains a function with the same name as a canonical function.</span></span> <span data-ttu-id="4529a-226">Pokud dva obory názvů mají stejnou funkci, uživatel má konkrétní úplný název.</span><span class="sxs-lookup"><span data-stu-id="4529a-226">If two namespaces have the same function, the user should specific the full name.</span></span>  
  
 <span data-ttu-id="4529a-227">Příklad:</span><span class="sxs-lookup"><span data-stu-id="4529a-227">Example:</span></span>  
  
```  
SELECT Length(c. FirstName) As NameLen FROM   
    AdventureWorksEntities.Contact AS c   
    WHERE c.ContactID BETWEEN 10 AND 12  
```  
  
 <span data-ttu-id="4529a-228">Výstup:</span><span class="sxs-lookup"><span data-stu-id="4529a-228">Output:</span></span>  
  
|<span data-ttu-id="4529a-229">NameLen</span><span class="sxs-lookup"><span data-stu-id="4529a-229">NameLen</span></span>|  
|-------------|  
|<span data-ttu-id="4529a-230">6</span><span class="sxs-lookup"><span data-stu-id="4529a-230">6</span></span>|  
|<span data-ttu-id="4529a-231">6</span><span class="sxs-lookup"><span data-stu-id="4529a-231">6</span></span>|  
|<span data-ttu-id="4529a-232">5</span><span class="sxs-lookup"><span data-stu-id="4529a-232">5</span></span>|  
  
### <a name="microsoft-provider-specific"></a><span data-ttu-id="4529a-233">Microsoft Provider-Specific</span><span class="sxs-lookup"><span data-stu-id="4529a-233">Microsoft Provider-Specific</span></span>  
 <span data-ttu-id="4529a-234">[Funkce specifické pro zprostředkovatele Microsoft](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md) v `SqlServer` oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="4529a-234">[Microsoft provider-specific functions](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md) are in the `SqlServer` namespace.</span></span>  
  
 <span data-ttu-id="4529a-235">Příklad:</span><span class="sxs-lookup"><span data-stu-id="4529a-235">Example:</span></span>  
  
```  
SELECT SqlServer.LEN(c.EmailAddress) As EmailLen FROM   
    AdventureWorksEntities.Contact AS c WHERE   
    c.ContactID BETWEEN 10 AND 12  
```  
  
 <span data-ttu-id="4529a-236">Výstup:</span><span class="sxs-lookup"><span data-stu-id="4529a-236">Output:</span></span>  
  
|<span data-ttu-id="4529a-237">EmailLen</span><span class="sxs-lookup"><span data-stu-id="4529a-237">EmailLen</span></span>|  
|--------------|  
|<span data-ttu-id="4529a-238">27</span><span class="sxs-lookup"><span data-stu-id="4529a-238">27</span></span>|  
|<span data-ttu-id="4529a-239">27</span><span class="sxs-lookup"><span data-stu-id="4529a-239">27</span></span>|  
|<span data-ttu-id="4529a-240">26</span><span class="sxs-lookup"><span data-stu-id="4529a-240">26</span></span>|  
  
## <a name="namespaces"></a><span data-ttu-id="4529a-241">Jmenné prostory</span><span class="sxs-lookup"><span data-stu-id="4529a-241">Namespaces</span></span>  
 <span data-ttu-id="4529a-242">[POMOCÍ](../../../../../../docs/framework/data/adonet/ef/language-reference/using-entity-sql.md) určuje oborů názvů používaných ve výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="4529a-242">[USING](../../../../../../docs/framework/data/adonet/ef/language-reference/using-entity-sql.md) specifies namespaces used in a query expression.</span></span>  
  
 <span data-ttu-id="4529a-243">Příklad:</span><span class="sxs-lookup"><span data-stu-id="4529a-243">Example:</span></span>  
  
```  
using SqlServer; LOWER('AA');  
```  
  
 <span data-ttu-id="4529a-244">Výstup:</span><span class="sxs-lookup"><span data-stu-id="4529a-244">Output:</span></span>  
  
|<span data-ttu-id="4529a-245">Hodnota</span><span class="sxs-lookup"><span data-stu-id="4529a-245">Value</span></span>|  
|-----------|  
|<span data-ttu-id="4529a-246">aa</span><span class="sxs-lookup"><span data-stu-id="4529a-246">aa</span></span>|  
  
## <a name="paging"></a><span data-ttu-id="4529a-247">Stránkování</span><span class="sxs-lookup"><span data-stu-id="4529a-247">Paging</span></span>  
 <span data-ttu-id="4529a-248">Stránkování rozdíl lze vyjádřit pomocí deklarace [přeskočit](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md) a [LIMIT](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md) dílčí klauzule k [Order](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) klauzule.</span><span class="sxs-lookup"><span data-stu-id="4529a-248">Paging can be expressed by declaring a [SKIP](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md) and [LIMIT](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md) sub-clauses to the [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) clause.</span></span>  
  
 <span data-ttu-id="4529a-249">Příklad:</span><span class="sxs-lookup"><span data-stu-id="4529a-249">Example:</span></span>  
  
```  
SELECT c.ContactID as ID, c.LastName as Name FROM   
    AdventureWorks.Contact AS c ORDER BY c.ContactID SKIP 9 LIMIT 3;  
```  
  
 <span data-ttu-id="4529a-250">Výstup:</span><span class="sxs-lookup"><span data-stu-id="4529a-250">Output:</span></span>  
  
|<span data-ttu-id="4529a-251">ID</span><span class="sxs-lookup"><span data-stu-id="4529a-251">ID</span></span>|<span data-ttu-id="4529a-252">Název</span><span class="sxs-lookup"><span data-stu-id="4529a-252">Name</span></span>|  
|--------|----------|  
|<span data-ttu-id="4529a-253">10</span><span class="sxs-lookup"><span data-stu-id="4529a-253">10</span></span>|<span data-ttu-id="4529a-254">Adina</span><span class="sxs-lookup"><span data-stu-id="4529a-254">Adina</span></span>|  
|<span data-ttu-id="4529a-255">11</span><span class="sxs-lookup"><span data-stu-id="4529a-255">11</span></span>|<span data-ttu-id="4529a-256">Agcaoili</span><span class="sxs-lookup"><span data-stu-id="4529a-256">Agcaoili</span></span>|  
|<span data-ttu-id="4529a-257">12</span><span class="sxs-lookup"><span data-stu-id="4529a-257">12</span></span>|<span data-ttu-id="4529a-258">Aguilar</span><span class="sxs-lookup"><span data-stu-id="4529a-258">Aguilar</span></span>|  
  
## <a name="grouping"></a><span data-ttu-id="4529a-259">Seskupování</span><span class="sxs-lookup"><span data-stu-id="4529a-259">Grouping</span></span>  
 <span data-ttu-id="4529a-260">[SESKUPENÍ podle](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md) Určuje skupiny, do které objektů vrácených dotazem ([vyberte](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)) výrazu mají být umístěny.</span><span class="sxs-lookup"><span data-stu-id="4529a-260">[GROUPING BY](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md) specifies groups into which objects returned by a query ([SELECT](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)) expression are to be placed.</span></span>  
  
 <span data-ttu-id="4529a-261">Příklad:</span><span class="sxs-lookup"><span data-stu-id="4529a-261">Example:</span></span>  
  
```  
SELECT VALUE name FROM AdventureWorksEntities.Product as P   
    GROUP BY P.Name HAVING MAX(P.ListPrice) > 5  
```  
  
 <span data-ttu-id="4529a-262">Výstup:</span><span class="sxs-lookup"><span data-stu-id="4529a-262">Output:</span></span>  
  
|<span data-ttu-id="4529a-263">name</span><span class="sxs-lookup"><span data-stu-id="4529a-263">name</span></span>|  
|----------|  
|<span data-ttu-id="4529a-264">Le Horská stanici sestavení</span><span class="sxs-lookup"><span data-stu-id="4529a-264">LL Mountain Seat Assembly</span></span>|  
|<span data-ttu-id="4529a-265">ML Horská stanici sestavení</span><span class="sxs-lookup"><span data-stu-id="4529a-265">ML Mountain Seat Assembly</span></span>|  
|<span data-ttu-id="4529a-266">HL Horská stanici sestavení</span><span class="sxs-lookup"><span data-stu-id="4529a-266">HL Mountain Seat Assembly</span></span>|  
|<span data-ttu-id="4529a-267">...</span><span class="sxs-lookup"><span data-stu-id="4529a-267">...</span></span>|  
  
## <a name="navigation"></a><span data-ttu-id="4529a-268">Navigace</span><span class="sxs-lookup"><span data-stu-id="4529a-268">Navigation</span></span>  
 <span data-ttu-id="4529a-269">Operátor navigační vztah můžete přejít přes vztah z jedné entity (od konce) na jiný (na konec).</span><span class="sxs-lookup"><span data-stu-id="4529a-269">The relationship navigation operator allows you to navigate over the relationship from one entity (from end) to another (to end).</span></span> <span data-ttu-id="4529a-270">[NAVIGOVAT](../../../../../../docs/framework/data/adonet/ef/language-reference/navigate-entity-sql.md) trvá kvalifikovaný typ vztahu jako \<obor názvů >.\< Název typu vztahu >.</span><span class="sxs-lookup"><span data-stu-id="4529a-270">[NAVIGATE](../../../../../../docs/framework/data/adonet/ef/language-reference/navigate-entity-sql.md) takes the relationship type qualified as \<namespace>.\<relationship type name>.</span></span> <span data-ttu-id="4529a-271">Přejděte vrátí Ref\<T > Pokud mohutnost pro ukončení je 1.</span><span class="sxs-lookup"><span data-stu-id="4529a-271">Navigate returns Ref\<T> if the cardinality of the to end is 1.</span></span> <span data-ttu-id="4529a-272">Pokud na kardinalitu pro ukončení je n, kolekce < Ref\<T >> bude vrácen.</span><span class="sxs-lookup"><span data-stu-id="4529a-272">If the cardinality of the to end is n, the Collection<Ref\<T>> will be returned.</span></span>  
  
 <span data-ttu-id="4529a-273">Příklad:</span><span class="sxs-lookup"><span data-stu-id="4529a-273">Example:</span></span>  
  
```  
SELECT a.AddressID, (SELECT VALUE DEREF(v) FROM   
    NAVIGATE(a, AdventureWorksModel.FK_SalesOrderHeader_Address_BillToAddressID) AS v)   
    FROM AdventureWorksEntities.Address AS a  
```  
  
 <span data-ttu-id="4529a-274">Výstup:</span><span class="sxs-lookup"><span data-stu-id="4529a-274">Output:</span></span>  
  
|<span data-ttu-id="4529a-275">AddressID</span><span class="sxs-lookup"><span data-stu-id="4529a-275">AddressID</span></span>|  
|---------------|  
|<span data-ttu-id="4529a-276">1</span><span class="sxs-lookup"><span data-stu-id="4529a-276">1</span></span>|  
|<span data-ttu-id="4529a-277">2</span><span class="sxs-lookup"><span data-stu-id="4529a-277">2</span></span>|  
|<span data-ttu-id="4529a-278">3</span><span class="sxs-lookup"><span data-stu-id="4529a-278">3</span></span>|  
|<span data-ttu-id="4529a-279">...</span><span class="sxs-lookup"><span data-stu-id="4529a-279">...</span></span>|  
  
## <a name="select-value-and-select"></a><span data-ttu-id="4529a-280">VYBERTE HODNOTU A VYBERTE</span><span class="sxs-lookup"><span data-stu-id="4529a-280">SELECT VALUE AND SELECT</span></span>  
  
### <a name="select-value"></a><span data-ttu-id="4529a-281">VYBERTE HODNOTU</span><span class="sxs-lookup"><span data-stu-id="4529a-281">SELECT VALUE</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="4529a-282">poskytuje v klauzuli SELECT VALUE tak, aby přeskočil konstrukce implicitní řádek.</span><span class="sxs-lookup"><span data-stu-id="4529a-282"> provides the SELECT VALUE clause to skip the implicit row construction.</span></span> <span data-ttu-id="4529a-283">V klauzuli SELECT VALUE lze zadat pouze jednu položku.</span><span class="sxs-lookup"><span data-stu-id="4529a-283">Only one item can be specified in a SELECT VALUE clause.</span></span> <span data-ttu-id="4529a-284">Když se používá tato klauzule, sestavený žádný řádek obálku kolem položky v klauzuli SELECT a kolekce požadovaný tvar je možné vytvořit, například: `SELECT VALUE a`.</span><span class="sxs-lookup"><span data-stu-id="4529a-284">When such a clause is used, no row wrapper is constructed around the items in the SELECT clause, and a collection of the desired shape can be produced, for example: `SELECT VALUE a`.</span></span>  
  
 <span data-ttu-id="4529a-285">Příklad:</span><span class="sxs-lookup"><span data-stu-id="4529a-285">Example:</span></span>  
  
```  
SELECT VALUE p.Name FROM AdventureWorksEntities.Product as p  
```  
  
 <span data-ttu-id="4529a-286">Výstup:</span><span class="sxs-lookup"><span data-stu-id="4529a-286">Output:</span></span>  
  
|<span data-ttu-id="4529a-287">Název</span><span class="sxs-lookup"><span data-stu-id="4529a-287">Name</span></span>|  
|----------|  
|<span data-ttu-id="4529a-288">Upravit soupeření</span><span class="sxs-lookup"><span data-stu-id="4529a-288">Adjustable Race</span></span>|  
|<span data-ttu-id="4529a-289">Všechny účely kolo úsporný režim</span><span class="sxs-lookup"><span data-stu-id="4529a-289">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="4529a-290">AWC Logo Cap</span><span class="sxs-lookup"><span data-stu-id="4529a-290">AWC Logo Cap</span></span>|  
|<span data-ttu-id="4529a-291">...</span><span class="sxs-lookup"><span data-stu-id="4529a-291">...</span></span>|  
  
### <a name="select"></a><span data-ttu-id="4529a-292">VYBERTE</span><span class="sxs-lookup"><span data-stu-id="4529a-292">SELECT</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="4529a-293">také poskytuje konstruktor row můžete vytvořit libovolný řádků.</span><span class="sxs-lookup"><span data-stu-id="4529a-293"> also provides the row constructor to construct arbitrary rows.</span></span> <span data-ttu-id="4529a-294">Vyberte trvá jeden či více elementů v projekci a má za následek záznam dat s poli, například: `SELECT a, b, c`.</span><span class="sxs-lookup"><span data-stu-id="4529a-294">SELECT takes one or more elements in the projection and results in a data record with fields, for example: `SELECT a, b, c`.</span></span>  
  
 <span data-ttu-id="4529a-295">Příklad:</span><span class="sxs-lookup"><span data-stu-id="4529a-295">Example:</span></span>  
  
 <span data-ttu-id="4529a-296">Vyberte p.Name, p.ProductID z AdventureWorksEntities.Product jako p výstup:</span><span class="sxs-lookup"><span data-stu-id="4529a-296">SELECT p.Name, p.ProductID FROM AdventureWorksEntities.Product as p Output:</span></span>  
  
|<span data-ttu-id="4529a-297">Název</span><span class="sxs-lookup"><span data-stu-id="4529a-297">Name</span></span>|<span data-ttu-id="4529a-298">ProductID</span><span class="sxs-lookup"><span data-stu-id="4529a-298">ProductID</span></span>|  
|----------|---------------|  
|<span data-ttu-id="4529a-299">Upravit soupeření</span><span class="sxs-lookup"><span data-stu-id="4529a-299">Adjustable Race</span></span>|<span data-ttu-id="4529a-300">1</span><span class="sxs-lookup"><span data-stu-id="4529a-300">1</span></span>|  
|<span data-ttu-id="4529a-301">Všechny účely kolo úsporný režim</span><span class="sxs-lookup"><span data-stu-id="4529a-301">All-Purpose Bike Stand</span></span>|<span data-ttu-id="4529a-302">879</span><span class="sxs-lookup"><span data-stu-id="4529a-302">879</span></span>|  
|<span data-ttu-id="4529a-303">AWC Logo Cap</span><span class="sxs-lookup"><span data-stu-id="4529a-303">AWC Logo Cap</span></span>|<span data-ttu-id="4529a-304">712</span><span class="sxs-lookup"><span data-stu-id="4529a-304">712</span></span>|  
|<span data-ttu-id="4529a-305">...</span><span class="sxs-lookup"><span data-stu-id="4529a-305">...</span></span>|<span data-ttu-id="4529a-306">...</span><span class="sxs-lookup"><span data-stu-id="4529a-306">...</span></span>|  
  
## <a name="case-expression"></a><span data-ttu-id="4529a-307">VÝRAZ CASE</span><span class="sxs-lookup"><span data-stu-id="4529a-307">CASE EXPRESSION</span></span>  
 <span data-ttu-id="4529a-308">[Případ výraz](../../../../../../docs/framework/data/adonet/ef/language-reference/case-entity-sql.md) vyhodnotí sadu logických výrazů k určení výsledku.</span><span class="sxs-lookup"><span data-stu-id="4529a-308">The [case expression](../../../../../../docs/framework/data/adonet/ef/language-reference/case-entity-sql.md) evaluates a set of Boolean expressions to determine the result.</span></span>  
  
 <span data-ttu-id="4529a-309">Příklad:</span><span class="sxs-lookup"><span data-stu-id="4529a-309">Example:</span></span>  
  
```  
CASE WHEN AVG({25,12,11}) < 100 THEN TRUE ELSE FALSE END  
```  
  
 <span data-ttu-id="4529a-310">Výstup:</span><span class="sxs-lookup"><span data-stu-id="4529a-310">Output:</span></span>  
  
|<span data-ttu-id="4529a-311">Hodnota</span><span class="sxs-lookup"><span data-stu-id="4529a-311">Value</span></span>|  
|-----------|  
|<span data-ttu-id="4529a-312">HODNOTA TRUE</span><span class="sxs-lookup"><span data-stu-id="4529a-312">TRUE</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4529a-313">Viz také</span><span class="sxs-lookup"><span data-stu-id="4529a-313">See Also</span></span>  
 [<span data-ttu-id="4529a-314">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="4529a-314">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="4529a-315">Přehled Entity SQL</span><span class="sxs-lookup"><span data-stu-id="4529a-315">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
