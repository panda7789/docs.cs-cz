---
title: Stručné reference k Entity SQL
ms.date: 03/30/2017
ms.assetid: e53dad9e-5e83-426e-abb4-be3e78e3d6dc
ms.openlocfilehash: fc7cf8f8f692f9dc4230569d5f575b6d5fad19fa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150347"
---
# <a name="entity-sql-quick-reference"></a><span data-ttu-id="a94bd-102">Stručné reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="a94bd-102">Entity SQL Quick Reference</span></span>
<span data-ttu-id="a94bd-103">Toto téma obsahuje [!INCLUDE[esql](../../../../../../includes/esql-md.md)] rychlý odkaz na dotazy.</span><span class="sxs-lookup"><span data-stu-id="a94bd-103">This topic provides a quick reference to [!INCLUDE[esql](../../../../../../includes/esql-md.md)] queries.</span></span> <span data-ttu-id="a94bd-104">Dotazy v tomto tématu jsou založeny na adventureworks prodejní model.</span><span class="sxs-lookup"><span data-stu-id="a94bd-104">The queries in this topic are based on the AdventureWorks Sales model.</span></span>  
  
## <a name="literals"></a><span data-ttu-id="a94bd-105">Literály</span><span class="sxs-lookup"><span data-stu-id="a94bd-105">Literals</span></span>  
  
### <a name="string"></a><span data-ttu-id="a94bd-106">Řetězec</span><span class="sxs-lookup"><span data-stu-id="a94bd-106">String</span></span>  
 <span data-ttu-id="a94bd-107">Existují literály řetězce znaků Unicode a non-Unicode.</span><span class="sxs-lookup"><span data-stu-id="a94bd-107">There are Unicode and non-Unicode character string literals.</span></span> <span data-ttu-id="a94bd-108">Řetězce Unicode jsou předřazeny n. Například `N'hello'`.</span><span class="sxs-lookup"><span data-stu-id="a94bd-108">Unicode strings are prepended with N. For example, `N'hello'`.</span></span>  
  
 <span data-ttu-id="a94bd-109">Následuje příklad literálu řetězce bez Unicode:</span><span class="sxs-lookup"><span data-stu-id="a94bd-109">The following is an example of a Non-Unicode string literal:</span></span>  
  
```sql  
'hello'  
--same as  
"hello"  
```  
  
 <span data-ttu-id="a94bd-110">Výstup:</span><span class="sxs-lookup"><span data-stu-id="a94bd-110">Output:</span></span>  
  
|<span data-ttu-id="a94bd-111">Hodnota</span><span class="sxs-lookup"><span data-stu-id="a94bd-111">Value</span></span>|  
|-----------|  
|<span data-ttu-id="a94bd-112">hello</span><span class="sxs-lookup"><span data-stu-id="a94bd-112">hello</span></span>|  
  
### <a name="datetime"></a><span data-ttu-id="a94bd-113">DateTime</span><span class="sxs-lookup"><span data-stu-id="a94bd-113">DateTime</span></span>  
 <span data-ttu-id="a94bd-114">V DateTime literály jsou povinné části data a času.</span><span class="sxs-lookup"><span data-stu-id="a94bd-114">In DateTime literals, both date and time parts are mandatory.</span></span> <span data-ttu-id="a94bd-115">Neexistují žádné výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="a94bd-115">There are no default values.</span></span>  
  
 <span data-ttu-id="a94bd-116">Příklad:</span><span class="sxs-lookup"><span data-stu-id="a94bd-116">Example:</span></span>  
  
```sql  
DATETIME '2006-12-25 01:01:00.000'
--same as  
DATETIME '2006-12-25 01:01'  
```  
  
 <span data-ttu-id="a94bd-117">Výstup:</span><span class="sxs-lookup"><span data-stu-id="a94bd-117">Output:</span></span>  
  
|<span data-ttu-id="a94bd-118">Hodnota</span><span class="sxs-lookup"><span data-stu-id="a94bd-118">Value</span></span>|  
|-----------|  
|<span data-ttu-id="a94bd-119">12/25/2006 1:01:00</span><span class="sxs-lookup"><span data-stu-id="a94bd-119">12/25/2006 1:01:00 AM</span></span>|  
  
### <a name="integer"></a><span data-ttu-id="a94bd-120">Integer</span><span class="sxs-lookup"><span data-stu-id="a94bd-120">Integer</span></span>  
 <span data-ttu-id="a94bd-121">Celé číslo literály může být typu Int32 (123), UInt32 (123U), Int64 (123L) a UInt64 (123UL).</span><span class="sxs-lookup"><span data-stu-id="a94bd-121">Integer literals can be of type Int32 (123), UInt32 (123U), Int64 (123L), and UInt64 (123UL).</span></span>  
  
 <span data-ttu-id="a94bd-122">Příklad:</span><span class="sxs-lookup"><span data-stu-id="a94bd-122">Example:</span></span>  
  
```sql  
--a collection of integers  
{1, 2, 3}  
```  
  
 <span data-ttu-id="a94bd-123">Výstup:</span><span class="sxs-lookup"><span data-stu-id="a94bd-123">Output:</span></span>  
  
|<span data-ttu-id="a94bd-124">Hodnota</span><span class="sxs-lookup"><span data-stu-id="a94bd-124">Value</span></span>|  
|-----------|  
|<span data-ttu-id="a94bd-125">1</span><span class="sxs-lookup"><span data-stu-id="a94bd-125">1</span></span>|  
|<span data-ttu-id="a94bd-126">2</span><span class="sxs-lookup"><span data-stu-id="a94bd-126">2</span></span>|  
|<span data-ttu-id="a94bd-127">3</span><span class="sxs-lookup"><span data-stu-id="a94bd-127">3</span></span>|  
  
