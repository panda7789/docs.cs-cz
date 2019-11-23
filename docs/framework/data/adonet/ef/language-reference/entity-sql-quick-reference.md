---
title: Stručné reference k Entity SQL
ms.date: 03/30/2017
ms.assetid: e53dad9e-5e83-426e-abb4-be3e78e3d6dc
ms.openlocfilehash: 9ccfc461d394af8804c960ebf460e7fbfb025b64
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833877"
---
# <a name="entity-sql-quick-reference"></a><span data-ttu-id="5fbfc-102">Stručné reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="5fbfc-102">Entity SQL Quick Reference</span></span>
<span data-ttu-id="5fbfc-103">V tomto tématu najdete stručný přehled [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dotazů.</span><span class="sxs-lookup"><span data-stu-id="5fbfc-103">This topic provides a quick reference to [!INCLUDE[esql](../../../../../../includes/esql-md.md)] queries.</span></span> <span data-ttu-id="5fbfc-104">Dotazy v tomto tématu jsou založené na modelu prodeje společnosti AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="5fbfc-104">The queries in this topic are based on the AdventureWorks Sales model.</span></span>  
  
## <a name="literals"></a><span data-ttu-id="5fbfc-105">Literály</span><span class="sxs-lookup"><span data-stu-id="5fbfc-105">Literals</span></span>  
  
### <a name="string"></a><span data-ttu-id="5fbfc-106">String</span><span class="sxs-lookup"><span data-stu-id="5fbfc-106">String</span></span>  
 <span data-ttu-id="5fbfc-107">Existují řetězcové literály znaků Unicode a non-Unicode.</span><span class="sxs-lookup"><span data-stu-id="5fbfc-107">There are Unicode and non-Unicode character string literals.</span></span> <span data-ttu-id="5fbfc-108">K řetězcům Unicode jsou předpony N. Například `N'hello'`.</span><span class="sxs-lookup"><span data-stu-id="5fbfc-108">Unicode strings are prepended with N. For example, `N'hello'`.</span></span>  
  
 <span data-ttu-id="5fbfc-109">Následuje příklad řetězcového literálu, který není Unicode:</span><span class="sxs-lookup"><span data-stu-id="5fbfc-109">The following is an example of a Non-Unicode string literal:</span></span>  
  
```sql  
'hello'  
--same as  
"hello"  
```  
  
 <span data-ttu-id="5fbfc-110">Výstup:</span><span class="sxs-lookup"><span data-stu-id="5fbfc-110">Output:</span></span>  
  
|<span data-ttu-id="5fbfc-111">Hodnota</span><span class="sxs-lookup"><span data-stu-id="5fbfc-111">Value</span></span>|  
|-----------|  
|<span data-ttu-id="5fbfc-112">Dobrý den</span><span class="sxs-lookup"><span data-stu-id="5fbfc-112">hello</span></span>|  
  
### <a name="datetime"></a><span data-ttu-id="5fbfc-113">Datum a čas</span><span class="sxs-lookup"><span data-stu-id="5fbfc-113">DateTime</span></span>  
 <span data-ttu-id="5fbfc-114">V literálech DateTime jsou části data a času povinné.</span><span class="sxs-lookup"><span data-stu-id="5fbfc-114">In DateTime literals, both date and time parts are mandatory.</span></span> <span data-ttu-id="5fbfc-115">Neexistují žádné výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="5fbfc-115">There are no default values.</span></span>  
  
 <span data-ttu-id="5fbfc-116">Příklad:</span><span class="sxs-lookup"><span data-stu-id="5fbfc-116">Example:</span></span>  
  
```sql  
DATETIME '2006-12-25 01:01:00.000'   
--same as  
DATETIME '2006-12-25 01:01'  
```  
  
 <span data-ttu-id="5fbfc-117">Výstup:</span><span class="sxs-lookup"><span data-stu-id="5fbfc-117">Output:</span></span>  
  
|<span data-ttu-id="5fbfc-118">Hodnota</span><span class="sxs-lookup"><span data-stu-id="5fbfc-118">Value</span></span>|  
|-----------|  
|<span data-ttu-id="5fbfc-119">12/25/2006 1:01:00 DOP.</span><span class="sxs-lookup"><span data-stu-id="5fbfc-119">12/25/2006 1:01:00 AM</span></span>|  
  
### <a name="integer"></a><span data-ttu-id="5fbfc-120">Celé číslo</span><span class="sxs-lookup"><span data-stu-id="5fbfc-120">Integer</span></span>  
 <span data-ttu-id="5fbfc-121">Celočíselné literály můžou být typu Int32 (123), UInt32 (123U), Int64 (123L) a UInt64 (123UL).</span><span class="sxs-lookup"><span data-stu-id="5fbfc-121">Integer literals can be of type Int32 (123), UInt32 (123U), Int64 (123L), and UInt64 (123UL).</span></span>  
  
 <span data-ttu-id="5fbfc-122">Příklad:</span><span class="sxs-lookup"><span data-stu-id="5fbfc-122">Example:</span></span>  
  
```sql  
--a collection of integers  
{1, 2, 3}  
```  
  
 <span data-ttu-id="5fbfc-123">Výstup:</span><span class="sxs-lookup"><span data-stu-id="5fbfc-123">Output:</span></span>  
  
|<span data-ttu-id="5fbfc-124">Hodnota</span><span class="sxs-lookup"><span data-stu-id="5fbfc-124">Value</span></span>|  
|-----------|  
|<span data-ttu-id="5fbfc-125">1</span><span class="sxs-lookup"><span data-stu-id="5fbfc-125">1</span></span>|  
|<span data-ttu-id="5fbfc-126">2</span><span class="sxs-lookup"><span data-stu-id="5fbfc-126">2</span></span>|  
|<span data-ttu-id="5fbfc-127">3</span><span class="sxs-lookup"><span data-stu-id="5fbfc-127">3</span></span>|  
  
### <a name="other"></a><span data-ttu-id="5fbfc-128">Další</span><span class="sxs-lookup"><span data-stu-id="5fbfc-128">Other</span></span>  
 <span data-ttu-id="5fbfc-129">Další literály podporované [!INCLUDE[esql](../../../../../../includes/esql-md.md)] jsou GUID, binary, float, Double, Decimal a `null`.</span><span class="sxs-lookup"><span data-stu-id="5fbfc-129">Other literals supported by [!INCLUDE[esql](../../../../../../includes/esql-md.md)] are Guid, Binary, Float/Double, Decimal, and `null`.</span></span> <span data-ttu-id="5fbfc-130">Literály null v [!INCLUDE[esql](../../../../../../includes/esql-md.md)] jsou považovány za kompatibilní s každým jiným typem v koncepčním modelu.</span><span class="sxs-lookup"><span data-stu-id="5fbfc-130">Null literals in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] are considered to be compatible with every other type in the conceptual model.</span></span>  
  
## <a name="type-constructors"></a><span data-ttu-id="5fbfc-131">Konstruktory typů</span><span class="sxs-lookup"><span data-stu-id="5fbfc-131">Type Constructors</span></span>  
  
### <a name="row"></a><span data-ttu-id="5fbfc-132">ROW</span><span class="sxs-lookup"><span data-stu-id="5fbfc-132">ROW</span></span>  
 <span data-ttu-id="5fbfc-133">[Řádek](row-entity-sql.md) vytvoří anonymní, strukturálně napsané (záznam) hodnoty jako v: `ROW(1 AS myNumber, ‘Name’ AS myName).`</span><span class="sxs-lookup"><span data-stu-id="5fbfc-133">[ROW](row-entity-sql.md) constructs an anonymous, structurally-typed (record) value as in: `ROW(1 AS myNumber, ‘Name’ AS myName).`</span></span>  
  
 <span data-ttu-id="5fbfc-134">Příklad:</span><span class="sxs-lookup"><span data-stu-id="5fbfc-134">Example:</span></span>  
  
```sql  
SELECT VALUE row (product.ProductID AS ProductID, product.Name
    AS ProductName) FROM AdventureWorksEntities.Product AS product
```  
  
 <span data-ttu-id="5fbfc-135">Výstup:</span><span class="sxs-lookup"><span data-stu-id="5fbfc-135">Output:</span></span>  
  
|<span data-ttu-id="5fbfc-136">ProductID</span><span class="sxs-lookup"><span data-stu-id="5fbfc-136">ProductID</span></span>|<span data-ttu-id="5fbfc-137">Název</span><span class="sxs-lookup"><span data-stu-id="5fbfc-137">Name</span></span>|  
|---------------|----------|  
|<span data-ttu-id="5fbfc-138">1</span><span class="sxs-lookup"><span data-stu-id="5fbfc-138">1</span></span>|<span data-ttu-id="5fbfc-139">Přizpůsobitelná rasy</span><span class="sxs-lookup"><span data-stu-id="5fbfc-139">Adjustable Race</span></span>|  
|<span data-ttu-id="5fbfc-140">879</span><span class="sxs-lookup"><span data-stu-id="5fbfc-140">879</span></span>|<span data-ttu-id="5fbfc-141">Stojan kol pro všechny účely</span><span class="sxs-lookup"><span data-stu-id="5fbfc-141">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="5fbfc-142">712</span><span class="sxs-lookup"><span data-stu-id="5fbfc-142">712</span></span>|<span data-ttu-id="5fbfc-143">AWC Logo Cap</span><span class="sxs-lookup"><span data-stu-id="5fbfc-143">AWC Logo Cap</span></span>|  
|<span data-ttu-id="5fbfc-144">...</span><span class="sxs-lookup"><span data-stu-id="5fbfc-144">...</span></span>|<span data-ttu-id="5fbfc-145">...</span><span class="sxs-lookup"><span data-stu-id="5fbfc-145">...</span></span>|  
  
### <a name="multiset"></a><span data-ttu-id="5fbfc-146">MULTISET</span><span class="sxs-lookup"><span data-stu-id="5fbfc-146">MULTISET</span></span>  
 <span data-ttu-id="5fbfc-147">[MULTISET](multiset-entity-sql.md) sestaví kolekce, například:</span><span class="sxs-lookup"><span data-stu-id="5fbfc-147">[MULTISET](multiset-entity-sql.md) constructs collections, such as:</span></span>  
  
 <span data-ttu-id="5fbfc-148">`MULTISET(1,2,2,3)` `--same as`-`{1,2,2,3}.`</span><span class="sxs-lookup"><span data-stu-id="5fbfc-148">`MULTISET(1,2,2,3)` `--same as`-`{1,2,2,3}.`</span></span>  
  
 <span data-ttu-id="5fbfc-149">Příklad:</span><span class="sxs-lookup"><span data-stu-id="5fbfc-149">Example:</span></span>  
  
```sql  
SELECT VALUE product FROM AdventureWorksEntities.Product AS product WHERE product.ListPrice IN MultiSet (125, 300)  
```  
  
 <span data-ttu-id="5fbfc-150">Výstup:</span><span class="sxs-lookup"><span data-stu-id="5fbfc-150">Output:</span></span>  
  