### <a name="other"></a><span data-ttu-id="a94bd-128">Ostatní</span><span class="sxs-lookup"><span data-stu-id="a94bd-128">Other</span></span>  
 <span data-ttu-id="a94bd-129">Další literály [!INCLUDE[esql](../../../../../../includes/esql-md.md)] podporované jsou Guid, Binary, Float/Double, `null`Decimal a .</span><span class="sxs-lookup"><span data-stu-id="a94bd-129">Other literals supported by [!INCLUDE[esql](../../../../../../includes/esql-md.md)] are Guid, Binary, Float/Double, Decimal, and `null`.</span></span> <span data-ttu-id="a94bd-130">Null literály [!INCLUDE[esql](../../../../../../includes/esql-md.md)] v jsou považovány za kompatibilní s každý jiný typ v koncepční model.</span><span class="sxs-lookup"><span data-stu-id="a94bd-130">Null literals in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] are considered to be compatible with every other type in the conceptual model.</span></span>  
  
## <a name="type-constructors"></a><span data-ttu-id="a94bd-131">Konstruktory typu</span><span class="sxs-lookup"><span data-stu-id="a94bd-131">Type Constructors</span></span>  
  
### <a name="row"></a><span data-ttu-id="a94bd-132">ROW</span><span class="sxs-lookup"><span data-stu-id="a94bd-132">ROW</span></span>  
 <span data-ttu-id="a94bd-133">[ROW](row-entity-sql.md) vytvoří anonymní, strukturálně zadaný (záznam) hodnotu jako v:`ROW(1 AS myNumber, ‘Name’ AS myName).`</span><span class="sxs-lookup"><span data-stu-id="a94bd-133">[ROW](row-entity-sql.md) constructs an anonymous, structurally-typed (record) value as in: `ROW(1 AS myNumber, ‘Name’ AS myName).`</span></span>  
  
 <span data-ttu-id="a94bd-134">Příklad:</span><span class="sxs-lookup"><span data-stu-id="a94bd-134">Example:</span></span>  
  
```sql  
SELECT VALUE row (product.ProductID AS ProductID, product.Name
    AS ProductName) FROM AdventureWorksEntities.Product AS product
```  
  
 <span data-ttu-id="a94bd-135">Výstup:</span><span class="sxs-lookup"><span data-stu-id="a94bd-135">Output:</span></span>  
  
|<span data-ttu-id="a94bd-136">ProductID</span><span class="sxs-lookup"><span data-stu-id="a94bd-136">ProductID</span></span>|<span data-ttu-id="a94bd-137">Name (Název)</span><span class="sxs-lookup"><span data-stu-id="a94bd-137">Name</span></span>|  
|---------------|----------|  
|<span data-ttu-id="a94bd-138">1</span><span class="sxs-lookup"><span data-stu-id="a94bd-138">1</span></span>|<span data-ttu-id="a94bd-139">Nastavitelná rasa</span><span class="sxs-lookup"><span data-stu-id="a94bd-139">Adjustable Race</span></span>|  
|<span data-ttu-id="a94bd-140">879</span><span class="sxs-lookup"><span data-stu-id="a94bd-140">879</span></span>|<span data-ttu-id="a94bd-141">Univerzální stojan na kola</span><span class="sxs-lookup"><span data-stu-id="a94bd-141">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="a94bd-142">712</span><span class="sxs-lookup"><span data-stu-id="a94bd-142">712</span></span>|<span data-ttu-id="a94bd-143">Víčko loga AWC</span><span class="sxs-lookup"><span data-stu-id="a94bd-143">AWC Logo Cap</span></span>|  
|<span data-ttu-id="a94bd-144">...</span><span class="sxs-lookup"><span data-stu-id="a94bd-144">...</span></span>|<span data-ttu-id="a94bd-145">...</span><span class="sxs-lookup"><span data-stu-id="a94bd-145">...</span></span>|  
  
### <a name="multiset"></a><span data-ttu-id="a94bd-146">MULTISET</span><span class="sxs-lookup"><span data-stu-id="a94bd-146">MULTISET</span></span>  
 <span data-ttu-id="a94bd-147">[MULTISET](multiset-entity-sql.md) vytváří kolekce, jako jsou:</span><span class="sxs-lookup"><span data-stu-id="a94bd-147">[MULTISET](multiset-entity-sql.md) constructs collections, such as:</span></span>  
  
 <span data-ttu-id="a94bd-148">`MULTISET(1,2,2,3)` `--same as`-`{1,2,2,3}.`</span><span class="sxs-lookup"><span data-stu-id="a94bd-148">`MULTISET(1,2,2,3)` `--same as`-`{1,2,2,3}.`</span></span>  
  
 <span data-ttu-id="a94bd-149">Příklad:</span><span class="sxs-lookup"><span data-stu-id="a94bd-149">Example:</span></span>  
  
```sql  
SELECT VALUE product FROM AdventureWorksEntities.Product AS product WHERE product.ListPrice IN MultiSet (125, 300)  
```  
  
 <span data-ttu-id="a94bd-150">Výstup:</span><span class="sxs-lookup"><span data-stu-id="a94bd-150">Output:</span></span>  
  