|<span data-ttu-id="5fbfc-151">ProductID</span><span class="sxs-lookup"><span data-stu-id="5fbfc-151">ProductID</span></span>|<span data-ttu-id="5fbfc-152">Název</span><span class="sxs-lookup"><span data-stu-id="5fbfc-152">Name</span></span>|<span data-ttu-id="5fbfc-153">ProductNumber</span><span class="sxs-lookup"><span data-stu-id="5fbfc-153">ProductNumber</span></span>|<span data-ttu-id="5fbfc-154">…</span><span class="sxs-lookup"><span data-stu-id="5fbfc-154">…</span></span>|  
|---------------|----------|-------------------|-------|  
|<span data-ttu-id="5fbfc-155">842</span><span class="sxs-lookup"><span data-stu-id="5fbfc-155">842</span></span>|<span data-ttu-id="5fbfc-156">Touring – Panniers, velký</span><span class="sxs-lookup"><span data-stu-id="5fbfc-156">Touring-Panniers, Large</span></span>|<span data-ttu-id="5fbfc-157">PA-T100</span><span class="sxs-lookup"><span data-stu-id="5fbfc-157">PA-T100</span></span>|<span data-ttu-id="5fbfc-158">…</span><span class="sxs-lookup"><span data-stu-id="5fbfc-158">…</span></span>|  
  
### <a name="object"></a><span data-ttu-id="5fbfc-159">Objekt</span><span class="sxs-lookup"><span data-stu-id="5fbfc-159">Object</span></span>  
 <span data-ttu-id="5fbfc-160">[Konstruktor pojmenovaného typu](named-type-constructor-entity-sql.md) konstrukce (pojmenované) uživatelsky definované objekty, například `person("abc", 12)`.</span><span class="sxs-lookup"><span data-stu-id="5fbfc-160">[Named Type Constructor](named-type-constructor-entity-sql.md) constructs (named) user-defined objects, such as `person("abc", 12)`.</span></span>  
  
 <span data-ttu-id="5fbfc-161">Příklad:</span><span class="sxs-lookup"><span data-stu-id="5fbfc-161">Example:</span></span>  
  
```sql  
SELECT VALUE AdventureWorksModel.SalesOrderDetail (o.SalesOrderDetailID, o.CarrierTrackingNumber, o.OrderQty,   
o.ProductID, o.SpecialOfferID, o.UnitPrice, o.UnitPriceDiscount,   
o.rowguid, o.ModifiedDate) FROM AdventureWorksEntities.SalesOrderDetail   
AS o  
```  
  
 <span data-ttu-id="5fbfc-162">Výstup:</span><span class="sxs-lookup"><span data-stu-id="5fbfc-162">Output:</span></span>  
  
|<span data-ttu-id="5fbfc-163">SalesOrderDetailID</span><span class="sxs-lookup"><span data-stu-id="5fbfc-163">SalesOrderDetailID</span></span>|<span data-ttu-id="5fbfc-164">CarrierTrackingNumber</span><span class="sxs-lookup"><span data-stu-id="5fbfc-164">CarrierTrackingNumber</span></span>|<span data-ttu-id="5fbfc-165">OrderQty</span><span class="sxs-lookup"><span data-stu-id="5fbfc-165">OrderQty</span></span>|<span data-ttu-id="5fbfc-166">ProductID</span><span class="sxs-lookup"><span data-stu-id="5fbfc-166">ProductID</span></span>|<span data-ttu-id="5fbfc-167">...</span><span class="sxs-lookup"><span data-stu-id="5fbfc-167">...</span></span>|  
|------------------------|---------------------------|--------------|---------------|---------|  
|<span data-ttu-id="5fbfc-168">1</span><span class="sxs-lookup"><span data-stu-id="5fbfc-168">1</span></span>|<span data-ttu-id="5fbfc-169">4911-403C-98</span><span class="sxs-lookup"><span data-stu-id="5fbfc-169">4911-403C-98</span></span>|<span data-ttu-id="5fbfc-170">1</span><span class="sxs-lookup"><span data-stu-id="5fbfc-170">1</span></span>|<span data-ttu-id="5fbfc-171">776</span><span class="sxs-lookup"><span data-stu-id="5fbfc-171">776</span></span>|<span data-ttu-id="5fbfc-172">...</span><span class="sxs-lookup"><span data-stu-id="5fbfc-172">...</span></span>|  
|<span data-ttu-id="5fbfc-173">2</span><span class="sxs-lookup"><span data-stu-id="5fbfc-173">2</span></span>|<span data-ttu-id="5fbfc-174">4911-403C-98</span><span class="sxs-lookup"><span data-stu-id="5fbfc-174">4911-403C-98</span></span>|<span data-ttu-id="5fbfc-175">3</span><span class="sxs-lookup"><span data-stu-id="5fbfc-175">3</span></span>|<span data-ttu-id="5fbfc-176">777</span><span class="sxs-lookup"><span data-stu-id="5fbfc-176">777</span></span>|<span data-ttu-id="5fbfc-177">...</span><span class="sxs-lookup"><span data-stu-id="5fbfc-177">...</span></span>|  
|<span data-ttu-id="5fbfc-178">...</span><span class="sxs-lookup"><span data-stu-id="5fbfc-178">...</span></span>|<span data-ttu-id="5fbfc-179">...</span><span class="sxs-lookup"><span data-stu-id="5fbfc-179">...</span></span>|<span data-ttu-id="5fbfc-180">...</span><span class="sxs-lookup"><span data-stu-id="5fbfc-180">...</span></span>|<span data-ttu-id="5fbfc-181">...</span><span class="sxs-lookup"><span data-stu-id="5fbfc-181">...</span></span>|<span data-ttu-id="5fbfc-182">...</span><span class="sxs-lookup"><span data-stu-id="5fbfc-182">...</span></span>|  
  
## <a name="references"></a><span data-ttu-id="5fbfc-183">Reference</span><span class="sxs-lookup"><span data-stu-id="5fbfc-183">References</span></span>  
  