|<span data-ttu-id="a94bd-151">ProductID</span><span class="sxs-lookup"><span data-stu-id="a94bd-151">ProductID</span></span>|<span data-ttu-id="a94bd-152">Name (Název)</span><span class="sxs-lookup"><span data-stu-id="a94bd-152">Name</span></span>|<span data-ttu-id="a94bd-153">Číslo produktu</span><span class="sxs-lookup"><span data-stu-id="a94bd-153">ProductNumber</span></span>|<span data-ttu-id="a94bd-154">…</span><span class="sxs-lookup"><span data-stu-id="a94bd-154">…</span></span>|  
|---------------|----------|-------------------|-------|  
|<span data-ttu-id="a94bd-155">842</span><span class="sxs-lookup"><span data-stu-id="a94bd-155">842</span></span>|<span data-ttu-id="a94bd-156">Touring-Kufry, Velké</span><span class="sxs-lookup"><span data-stu-id="a94bd-156">Touring-Panniers, Large</span></span>|<span data-ttu-id="a94bd-157">PA-T100</span><span class="sxs-lookup"><span data-stu-id="a94bd-157">PA-T100</span></span>|<span data-ttu-id="a94bd-158">…</span><span class="sxs-lookup"><span data-stu-id="a94bd-158">…</span></span>|  
  
### <a name="object"></a><span data-ttu-id="a94bd-159">Objekt</span><span class="sxs-lookup"><span data-stu-id="a94bd-159">Object</span></span>  
 <span data-ttu-id="a94bd-160">[Pojmenovaný typ konstruktoru](named-type-constructor-entity-sql.md) konstrukce (pojmenované) uživatelem `person("abc", 12)`definované objekty, například .</span><span class="sxs-lookup"><span data-stu-id="a94bd-160">[Named Type Constructor](named-type-constructor-entity-sql.md) constructs (named) user-defined objects, such as `person("abc", 12)`.</span></span>  
  
 <span data-ttu-id="a94bd-161">Příklad:</span><span class="sxs-lookup"><span data-stu-id="a94bd-161">Example:</span></span>  
  
```sql  
SELECT VALUE AdventureWorksModel.SalesOrderDetail (o.SalesOrderDetailID, o.CarrierTrackingNumber, o.OrderQty,
o.ProductID, o.SpecialOfferID, o.UnitPrice, o.UnitPriceDiscount,
o.rowguid, o.ModifiedDate) FROM AdventureWorksEntities.SalesOrderDetail
AS o  
```  
  
 <span data-ttu-id="a94bd-162">Výstup:</span><span class="sxs-lookup"><span data-stu-id="a94bd-162">Output:</span></span>  
  
|<span data-ttu-id="a94bd-163">SalesOrderDetailID</span><span class="sxs-lookup"><span data-stu-id="a94bd-163">SalesOrderDetailID</span></span>|<span data-ttu-id="a94bd-164">Číslo CarrierTrackingNumber</span><span class="sxs-lookup"><span data-stu-id="a94bd-164">CarrierTrackingNumber</span></span>|<span data-ttu-id="a94bd-165">OrderQty</span><span class="sxs-lookup"><span data-stu-id="a94bd-165">OrderQty</span></span>|<span data-ttu-id="a94bd-166">ProductID</span><span class="sxs-lookup"><span data-stu-id="a94bd-166">ProductID</span></span>|<span data-ttu-id="a94bd-167">...</span><span class="sxs-lookup"><span data-stu-id="a94bd-167">...</span></span>|  
|------------------------|---------------------------|--------------|---------------|---------|  
|<span data-ttu-id="a94bd-168">1</span><span class="sxs-lookup"><span data-stu-id="a94bd-168">1</span></span>|<span data-ttu-id="a94bd-169">4911-403C-98</span><span class="sxs-lookup"><span data-stu-id="a94bd-169">4911-403C-98</span></span>|<span data-ttu-id="a94bd-170">1</span><span class="sxs-lookup"><span data-stu-id="a94bd-170">1</span></span>|<span data-ttu-id="a94bd-171">776</span><span class="sxs-lookup"><span data-stu-id="a94bd-171">776</span></span>|<span data-ttu-id="a94bd-172">...</span><span class="sxs-lookup"><span data-stu-id="a94bd-172">...</span></span>|  
|<span data-ttu-id="a94bd-173">2</span><span class="sxs-lookup"><span data-stu-id="a94bd-173">2</span></span>|<span data-ttu-id="a94bd-174">4911-403C-98</span><span class="sxs-lookup"><span data-stu-id="a94bd-174">4911-403C-98</span></span>|<span data-ttu-id="a94bd-175">3</span><span class="sxs-lookup"><span data-stu-id="a94bd-175">3</span></span>|<span data-ttu-id="a94bd-176">777</span><span class="sxs-lookup"><span data-stu-id="a94bd-176">777</span></span>|<span data-ttu-id="a94bd-177">...</span><span class="sxs-lookup"><span data-stu-id="a94bd-177">...</span></span>|  
|<span data-ttu-id="a94bd-178">...</span><span class="sxs-lookup"><span data-stu-id="a94bd-178">...</span></span>|<span data-ttu-id="a94bd-179">...</span><span class="sxs-lookup"><span data-stu-id="a94bd-179">...</span></span>|<span data-ttu-id="a94bd-180">...</span><span class="sxs-lookup"><span data-stu-id="a94bd-180">...</span></span>|<span data-ttu-id="a94bd-181">...</span><span class="sxs-lookup"><span data-stu-id="a94bd-181">...</span></span>|<span data-ttu-id="a94bd-182">...</span><span class="sxs-lookup"><span data-stu-id="a94bd-182">...</span></span>|  
  
## <a name="references"></a><span data-ttu-id="a94bd-183">Odkazy</span><span class="sxs-lookup"><span data-stu-id="a94bd-183">References</span></span>  
  