### <a name="ref"></a><span data-ttu-id="5fbfc-184">REF</span><span class="sxs-lookup"><span data-stu-id="5fbfc-184">REF</span></span>  
 <span data-ttu-id="5fbfc-185">[Odkaz vytvoří odkaz](ref-entity-sql.md) na instanci typu entity.</span><span class="sxs-lookup"><span data-stu-id="5fbfc-185">[REF](ref-entity-sql.md) creates a reference to an entity type instance.</span></span> <span data-ttu-id="5fbfc-186">Následující dotaz například vrátí odkazy na každou entitu objednávky v sadě entit Orders:</span><span class="sxs-lookup"><span data-stu-id="5fbfc-186">For example, the following query returns references to each Order entity in the Orders entity set:</span></span>  
  
```sql  
SELECT REF(o) AS OrderID FROM Orders AS o  
```  
  
 <span data-ttu-id="5fbfc-187">Výstup:</span><span class="sxs-lookup"><span data-stu-id="5fbfc-187">Output:</span></span>  
  
|<span data-ttu-id="5fbfc-188">Hodnota</span><span class="sxs-lookup"><span data-stu-id="5fbfc-188">Value</span></span>|  
|-----------|  
|<span data-ttu-id="5fbfc-189">1</span><span class="sxs-lookup"><span data-stu-id="5fbfc-189">1</span></span>|  
|<span data-ttu-id="5fbfc-190">2</span><span class="sxs-lookup"><span data-stu-id="5fbfc-190">2</span></span>|  
|<span data-ttu-id="5fbfc-191">3</span><span class="sxs-lookup"><span data-stu-id="5fbfc-191">3</span></span>|  
|<span data-ttu-id="5fbfc-192">...</span><span class="sxs-lookup"><span data-stu-id="5fbfc-192">...</span></span>|  
  
 <span data-ttu-id="5fbfc-193">Následující příklad používá operátor extrakce vlastností (.) pro přístup k vlastnosti entity.</span><span class="sxs-lookup"><span data-stu-id="5fbfc-193">The following example uses the property extraction operator (.) to access a property of an entity.</span></span> <span data-ttu-id="5fbfc-194">Při použití operátoru extrakce vlastností je odkaz automaticky odkázat.</span><span class="sxs-lookup"><span data-stu-id="5fbfc-194">When the property extraction operator is used, the reference is automatically dereferenced.</span></span>  
  
 <span data-ttu-id="5fbfc-195">Příklad:</span><span class="sxs-lookup"><span data-stu-id="5fbfc-195">Example:</span></span>  
  
```sql  
SELECT VALUE REF(p).Name FROM   
    AdventureWorksEntities.Product AS p
```  
  
 <span data-ttu-id="5fbfc-196">Výstup:</span><span class="sxs-lookup"><span data-stu-id="5fbfc-196">Output:</span></span>  
  
|<span data-ttu-id="5fbfc-197">Hodnota</span><span class="sxs-lookup"><span data-stu-id="5fbfc-197">Value</span></span>|  
|-----------|  
|<span data-ttu-id="5fbfc-198">Přizpůsobitelná rasy</span><span class="sxs-lookup"><span data-stu-id="5fbfc-198">Adjustable Race</span></span>|  
|<span data-ttu-id="5fbfc-199">Stojan kol pro všechny účely</span><span class="sxs-lookup"><span data-stu-id="5fbfc-199">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="5fbfc-200">AWC Logo Cap</span><span class="sxs-lookup"><span data-stu-id="5fbfc-200">AWC Logo Cap</span></span>|  
|<span data-ttu-id="5fbfc-201">...</span><span class="sxs-lookup"><span data-stu-id="5fbfc-201">...</span></span>|  
  
### <a name="deref"></a><span data-ttu-id="5fbfc-202">DEREF</span><span class="sxs-lookup"><span data-stu-id="5fbfc-202">DEREF</span></span>  
 <span data-ttu-id="5fbfc-203">[DEREF](deref-entity-sql.md) odkazuje na referenční hodnotu a vytváří výsledek tohoto odkázání.</span><span class="sxs-lookup"><span data-stu-id="5fbfc-203">[DEREF](deref-entity-sql.md) dereferences a reference value and produces the result of that dereference.</span></span> <span data-ttu-id="5fbfc-204">Následující dotaz například generuje entity Order pro jednotlivé objednávky v sadě entit Orders: `SELECT DEREF(o2.r) FROM (SELECT REF(o) AS r FROM LOB.Orders AS o) AS o2`..</span><span class="sxs-lookup"><span data-stu-id="5fbfc-204">For example, the following query produces the Order entities for each Order in the Orders entity set: `SELECT DEREF(o2.r) FROM (SELECT REF(o) AS r FROM LOB.Orders AS o) AS o2`..</span></span>  
  
 <span data-ttu-id="5fbfc-205">Příklad:</span><span class="sxs-lookup"><span data-stu-id="5fbfc-205">Example:</span></span>  
  
```sql  
SELECT VALUE DEREF(REF(p)).Name FROM   
    AdventureWorksEntities.Product AS p
```  
  
 <span data-ttu-id="5fbfc-206">Výstup:</span><span class="sxs-lookup"><span data-stu-id="5fbfc-206">Output:</span></span>  
  
|<span data-ttu-id="5fbfc-207">Hodnota</span><span class="sxs-lookup"><span data-stu-id="5fbfc-207">Value</span></span>|  
|-----------|  
|<span data-ttu-id="5fbfc-208">Přizpůsobitelná rasy</span><span class="sxs-lookup"><span data-stu-id="5fbfc-208">Adjustable Race</span></span>|  
|<span data-ttu-id="5fbfc-209">Stojan kol pro všechny účely</span><span class="sxs-lookup"><span data-stu-id="5fbfc-209">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="5fbfc-210">AWC Logo Cap</span><span class="sxs-lookup"><span data-stu-id="5fbfc-210">AWC Logo Cap</span></span>|  
|<span data-ttu-id="5fbfc-211">...</span><span class="sxs-lookup"><span data-stu-id="5fbfc-211">...</span></span>|  
  
### <a name="createref-and-key"></a><span data-ttu-id="5fbfc-212">CREATEREF A KLÍČ</span><span class="sxs-lookup"><span data-stu-id="5fbfc-212">CREATEREF AND KEY</span></span>  
 <span data-ttu-id="5fbfc-213">[CREATEREF](createref-entity-sql.md) vytvoří odkaz, který projde klíč.</span><span class="sxs-lookup"><span data-stu-id="5fbfc-213">[CREATEREF](createref-entity-sql.md) creates a reference passing a key.</span></span> <span data-ttu-id="5fbfc-214">[Klíč](key-entity-sql.md) extrahuje klíčovou část výrazu s odkazem na typ.</span><span class="sxs-lookup"><span data-stu-id="5fbfc-214">[KEY](key-entity-sql.md) extracts the key portion of an expression with type reference.</span></span>  
  
 <span data-ttu-id="5fbfc-215">Příklad:</span><span class="sxs-lookup"><span data-stu-id="5fbfc-215">Example:</span></span>  
  
```sql  
SELECT VALUE Key(CreateRef(AdventureWorksEntities.Product, row(p.ProductID)))   
    FROM AdventureWorksEntities.Product AS p
```  
  
 <span data-ttu-id="5fbfc-216">Výstup:</span><span class="sxs-lookup"><span data-stu-id="5fbfc-216">Output:</span></span>  
  
|<span data-ttu-id="5fbfc-217">ProductID</span><span class="sxs-lookup"><span data-stu-id="5fbfc-217">ProductID</span></span>|  
|---------------|  
|<span data-ttu-id="5fbfc-218">980</span><span class="sxs-lookup"><span data-stu-id="5fbfc-218">980</span></span>|  
|<span data-ttu-id="5fbfc-219">365</span><span class="sxs-lookup"><span data-stu-id="5fbfc-219">365</span></span>|  
|<span data-ttu-id="5fbfc-220">771</span><span class="sxs-lookup"><span data-stu-id="5fbfc-220">771</span></span>|  
|<span data-ttu-id="5fbfc-221">...</span><span class="sxs-lookup"><span data-stu-id="5fbfc-221">...</span></span>|  
  
## <a name="functions"></a><span data-ttu-id="5fbfc-222">Funkce</span><span class="sxs-lookup"><span data-stu-id="5fbfc-222">Functions</span></span>  
  
### <a name="canonical"></a><span data-ttu-id="5fbfc-223">Canonical</span><span class="sxs-lookup"><span data-stu-id="5fbfc-223">Canonical</span></span>  
 <span data-ttu-id="5fbfc-224">Obor názvů pro [kanonické funkce](canonical-functions.md) je EDM, jak je uvedeno v `Edm.Length("string")`.</span><span class="sxs-lookup"><span data-stu-id="5fbfc-224">The namespace for [canonical functions](canonical-functions.md) is Edm, as in `Edm.Length("string")`.</span></span> <span data-ttu-id="5fbfc-225">Není nutné zadávat obor názvů, pokud není importován jiný obor názvů, který obsahuje funkci se stejným názvem jako kanonická funkce.</span><span class="sxs-lookup"><span data-stu-id="5fbfc-225">You do not have to specify the namespace unless another namespace is imported that contains a function with the same name as a canonical function.</span></span> <span data-ttu-id="5fbfc-226">Pokud mají dva obory názvů stejnou funkci, měl by uživatel určit celé jméno.</span><span class="sxs-lookup"><span data-stu-id="5fbfc-226">If two namespaces have the same function, the user should specific the full name.</span></span>  
  
 <span data-ttu-id="5fbfc-227">Příklad:</span><span class="sxs-lookup"><span data-stu-id="5fbfc-227">Example:</span></span>  
  
```sql  
SELECT Length(c. FirstName) AS NameLen FROM
    AdventureWorksEntities.Contact AS c   
    WHERE c.ContactID BETWEEN 10 AND 12  
```  
  
 <span data-ttu-id="5fbfc-228">Výstup:</span><span class="sxs-lookup"><span data-stu-id="5fbfc-228">Output:</span></span>  
  
|<span data-ttu-id="5fbfc-229">NameLen</span><span class="sxs-lookup"><span data-stu-id="5fbfc-229">NameLen</span></span>|  
|-------------|  
|<span data-ttu-id="5fbfc-230">6</span><span class="sxs-lookup"><span data-stu-id="5fbfc-230">6</span></span>|  
|<span data-ttu-id="5fbfc-231">6</span><span class="sxs-lookup"><span data-stu-id="5fbfc-231">6</span></span>|  
|<span data-ttu-id="5fbfc-232">5</span><span class="sxs-lookup"><span data-stu-id="5fbfc-232">5</span></span>|  
  
### <a name="microsoft-provider-specific"></a><span data-ttu-id="5fbfc-233">Specifické pro poskytovatele Microsoftu</span><span class="sxs-lookup"><span data-stu-id="5fbfc-233">Microsoft Provider-Specific</span></span>  
 <span data-ttu-id="5fbfc-234">[Funkce specifické pro poskytovatele společnosti Microsoft](../sqlclient-for-ef-functions.md) jsou v oboru názvů `SqlServer`.</span><span class="sxs-lookup"><span data-stu-id="5fbfc-234">[Microsoft provider-specific functions](../sqlclient-for-ef-functions.md) are in the `SqlServer` namespace.</span></span>  
  
 <span data-ttu-id="5fbfc-235">Příklad:</span><span class="sxs-lookup"><span data-stu-id="5fbfc-235">Example:</span></span>  
  