### <a name="ref"></a><span data-ttu-id="a94bd-184">REF</span><span class="sxs-lookup"><span data-stu-id="a94bd-184">REF</span></span>  
 <span data-ttu-id="a94bd-185">[REF](ref-entity-sql.md) vytvoří odkaz na instanci typu entity.</span><span class="sxs-lookup"><span data-stu-id="a94bd-185">[REF](ref-entity-sql.md) creates a reference to an entity type instance.</span></span> <span data-ttu-id="a94bd-186">Například následující dotaz vrátí odkazy na každou entitu Objednávka v sadě entit Objednávky:</span><span class="sxs-lookup"><span data-stu-id="a94bd-186">For example, the following query returns references to each Order entity in the Orders entity set:</span></span>  
  
```sql  
SELECT REF(o) AS OrderID FROM Orders AS o  
```  
  
 <span data-ttu-id="a94bd-187">Výstup:</span><span class="sxs-lookup"><span data-stu-id="a94bd-187">Output:</span></span>  
  
|<span data-ttu-id="a94bd-188">Hodnota</span><span class="sxs-lookup"><span data-stu-id="a94bd-188">Value</span></span>|  
|-----------|  
|<span data-ttu-id="a94bd-189">1</span><span class="sxs-lookup"><span data-stu-id="a94bd-189">1</span></span>|  
|<span data-ttu-id="a94bd-190">2</span><span class="sxs-lookup"><span data-stu-id="a94bd-190">2</span></span>|  
|<span data-ttu-id="a94bd-191">3</span><span class="sxs-lookup"><span data-stu-id="a94bd-191">3</span></span>|  
|<span data-ttu-id="a94bd-192">...</span><span class="sxs-lookup"><span data-stu-id="a94bd-192">...</span></span>|  
  
 <span data-ttu-id="a94bd-193">Následující příklad používá operátor extrakce vlastnosti (.) pro přístup k vlastnosti entity.</span><span class="sxs-lookup"><span data-stu-id="a94bd-193">The following example uses the property extraction operator (.) to access a property of an entity.</span></span> <span data-ttu-id="a94bd-194">Při použití operátoru extrakce vlastnosti je odkaz automaticky odkazován.</span><span class="sxs-lookup"><span data-stu-id="a94bd-194">When the property extraction operator is used, the reference is automatically dereferenced.</span></span>  
  
 <span data-ttu-id="a94bd-195">Příklad:</span><span class="sxs-lookup"><span data-stu-id="a94bd-195">Example:</span></span>  
  
```sql  
SELECT VALUE REF(p).Name FROM
    AdventureWorksEntities.Product AS p
```  
  
 <span data-ttu-id="a94bd-196">Výstup:</span><span class="sxs-lookup"><span data-stu-id="a94bd-196">Output:</span></span>  
  
|<span data-ttu-id="a94bd-197">Hodnota</span><span class="sxs-lookup"><span data-stu-id="a94bd-197">Value</span></span>|  
|-----------|  
|<span data-ttu-id="a94bd-198">Nastavitelná rasa</span><span class="sxs-lookup"><span data-stu-id="a94bd-198">Adjustable Race</span></span>|  
|<span data-ttu-id="a94bd-199">Univerzální stojan na kola</span><span class="sxs-lookup"><span data-stu-id="a94bd-199">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="a94bd-200">Víčko loga AWC</span><span class="sxs-lookup"><span data-stu-id="a94bd-200">AWC Logo Cap</span></span>|  
|<span data-ttu-id="a94bd-201">...</span><span class="sxs-lookup"><span data-stu-id="a94bd-201">...</span></span>|  
  
### <a name="deref"></a><span data-ttu-id="a94bd-202">DEREF</span><span class="sxs-lookup"><span data-stu-id="a94bd-202">DEREF</span></span>  
 <span data-ttu-id="a94bd-203">[DEREF](deref-entity-sql.md) dereferences referenční hodnotu a vytváří výsledek tohoto dereference.</span><span class="sxs-lookup"><span data-stu-id="a94bd-203">[DEREF](deref-entity-sql.md) dereferences a reference value and produces the result of that dereference.</span></span> <span data-ttu-id="a94bd-204">Například následující dotaz vytvoří entity Objednávka pro každou objednávku `SELECT DEREF(o2.r) FROM (SELECT REF(o) AS r FROM LOB.Orders AS o) AS o2`v sadě entit Objednávky: ..</span><span class="sxs-lookup"><span data-stu-id="a94bd-204">For example, the following query produces the Order entities for each Order in the Orders entity set: `SELECT DEREF(o2.r) FROM (SELECT REF(o) AS r FROM LOB.Orders AS o) AS o2`..</span></span>  
  
 <span data-ttu-id="a94bd-205">Příklad:</span><span class="sxs-lookup"><span data-stu-id="a94bd-205">Example:</span></span>  
  
```sql  
SELECT VALUE DEREF(REF(p)).Name FROM
    AdventureWorksEntities.Product AS p
```  
  
 <span data-ttu-id="a94bd-206">Výstup:</span><span class="sxs-lookup"><span data-stu-id="a94bd-206">Output:</span></span>  
  
|<span data-ttu-id="a94bd-207">Hodnota</span><span class="sxs-lookup"><span data-stu-id="a94bd-207">Value</span></span>|  
|-----------|  
|<span data-ttu-id="a94bd-208">Nastavitelná rasa</span><span class="sxs-lookup"><span data-stu-id="a94bd-208">Adjustable Race</span></span>|  
|<span data-ttu-id="a94bd-209">Univerzální stojan na kola</span><span class="sxs-lookup"><span data-stu-id="a94bd-209">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="a94bd-210">Víčko loga AWC</span><span class="sxs-lookup"><span data-stu-id="a94bd-210">AWC Logo Cap</span></span>|  
|<span data-ttu-id="a94bd-211">...</span><span class="sxs-lookup"><span data-stu-id="a94bd-211">...</span></span>|  
  
### <a name="createref-and-key"></a><span data-ttu-id="a94bd-212">CREATEREF A KLÍČ</span><span class="sxs-lookup"><span data-stu-id="a94bd-212">CREATEREF AND KEY</span></span>  
 <span data-ttu-id="a94bd-213">[CREATEREF](createref-entity-sql.md) vytvoří odkaz předání klíče.</span><span class="sxs-lookup"><span data-stu-id="a94bd-213">[CREATEREF](createref-entity-sql.md) creates a reference passing a key.</span></span> <span data-ttu-id="a94bd-214">[KEY](key-entity-sql.md) extrahuje klíčovou část výrazu s odkazem na typ.</span><span class="sxs-lookup"><span data-stu-id="a94bd-214">[KEY](key-entity-sql.md) extracts the key portion of an expression with type reference.</span></span>  
  
 <span data-ttu-id="a94bd-215">Příklad:</span><span class="sxs-lookup"><span data-stu-id="a94bd-215">Example:</span></span>  
  
```sql  
SELECT VALUE Key(CreateRef(AdventureWorksEntities.Product, row(p.ProductID)))
    FROM AdventureWorksEntities.Product AS p
```  
  
 <span data-ttu-id="a94bd-216">Výstup:</span><span class="sxs-lookup"><span data-stu-id="a94bd-216">Output:</span></span>  
  
|<span data-ttu-id="a94bd-217">ProductID</span><span class="sxs-lookup"><span data-stu-id="a94bd-217">ProductID</span></span>|  
|---------------|  
|<span data-ttu-id="a94bd-218">980</span><span class="sxs-lookup"><span data-stu-id="a94bd-218">980</span></span>|  
|<span data-ttu-id="a94bd-219">365</span><span class="sxs-lookup"><span data-stu-id="a94bd-219">365</span></span>|  
|<span data-ttu-id="a94bd-220">771</span><span class="sxs-lookup"><span data-stu-id="a94bd-220">771</span></span>|  
|<span data-ttu-id="a94bd-221">...</span><span class="sxs-lookup"><span data-stu-id="a94bd-221">...</span></span>|  
  
## <a name="functions"></a><span data-ttu-id="a94bd-222">Funkce</span><span class="sxs-lookup"><span data-stu-id="a94bd-222">Functions</span></span>  
  
### <a name="canonical"></a><span data-ttu-id="a94bd-223">Canonical</span><span class="sxs-lookup"><span data-stu-id="a94bd-223">Canonical</span></span>  
 <span data-ttu-id="a94bd-224">Obor názvů pro [kanonické funkce](canonical-functions.md) je `Edm.Length("string")`Edm, jako v .</span><span class="sxs-lookup"><span data-stu-id="a94bd-224">The namespace for [canonical functions](canonical-functions.md) is Edm, as in `Edm.Length("string")`.</span></span> <span data-ttu-id="a94bd-225">Není nutné zadávat obor názvů, pokud není importován jiný obor názvů, který obsahuje funkci se stejným názvem jako kanonická funkce.</span><span class="sxs-lookup"><span data-stu-id="a94bd-225">You do not have to specify the namespace unless another namespace is imported that contains a function with the same name as a canonical function.</span></span> <span data-ttu-id="a94bd-226">Pokud dva obory názvů mají stejnou funkci, uživatel by měl určit celé jméno.</span><span class="sxs-lookup"><span data-stu-id="a94bd-226">If two namespaces have the same function, the user should specific the full name.</span></span>  
  
 <span data-ttu-id="a94bd-227">Příklad:</span><span class="sxs-lookup"><span data-stu-id="a94bd-227">Example:</span></span>  
  
```sql  
SELECT Length(c. FirstName) AS NameLen FROM
    AdventureWorksEntities.Contact AS c
    WHERE c.ContactID BETWEEN 10 AND 12  
```  
  
 <span data-ttu-id="a94bd-228">Výstup:</span><span class="sxs-lookup"><span data-stu-id="a94bd-228">Output:</span></span>  
  
|<span data-ttu-id="a94bd-229">NázevLen</span><span class="sxs-lookup"><span data-stu-id="a94bd-229">NameLen</span></span>|  
|-------------|  
|<span data-ttu-id="a94bd-230">6</span><span class="sxs-lookup"><span data-stu-id="a94bd-230">6</span></span>|  
|<span data-ttu-id="a94bd-231">6</span><span class="sxs-lookup"><span data-stu-id="a94bd-231">6</span></span>|  
|<span data-ttu-id="a94bd-232">5</span><span class="sxs-lookup"><span data-stu-id="a94bd-232">5</span></span>|  
  
### <a name="microsoft-provider-specific"></a><span data-ttu-id="a94bd-233">Specifické pro poskytovatele společnosti Microsoft</span><span class="sxs-lookup"><span data-stu-id="a94bd-233">Microsoft Provider-Specific</span></span>  
 <span data-ttu-id="a94bd-234">[Funkce specifické pro poskytovatele](../sqlclient-for-ef-functions.md) `SqlServer` společnosti Microsoft jsou v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="a94bd-234">[Microsoft provider-specific functions](../sqlclient-for-ef-functions.md) are in the `SqlServer` namespace.</span></span>  
  
 <span data-ttu-id="a94bd-235">Příklad:</span><span class="sxs-lookup"><span data-stu-id="a94bd-235">Example:</span></span>  
  