```sql  
SELECT SqlServer.LEN(c.EmailAddress) AS EmailLen FROM
    AdventureWorksEntities.Contact AS c WHERE   
    c.ContactID BETWEEN 10 AND 12  
```  
  
 <span data-ttu-id="5fbfc-236">Výstup:</span><span class="sxs-lookup"><span data-stu-id="5fbfc-236">Output:</span></span>  
  
|<span data-ttu-id="5fbfc-237">EmailLen</span><span class="sxs-lookup"><span data-stu-id="5fbfc-237">EmailLen</span></span>|  
|--------------|  
|<span data-ttu-id="5fbfc-238">27</span><span class="sxs-lookup"><span data-stu-id="5fbfc-238">27</span></span>|  
|<span data-ttu-id="5fbfc-239">27</span><span class="sxs-lookup"><span data-stu-id="5fbfc-239">27</span></span>|  
|<span data-ttu-id="5fbfc-240">26</span><span class="sxs-lookup"><span data-stu-id="5fbfc-240">26</span></span>|  
  
## <a name="namespaces"></a><span data-ttu-id="5fbfc-241">Obory názvů</span><span class="sxs-lookup"><span data-stu-id="5fbfc-241">Namespaces</span></span>  
 <span data-ttu-id="5fbfc-242">[Použití](using-entity-sql.md) určuje obory názvů použité ve výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="5fbfc-242">[USING](using-entity-sql.md) specifies namespaces used in a query expression.</span></span>  
  
 <span data-ttu-id="5fbfc-243">Příklad:</span><span class="sxs-lookup"><span data-stu-id="5fbfc-243">Example:</span></span>  
  
```sql  
using SqlServer; LOWER('AA');  
```  
  
 <span data-ttu-id="5fbfc-244">Výstup:</span><span class="sxs-lookup"><span data-stu-id="5fbfc-244">Output:</span></span>  
  
|<span data-ttu-id="5fbfc-245">Hodnota</span><span class="sxs-lookup"><span data-stu-id="5fbfc-245">Value</span></span>|  
|-----------|  
|<span data-ttu-id="5fbfc-246">aa</span><span class="sxs-lookup"><span data-stu-id="5fbfc-246">aa</span></span>|  
  
## <a name="paging"></a><span data-ttu-id="5fbfc-247">Stránkování</span><span class="sxs-lookup"><span data-stu-id="5fbfc-247">Paging</span></span>  
 <span data-ttu-id="5fbfc-248">Stránkování lze vyjádřit deklarováním dílčích klauzulí [Skip](skip-entity-sql.md) a [limit](limit-entity-sql.md) na klauzuli [ORDER by](order-by-entity-sql.md) .</span><span class="sxs-lookup"><span data-stu-id="5fbfc-248">Paging can be expressed by declaring a [SKIP](skip-entity-sql.md) and [LIMIT](limit-entity-sql.md) sub-clauses to the [ORDER BY](order-by-entity-sql.md) clause.</span></span>  
  
 <span data-ttu-id="5fbfc-249">Příklad:</span><span class="sxs-lookup"><span data-stu-id="5fbfc-249">Example:</span></span>  
  
```sql  
SELECT c.ContactID as ID, c.LastName AS Name FROM
    AdventureWorks.Contact AS c ORDER BY c.ContactID SKIP 9 LIMIT 3;  
```  
  
 <span data-ttu-id="5fbfc-250">Výstup:</span><span class="sxs-lookup"><span data-stu-id="5fbfc-250">Output:</span></span>  
  
|<span data-ttu-id="5fbfc-251">ID</span><span class="sxs-lookup"><span data-stu-id="5fbfc-251">ID</span></span>|<span data-ttu-id="5fbfc-252">Název</span><span class="sxs-lookup"><span data-stu-id="5fbfc-252">Name</span></span>|  
|--------|----------|  
|<span data-ttu-id="5fbfc-253">10</span><span class="sxs-lookup"><span data-stu-id="5fbfc-253">10</span></span>|<span data-ttu-id="5fbfc-254">Adina</span><span class="sxs-lookup"><span data-stu-id="5fbfc-254">Adina</span></span>|  
|<span data-ttu-id="5fbfc-255">11</span><span class="sxs-lookup"><span data-stu-id="5fbfc-255">11</span></span>|<span data-ttu-id="5fbfc-256">Agcaoili</span><span class="sxs-lookup"><span data-stu-id="5fbfc-256">Agcaoili</span></span>|  
|<span data-ttu-id="5fbfc-257">12</span><span class="sxs-lookup"><span data-stu-id="5fbfc-257">12</span></span>|<span data-ttu-id="5fbfc-258">Aguilar</span><span class="sxs-lookup"><span data-stu-id="5fbfc-258">Aguilar</span></span>|  
  
## <a name="grouping"></a><span data-ttu-id="5fbfc-259">Seskupování</span><span class="sxs-lookup"><span data-stu-id="5fbfc-259">Grouping</span></span>  
 <span data-ttu-id="5fbfc-260">[Seskupení podle](group-by-entity-sql.md) určuje skupiny, do kterých se mají umístit objekty vrácené výrazem dotazu ([Select](select-entity-sql.md)).</span><span class="sxs-lookup"><span data-stu-id="5fbfc-260">[GROUPING BY](group-by-entity-sql.md) specifies groups into which objects returned by a query ([SELECT](select-entity-sql.md)) expression are to be placed.</span></span>  
  
 <span data-ttu-id="5fbfc-261">Příklad:</span><span class="sxs-lookup"><span data-stu-id="5fbfc-261">Example:</span></span>  
  