```sql  
SELECT SqlServer.LEN(c.EmailAddress) AS EmailLen FROM
    AdventureWorksEntities.Contact AS c WHERE
    c.ContactID BETWEEN 10 AND 12  
```  
  
 <span data-ttu-id="a94bd-236">Výstup:</span><span class="sxs-lookup"><span data-stu-id="a94bd-236">Output:</span></span>  
  
|<span data-ttu-id="a94bd-237">E-maillen</span><span class="sxs-lookup"><span data-stu-id="a94bd-237">EmailLen</span></span>|  
|--------------|  
|<span data-ttu-id="a94bd-238">27</span><span class="sxs-lookup"><span data-stu-id="a94bd-238">27</span></span>|  
|<span data-ttu-id="a94bd-239">27</span><span class="sxs-lookup"><span data-stu-id="a94bd-239">27</span></span>|  
|<span data-ttu-id="a94bd-240">26</span><span class="sxs-lookup"><span data-stu-id="a94bd-240">26</span></span>|  
  
## <a name="namespaces"></a><span data-ttu-id="a94bd-241">Obory názvů</span><span class="sxs-lookup"><span data-stu-id="a94bd-241">Namespaces</span></span>  
 <span data-ttu-id="a94bd-242">[Použití](using-entity-sql.md) určuje obory názvů používané ve výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="a94bd-242">[USING](using-entity-sql.md) specifies namespaces used in a query expression.</span></span>  
  
 <span data-ttu-id="a94bd-243">Příklad:</span><span class="sxs-lookup"><span data-stu-id="a94bd-243">Example:</span></span>  
  
```sql  
using SqlServer; LOWER('AA');  
```  
  
 <span data-ttu-id="a94bd-244">Výstup:</span><span class="sxs-lookup"><span data-stu-id="a94bd-244">Output:</span></span>  
  
|<span data-ttu-id="a94bd-245">Hodnota</span><span class="sxs-lookup"><span data-stu-id="a94bd-245">Value</span></span>|  
|-----------|  
|<span data-ttu-id="a94bd-246">aa</span><span class="sxs-lookup"><span data-stu-id="a94bd-246">aa</span></span>|  
  
## <a name="paging"></a><span data-ttu-id="a94bd-247">Stránkování</span><span class="sxs-lookup"><span data-stu-id="a94bd-247">Paging</span></span>  
 <span data-ttu-id="a94bd-248">Stránkování lze vyjádřit deklarováním podklauzulí [SKIP](skip-entity-sql.md) a [LIMIT](limit-entity-sql.md) do klauzule [ORDER BY.](order-by-entity-sql.md)</span><span class="sxs-lookup"><span data-stu-id="a94bd-248">Paging can be expressed by declaring a [SKIP](skip-entity-sql.md) and [LIMIT](limit-entity-sql.md) sub-clauses to the [ORDER BY](order-by-entity-sql.md) clause.</span></span>  
  
 <span data-ttu-id="a94bd-249">Příklad:</span><span class="sxs-lookup"><span data-stu-id="a94bd-249">Example:</span></span>  
  
```sql  
SELECT c.ContactID as ID, c.LastName AS Name FROM
    AdventureWorks.Contact AS c ORDER BY c.ContactID SKIP 9 LIMIT 3;  
```  
  
 <span data-ttu-id="a94bd-250">Výstup:</span><span class="sxs-lookup"><span data-stu-id="a94bd-250">Output:</span></span>  
  
|<span data-ttu-id="a94bd-251">ID</span><span class="sxs-lookup"><span data-stu-id="a94bd-251">ID</span></span>|<span data-ttu-id="a94bd-252">Name (Název)</span><span class="sxs-lookup"><span data-stu-id="a94bd-252">Name</span></span>|  
|--------|----------|  
|<span data-ttu-id="a94bd-253">10</span><span class="sxs-lookup"><span data-stu-id="a94bd-253">10</span></span>|<span data-ttu-id="a94bd-254">Adina</span><span class="sxs-lookup"><span data-stu-id="a94bd-254">Adina</span></span>|  
|<span data-ttu-id="a94bd-255">11</span><span class="sxs-lookup"><span data-stu-id="a94bd-255">11</span></span>|<span data-ttu-id="a94bd-256">Agcaoili</span><span class="sxs-lookup"><span data-stu-id="a94bd-256">Agcaoili</span></span>|  
|<span data-ttu-id="a94bd-257">12</span><span class="sxs-lookup"><span data-stu-id="a94bd-257">12</span></span>|<span data-ttu-id="a94bd-258">Aguilar</span><span class="sxs-lookup"><span data-stu-id="a94bd-258">Aguilar</span></span>|  
  
## <a name="grouping"></a><span data-ttu-id="a94bd-259">Seskupování</span><span class="sxs-lookup"><span data-stu-id="a94bd-259">Grouping</span></span>  
 <span data-ttu-id="a94bd-260">[SESKUPENÍ PODLE](group-by-entity-sql.md) určuje skupiny, do kterých mají být umístěny objekty vrácené výrazem dotazu[(SELECT).](select-entity-sql.md)</span><span class="sxs-lookup"><span data-stu-id="a94bd-260">[GROUPING BY](group-by-entity-sql.md) specifies groups into which objects returned by a query ([SELECT](select-entity-sql.md)) expression are to be placed.</span></span>  
  
 <span data-ttu-id="a94bd-261">Příklad:</span><span class="sxs-lookup"><span data-stu-id="a94bd-261">Example:</span></span>  
  
```sql  
SELECT VALUE name FROM AdventureWorksEntities.Product AS P
    GROUP BY P.Name HAVING MAX(P.ListPrice) > 5  
```  
  
 <span data-ttu-id="a94bd-262">Výstup:</span><span class="sxs-lookup"><span data-stu-id="a94bd-262">Output:</span></span>  
  
|<span data-ttu-id="a94bd-263">jméno</span><span class="sxs-lookup"><span data-stu-id="a94bd-263">name</span></span>|  
|----------|  
|<span data-ttu-id="a94bd-264">LL Montáž horských sedadel</span><span class="sxs-lookup"><span data-stu-id="a94bd-264">LL Mountain Seat Assembly</span></span>|  
|<span data-ttu-id="a94bd-265">Sestava horského sedadla ML</span><span class="sxs-lookup"><span data-stu-id="a94bd-265">ML Mountain Seat Assembly</span></span>|  
|<span data-ttu-id="a94bd-266">Hl Horské sídlo shromáždění</span><span class="sxs-lookup"><span data-stu-id="a94bd-266">HL Mountain Seat Assembly</span></span>|  
|<span data-ttu-id="a94bd-267">...</span><span class="sxs-lookup"><span data-stu-id="a94bd-267">...</span></span>|  
  
## <a name="navigation"></a><span data-ttu-id="a94bd-268">Navigace</span><span class="sxs-lookup"><span data-stu-id="a94bd-268">Navigation</span></span>  
 <span data-ttu-id="a94bd-269">Operátor navigace vztahu umožňuje přejít přes vztah z jedné entity (z konce) do druhé (do konce).</span><span class="sxs-lookup"><span data-stu-id="a94bd-269">The relationship navigation operator allows you to navigate over the relationship from one entity (from end) to another (to end).</span></span> <span data-ttu-id="a94bd-270">[FUNKCE NAVIGATE](navigate-entity-sql.md) přebírá typ \<vztahu kvalifikovaný jako obor názvů>. \<> název typu relace.</span><span class="sxs-lookup"><span data-stu-id="a94bd-270">[NAVIGATE](navigate-entity-sql.md) takes the relationship type qualified as \<namespace>.\<relationship type name>.</span></span> <span data-ttu-id="a94bd-271">Navigate vrátí\<Ref T> pokud mohutnost do konce je 1.</span><span class="sxs-lookup"><span data-stu-id="a94bd-271">Navigate returns Ref\<T> if the cardinality of the to end is 1.</span></span> <span data-ttu-id="a94bd-272">Pokud mohutnost do konce je n, kolekce\<<Ref T>> budou vráceny.</span><span class="sxs-lookup"><span data-stu-id="a94bd-272">If the cardinality of the to end is n, the Collection<Ref\<T>> will be returned.</span></span>  
  
 <span data-ttu-id="a94bd-273">Příklad:</span><span class="sxs-lookup"><span data-stu-id="a94bd-273">Example:</span></span>  
  
```sql  
SELECT a.AddressID, (SELECT VALUE DEREF(v) FROM
    NAVIGATE(a, AdventureWorksModel.FK_SalesOrderHeader_Address_BillToAddressID) AS v)
    FROM AdventureWorksEntities.Address AS a  
```  
  
 <span data-ttu-id="a94bd-274">Výstup:</span><span class="sxs-lookup"><span data-stu-id="a94bd-274">Output:</span></span>  
  
|<span data-ttu-id="a94bd-275">Adresní ID</span><span class="sxs-lookup"><span data-stu-id="a94bd-275">AddressID</span></span>|  
|---------------|  
|<span data-ttu-id="a94bd-276">1</span><span class="sxs-lookup"><span data-stu-id="a94bd-276">1</span></span>|  
|<span data-ttu-id="a94bd-277">2</span><span class="sxs-lookup"><span data-stu-id="a94bd-277">2</span></span>|  
|<span data-ttu-id="a94bd-278">3</span><span class="sxs-lookup"><span data-stu-id="a94bd-278">3</span></span>|  
|<span data-ttu-id="a94bd-279">...</span><span class="sxs-lookup"><span data-stu-id="a94bd-279">...</span></span>|  
  
## <a name="select-value-and-select"></a><span data-ttu-id="a94bd-280">VYBRAT HODNOTU A VYBRAT</span><span class="sxs-lookup"><span data-stu-id="a94bd-280">SELECT VALUE AND SELECT</span></span>  
  
### <a name="select-value"></a><span data-ttu-id="a94bd-281">VYBRAT HODNOTU</span><span class="sxs-lookup"><span data-stu-id="a94bd-281">SELECT VALUE</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="a94bd-282">poskytuje klauzuli SELECT VALUE přeskočit implicitní konstrukci řádku.</span><span class="sxs-lookup"><span data-stu-id="a94bd-282">provides the SELECT VALUE clause to skip the implicit row construction.</span></span> <span data-ttu-id="a94bd-283">V klauzuli SELECT VALUE lze zadat pouze jednu položku.</span><span class="sxs-lookup"><span data-stu-id="a94bd-283">Only one item can be specified in a SELECT VALUE clause.</span></span> <span data-ttu-id="a94bd-284">Při použití takové klauzule je vytvořen anulování řádku kolem položky v select klauzule a kolekce požadovaného tvaru lze vytvořit, například: `SELECT VALUE a`.</span><span class="sxs-lookup"><span data-stu-id="a94bd-284">When such a clause is used, no row wrapper is constructed around the items in the SELECT clause, and a collection of the desired shape can be produced, for example: `SELECT VALUE a`.</span></span>  
  
 <span data-ttu-id="a94bd-285">Příklad:</span><span class="sxs-lookup"><span data-stu-id="a94bd-285">Example:</span></span>  
  