```sql  
SELECT VALUE name FROM AdventureWorksEntities.Product AS P
    GROUP BY P.Name HAVING MAX(P.ListPrice) > 5  
```  
  
 <span data-ttu-id="5fbfc-262">Výstup:</span><span class="sxs-lookup"><span data-stu-id="5fbfc-262">Output:</span></span>  
  
|<span data-ttu-id="5fbfc-263">name</span><span class="sxs-lookup"><span data-stu-id="5fbfc-263">name</span></span>|  
|----------|  
|<span data-ttu-id="5fbfc-264">Sestavení pro horská místa</span><span class="sxs-lookup"><span data-stu-id="5fbfc-264">LL Mountain Seat Assembly</span></span>|  
|<span data-ttu-id="5fbfc-265">Sestavení ML horských sedadel</span><span class="sxs-lookup"><span data-stu-id="5fbfc-265">ML Mountain Seat Assembly</span></span>|  
|<span data-ttu-id="5fbfc-266">HL – sestavení pracovních stanic</span><span class="sxs-lookup"><span data-stu-id="5fbfc-266">HL Mountain Seat Assembly</span></span>|  
|<span data-ttu-id="5fbfc-267">...</span><span class="sxs-lookup"><span data-stu-id="5fbfc-267">...</span></span>|  
  
## <a name="navigation"></a><span data-ttu-id="5fbfc-268">Navigace</span><span class="sxs-lookup"><span data-stu-id="5fbfc-268">Navigation</span></span>  
 <span data-ttu-id="5fbfc-269">Operátor navigace mezi relacemi umožňuje procházet relaci z jedné entity (od konce) do jiné (do konce).</span><span class="sxs-lookup"><span data-stu-id="5fbfc-269">The relationship navigation operator allows you to navigate over the relationship from one entity (from end) to another (to end).</span></span> <span data-ttu-id="5fbfc-270">[Navigace](navigate-entity-sql.md) bere typ vztahu kvalifikovaný jako \<obor názvů >.\<název typu vztahu >.</span><span class="sxs-lookup"><span data-stu-id="5fbfc-270">[NAVIGATE](navigate-entity-sql.md) takes the relationship type qualified as \<namespace>.\<relationship type name>.</span></span> <span data-ttu-id="5fbfc-271">Funkce Navigate vrátí odkaz\<T >, pokud mohutnost má končit 1.</span><span class="sxs-lookup"><span data-stu-id="5fbfc-271">Navigate returns Ref\<T> if the cardinality of the to end is 1.</span></span> <span data-ttu-id="5fbfc-272">Pokud mohutnost koncového parametru má hodnotu n, bude vrácena kolekce < ref\<T > >.</span><span class="sxs-lookup"><span data-stu-id="5fbfc-272">If the cardinality of the to end is n, the Collection<Ref\<T>> will be returned.</span></span>  
  
 <span data-ttu-id="5fbfc-273">Příklad:</span><span class="sxs-lookup"><span data-stu-id="5fbfc-273">Example:</span></span>  
  
```sql  
SELECT a.AddressID, (SELECT VALUE DEREF(v) FROM   
    NAVIGATE(a, AdventureWorksModel.FK_SalesOrderHeader_Address_BillToAddressID) AS v)   
    FROM AdventureWorksEntities.Address AS a  
```  
  
 <span data-ttu-id="5fbfc-274">Výstup:</span><span class="sxs-lookup"><span data-stu-id="5fbfc-274">Output:</span></span>  
  
|<span data-ttu-id="5fbfc-275">AddressID</span><span class="sxs-lookup"><span data-stu-id="5fbfc-275">AddressID</span></span>|  
|---------------|  
|<span data-ttu-id="5fbfc-276">1</span><span class="sxs-lookup"><span data-stu-id="5fbfc-276">1</span></span>|  
|<span data-ttu-id="5fbfc-277">2</span><span class="sxs-lookup"><span data-stu-id="5fbfc-277">2</span></span>|  
|<span data-ttu-id="5fbfc-278">3</span><span class="sxs-lookup"><span data-stu-id="5fbfc-278">3</span></span>|  
|<span data-ttu-id="5fbfc-279">...</span><span class="sxs-lookup"><span data-stu-id="5fbfc-279">...</span></span>|  
  
## <a name="select-value-and-select"></a><span data-ttu-id="5fbfc-280">VYBERTE HODNOTU A VYBERTE</span><span class="sxs-lookup"><span data-stu-id="5fbfc-280">SELECT VALUE AND SELECT</span></span>  
  
### <a name="select-value"></a><span data-ttu-id="5fbfc-281">VYBRAT HODNOTU</span><span class="sxs-lookup"><span data-stu-id="5fbfc-281">SELECT VALUE</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="5fbfc-282">poskytuje klauzuli SELECT VALUE pro přeskočení vytváření implicitních řádků.</span><span class="sxs-lookup"><span data-stu-id="5fbfc-282">provides the SELECT VALUE clause to skip the implicit row construction.</span></span> <span data-ttu-id="5fbfc-283">V klauzuli SELECT VALUE lze zadat pouze jednu položku.</span><span class="sxs-lookup"><span data-stu-id="5fbfc-283">Only one item can be specified in a SELECT VALUE clause.</span></span> <span data-ttu-id="5fbfc-284">Je-li použita taková klauzule, není kolem položek v klauzuli SELECT vytvořena obálka řádku a může být vytvořena kolekce požadovaného tvaru, například: `SELECT VALUE a`.</span><span class="sxs-lookup"><span data-stu-id="5fbfc-284">When such a clause is used, no row wrapper is constructed around the items in the SELECT clause, and a collection of the desired shape can be produced, for example: `SELECT VALUE a`.</span></span>  
  
 <span data-ttu-id="5fbfc-285">Příklad:</span><span class="sxs-lookup"><span data-stu-id="5fbfc-285">Example:</span></span>  
  