```sql  
SELECT VALUE p.Name FROM AdventureWorksEntities.Product AS p
```  
  
 <span data-ttu-id="a94bd-286">Výstup:</span><span class="sxs-lookup"><span data-stu-id="a94bd-286">Output:</span></span>  
  
|<span data-ttu-id="a94bd-287">Name (Název)</span><span class="sxs-lookup"><span data-stu-id="a94bd-287">Name</span></span>|  
|----------|  
|<span data-ttu-id="a94bd-288">Nastavitelná rasa</span><span class="sxs-lookup"><span data-stu-id="a94bd-288">Adjustable Race</span></span>|  
|<span data-ttu-id="a94bd-289">Univerzální stojan na kola</span><span class="sxs-lookup"><span data-stu-id="a94bd-289">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="a94bd-290">Víčko loga AWC</span><span class="sxs-lookup"><span data-stu-id="a94bd-290">AWC Logo Cap</span></span>|  
|<span data-ttu-id="a94bd-291">...</span><span class="sxs-lookup"><span data-stu-id="a94bd-291">...</span></span>|  
  
### <a name="select"></a><span data-ttu-id="a94bd-292">SELECT</span><span class="sxs-lookup"><span data-stu-id="a94bd-292">SELECT</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="a94bd-293">také poskytuje konstruktor řádku pro vytvoření libovolných řádků.</span><span class="sxs-lookup"><span data-stu-id="a94bd-293">also provides the row constructor to construct arbitrary rows.</span></span> <span data-ttu-id="a94bd-294">SELECT převezme jeden nebo více prvků v projekci a `SELECT a, b, c`výsledkem je datový záznam s poli, například: .</span><span class="sxs-lookup"><span data-stu-id="a94bd-294">SELECT takes one or more elements in the projection and results in a data record with fields, for example: `SELECT a, b, c`.</span></span>  
  
 <span data-ttu-id="a94bd-295">Příklad:</span><span class="sxs-lookup"><span data-stu-id="a94bd-295">Example:</span></span>  
  
 <span data-ttu-id="a94bd-296">SELECT p.Name, p.ProductID from AdventureWorksEntities.Product as p Výstup:</span><span class="sxs-lookup"><span data-stu-id="a94bd-296">SELECT p.Name, p.ProductID FROM AdventureWorksEntities.Product as p Output:</span></span>  
  
|<span data-ttu-id="a94bd-297">Name (Název)</span><span class="sxs-lookup"><span data-stu-id="a94bd-297">Name</span></span>|<span data-ttu-id="a94bd-298">ProductID</span><span class="sxs-lookup"><span data-stu-id="a94bd-298">ProductID</span></span>|  
|----------|---------------|  
|<span data-ttu-id="a94bd-299">Nastavitelná rasa</span><span class="sxs-lookup"><span data-stu-id="a94bd-299">Adjustable Race</span></span>|<span data-ttu-id="a94bd-300">1</span><span class="sxs-lookup"><span data-stu-id="a94bd-300">1</span></span>|  
|<span data-ttu-id="a94bd-301">Univerzální stojan na kola</span><span class="sxs-lookup"><span data-stu-id="a94bd-301">All-Purpose Bike Stand</span></span>|<span data-ttu-id="a94bd-302">879</span><span class="sxs-lookup"><span data-stu-id="a94bd-302">879</span></span>|  
|<span data-ttu-id="a94bd-303">Víčko loga AWC</span><span class="sxs-lookup"><span data-stu-id="a94bd-303">AWC Logo Cap</span></span>|<span data-ttu-id="a94bd-304">712</span><span class="sxs-lookup"><span data-stu-id="a94bd-304">712</span></span>|  
|<span data-ttu-id="a94bd-305">...</span><span class="sxs-lookup"><span data-stu-id="a94bd-305">...</span></span>|<span data-ttu-id="a94bd-306">...</span><span class="sxs-lookup"><span data-stu-id="a94bd-306">...</span></span>|  
  
## <a name="case-expression"></a><span data-ttu-id="a94bd-307">VÝRAZ PŘÍPADU</span><span class="sxs-lookup"><span data-stu-id="a94bd-307">CASE EXPRESSION</span></span>  
 <span data-ttu-id="a94bd-308">[Výraz případu](case-entity-sql.md) vyhodnotí sadu logických výrazů k určení výsledku.</span><span class="sxs-lookup"><span data-stu-id="a94bd-308">The [case expression](case-entity-sql.md) evaluates a set of Boolean expressions to determine the result.</span></span>  
  
 <span data-ttu-id="a94bd-309">Příklad:</span><span class="sxs-lookup"><span data-stu-id="a94bd-309">Example:</span></span>  
  
```sql  
CASE WHEN AVG({25,12,11}) < 100 THEN TRUE ELSE FALSE END  
```  
  
 <span data-ttu-id="a94bd-310">Výstup:</span><span class="sxs-lookup"><span data-stu-id="a94bd-310">Output:</span></span>  
  
|<span data-ttu-id="a94bd-311">Hodnota</span><span class="sxs-lookup"><span data-stu-id="a94bd-311">Value</span></span>|  
|-----------|  
|<span data-ttu-id="a94bd-312">TRUE</span><span class="sxs-lookup"><span data-stu-id="a94bd-312">TRUE</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a94bd-313">Viz také</span><span class="sxs-lookup"><span data-stu-id="a94bd-313">See also</span></span>

- [<span data-ttu-id="a94bd-314">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="a94bd-314">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="a94bd-315">Přehled Entity SQL</span><span class="sxs-lookup"><span data-stu-id="a94bd-315">Entity SQL Overview</span></span>](entity-sql-overview.md)