```sql  
SELECT VALUE p.Name FROM AdventureWorksEntities.Product AS p
```  
  
 <span data-ttu-id="5fbfc-286">Výstup:</span><span class="sxs-lookup"><span data-stu-id="5fbfc-286">Output:</span></span>  
  
|<span data-ttu-id="5fbfc-287">Název</span><span class="sxs-lookup"><span data-stu-id="5fbfc-287">Name</span></span>|  
|----------|  
|<span data-ttu-id="5fbfc-288">Přizpůsobitelná rasy</span><span class="sxs-lookup"><span data-stu-id="5fbfc-288">Adjustable Race</span></span>|  
|<span data-ttu-id="5fbfc-289">Stojan kol pro všechny účely</span><span class="sxs-lookup"><span data-stu-id="5fbfc-289">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="5fbfc-290">AWC Logo Cap</span><span class="sxs-lookup"><span data-stu-id="5fbfc-290">AWC Logo Cap</span></span>|  
|<span data-ttu-id="5fbfc-291">...</span><span class="sxs-lookup"><span data-stu-id="5fbfc-291">...</span></span>|  
  
### <a name="select"></a><span data-ttu-id="5fbfc-292">VYBRAT</span><span class="sxs-lookup"><span data-stu-id="5fbfc-292">SELECT</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="5fbfc-293">také poskytuje konstruktor Row pro sestavování libovolných řádků.</span><span class="sxs-lookup"><span data-stu-id="5fbfc-293">also provides the row constructor to construct arbitrary rows.</span></span> <span data-ttu-id="5fbfc-294">Vyberte možnost přebírá jeden nebo více prvků v projekci a výsledkem je datový záznam s poli, například: `SELECT a, b, c`.</span><span class="sxs-lookup"><span data-stu-id="5fbfc-294">SELECT takes one or more elements in the projection and results in a data record with fields, for example: `SELECT a, b, c`.</span></span>  
  
 <span data-ttu-id="5fbfc-295">Příklad:</span><span class="sxs-lookup"><span data-stu-id="5fbfc-295">Example:</span></span>  
  
 <span data-ttu-id="5fbfc-296">Jako výstup p vyberte p.Name, p. ProductID z AdventureWorksEntities. Product:</span><span class="sxs-lookup"><span data-stu-id="5fbfc-296">SELECT p.Name, p.ProductID FROM AdventureWorksEntities.Product as p Output:</span></span>  
  
|<span data-ttu-id="5fbfc-297">Název</span><span class="sxs-lookup"><span data-stu-id="5fbfc-297">Name</span></span>|<span data-ttu-id="5fbfc-298">ProductID</span><span class="sxs-lookup"><span data-stu-id="5fbfc-298">ProductID</span></span>|  
|----------|---------------|  
|<span data-ttu-id="5fbfc-299">Přizpůsobitelná rasy</span><span class="sxs-lookup"><span data-stu-id="5fbfc-299">Adjustable Race</span></span>|<span data-ttu-id="5fbfc-300">1</span><span class="sxs-lookup"><span data-stu-id="5fbfc-300">1</span></span>|  
|<span data-ttu-id="5fbfc-301">Stojan kol pro všechny účely</span><span class="sxs-lookup"><span data-stu-id="5fbfc-301">All-Purpose Bike Stand</span></span>|<span data-ttu-id="5fbfc-302">879</span><span class="sxs-lookup"><span data-stu-id="5fbfc-302">879</span></span>|  
|<span data-ttu-id="5fbfc-303">AWC Logo Cap</span><span class="sxs-lookup"><span data-stu-id="5fbfc-303">AWC Logo Cap</span></span>|<span data-ttu-id="5fbfc-304">712</span><span class="sxs-lookup"><span data-stu-id="5fbfc-304">712</span></span>|  
|<span data-ttu-id="5fbfc-305">...</span><span class="sxs-lookup"><span data-stu-id="5fbfc-305">...</span></span>|<span data-ttu-id="5fbfc-306">...</span><span class="sxs-lookup"><span data-stu-id="5fbfc-306">...</span></span>|  
  
## <a name="case-expression"></a><span data-ttu-id="5fbfc-307">VÝRAZ CASE</span><span class="sxs-lookup"><span data-stu-id="5fbfc-307">CASE EXPRESSION</span></span>  
 <span data-ttu-id="5fbfc-308">[Výraz Case](case-entity-sql.md) vyhodnocuje sadu logických výrazů pro určení výsledku.</span><span class="sxs-lookup"><span data-stu-id="5fbfc-308">The [case expression](case-entity-sql.md) evaluates a set of Boolean expressions to determine the result.</span></span>  
  
 <span data-ttu-id="5fbfc-309">Příklad:</span><span class="sxs-lookup"><span data-stu-id="5fbfc-309">Example:</span></span>  
  
```sql  
CASE WHEN AVG({25,12,11}) < 100 THEN TRUE ELSE FALSE END  
```  
  
 <span data-ttu-id="5fbfc-310">Výstup:</span><span class="sxs-lookup"><span data-stu-id="5fbfc-310">Output:</span></span>  
  
|<span data-ttu-id="5fbfc-311">Hodnota</span><span class="sxs-lookup"><span data-stu-id="5fbfc-311">Value</span></span>|  
|-----------|  
|<span data-ttu-id="5fbfc-312">PRAVDA</span><span class="sxs-lookup"><span data-stu-id="5fbfc-312">TRUE</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5fbfc-313">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5fbfc-313">See also</span></span>

- [<span data-ttu-id="5fbfc-314">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="5fbfc-314">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="5fbfc-315">Přehled Entity SQL</span><span class="sxs-lookup"><span data-stu-id="5fbfc-315">Entity SQL Overview</span></span>](entity-sql-overview.md)
