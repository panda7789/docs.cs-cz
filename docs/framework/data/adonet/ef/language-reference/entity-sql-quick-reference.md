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
# <a name="entity-sql-quick-reference"></a><span data-ttu-id="b0a76-102">Stručné reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="b0a76-102">Entity SQL Quick Reference</span></span>
<span data-ttu-id="b0a76-103">V tomto tématu najdete stručný přehled dotazů [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b0a76-103">This topic provides a quick reference to [!INCLUDE[esql](../../../../../../includes/esql-md.md)] queries.</span></span> <span data-ttu-id="b0a76-104">Dotazy v tomto tématu jsou založené na modelu prodeje společnosti AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="b0a76-104">The queries in this topic are based on the AdventureWorks Sales model.</span></span>  
  
## <a name="literals"></a><span data-ttu-id="b0a76-105">Literály</span><span class="sxs-lookup"><span data-stu-id="b0a76-105">Literals</span></span>  
  
### <a name="string"></a><span data-ttu-id="b0a76-106">String</span><span class="sxs-lookup"><span data-stu-id="b0a76-106">String</span></span>  
 <span data-ttu-id="b0a76-107">Existují řetězcové literály znaků Unicode a non-Unicode.</span><span class="sxs-lookup"><span data-stu-id="b0a76-107">There are Unicode and non-Unicode character string literals.</span></span> <span data-ttu-id="b0a76-108">K řetězcům Unicode jsou předpony N. Například `N'hello'`.</span><span class="sxs-lookup"><span data-stu-id="b0a76-108">Unicode strings are prepended with N. For example, `N'hello'`.</span></span>  
  
 <span data-ttu-id="b0a76-109">Následuje příklad řetězcového literálu, který není Unicode:</span><span class="sxs-lookup"><span data-stu-id="b0a76-109">The following is an example of a Non-Unicode string literal:</span></span>  
  
```sql  
'hello'  
--same as  
"hello"  
```  
  
 <span data-ttu-id="b0a76-110">Výstup:</span><span class="sxs-lookup"><span data-stu-id="b0a76-110">Output:</span></span>  
  
|<span data-ttu-id="b0a76-111">Hodnota</span><span class="sxs-lookup"><span data-stu-id="b0a76-111">Value</span></span>|  
|-----------|  
|<span data-ttu-id="b0a76-112">Dobrý den</span><span class="sxs-lookup"><span data-stu-id="b0a76-112">hello</span></span>|  
  
### <a name="datetime"></a><span data-ttu-id="b0a76-113">DateTime</span><span class="sxs-lookup"><span data-stu-id="b0a76-113">DateTime</span></span>  
 <span data-ttu-id="b0a76-114">V literálech DateTime jsou části data a času povinné.</span><span class="sxs-lookup"><span data-stu-id="b0a76-114">In DateTime literals, both date and time parts are mandatory.</span></span> <span data-ttu-id="b0a76-115">Neexistují žádné výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="b0a76-115">There are no default values.</span></span>  
  
 <span data-ttu-id="b0a76-116">Příklad:</span><span class="sxs-lookup"><span data-stu-id="b0a76-116">Example:</span></span>  
  
```sql  
DATETIME '2006-12-25 01:01:00.000'   
--same as  
DATETIME '2006-12-25 01:01'  
```  
  
 <span data-ttu-id="b0a76-117">Výstup:</span><span class="sxs-lookup"><span data-stu-id="b0a76-117">Output:</span></span>  
  
|<span data-ttu-id="b0a76-118">Hodnota</span><span class="sxs-lookup"><span data-stu-id="b0a76-118">Value</span></span>|  
|-----------|  
|<span data-ttu-id="b0a76-119">12/25/2006 1:01:00 DOP.</span><span class="sxs-lookup"><span data-stu-id="b0a76-119">12/25/2006 1:01:00 AM</span></span>|  
  
### <a name="integer"></a><span data-ttu-id="b0a76-120">Integer</span><span class="sxs-lookup"><span data-stu-id="b0a76-120">Integer</span></span>  
 <span data-ttu-id="b0a76-121">Celočíselné literály můžou být typu Int32 (123), UInt32 (123U), Int64 (123L) a UInt64 (123UL).</span><span class="sxs-lookup"><span data-stu-id="b0a76-121">Integer literals can be of type Int32 (123), UInt32 (123U), Int64 (123L), and UInt64 (123UL).</span></span>  
  
 <span data-ttu-id="b0a76-122">Příklad:</span><span class="sxs-lookup"><span data-stu-id="b0a76-122">Example:</span></span>  
  
```sql  
--a collection of integers  
{1, 2, 3}  
```  
  
 <span data-ttu-id="b0a76-123">Výstup:</span><span class="sxs-lookup"><span data-stu-id="b0a76-123">Output:</span></span>  
  
|<span data-ttu-id="b0a76-124">Hodnota</span><span class="sxs-lookup"><span data-stu-id="b0a76-124">Value</span></span>|  
|-----------|  
|<span data-ttu-id="b0a76-125">první</span><span class="sxs-lookup"><span data-stu-id="b0a76-125">1</span></span>|  
|<span data-ttu-id="b0a76-126">odst</span><span class="sxs-lookup"><span data-stu-id="b0a76-126">2</span></span>|  
|<span data-ttu-id="b0a76-127">3</span><span class="sxs-lookup"><span data-stu-id="b0a76-127">3</span></span>|  
  
### <a name="other"></a><span data-ttu-id="b0a76-128">Ostatní</span><span class="sxs-lookup"><span data-stu-id="b0a76-128">Other</span></span>  
 <span data-ttu-id="b0a76-129">Jiné literály podporované [!INCLUDE[esql](../../../../../../includes/esql-md.md)] jsou GUID, binary, float, Double, Decimal a `null`.</span><span class="sxs-lookup"><span data-stu-id="b0a76-129">Other literals supported by [!INCLUDE[esql](../../../../../../includes/esql-md.md)] are Guid, Binary, Float/Double, Decimal, and `null`.</span></span> <span data-ttu-id="b0a76-130">Literály null v [!INCLUDE[esql](../../../../../../includes/esql-md.md)] jsou považovány za kompatibilní s každým jiným typem v koncepčním modelu.</span><span class="sxs-lookup"><span data-stu-id="b0a76-130">Null literals in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] are considered to be compatible with every other type in the conceptual model.</span></span>  
  
## <a name="type-constructors"></a><span data-ttu-id="b0a76-131">Konstruktory typů</span><span class="sxs-lookup"><span data-stu-id="b0a76-131">Type Constructors</span></span>  
  
### <a name="row"></a><span data-ttu-id="b0a76-132">ROW</span><span class="sxs-lookup"><span data-stu-id="b0a76-132">ROW</span></span>  
 <span data-ttu-id="b0a76-133">[Řádek](row-entity-sql.md) vytvoří anonymní, strukturálně napsané (záznam) hodnoty jako v: `ROW(1 AS myNumber, ‘Name’ AS myName).`</span><span class="sxs-lookup"><span data-stu-id="b0a76-133">[ROW](row-entity-sql.md) constructs an anonymous, structurally-typed (record) value as in: `ROW(1 AS myNumber, ‘Name’ AS myName).`</span></span>  
  
 <span data-ttu-id="b0a76-134">Příklad:</span><span class="sxs-lookup"><span data-stu-id="b0a76-134">Example:</span></span>  
  
```sql  
SELECT VALUE row (product.ProductID AS ProductID, product.Name
    AS ProductName) FROM AdventureWorksEntities.Product AS product
```  
  
 <span data-ttu-id="b0a76-135">Výstup:</span><span class="sxs-lookup"><span data-stu-id="b0a76-135">Output:</span></span>  
  
|<span data-ttu-id="b0a76-136">ProductID</span><span class="sxs-lookup"><span data-stu-id="b0a76-136">ProductID</span></span>|<span data-ttu-id="b0a76-137">Name</span><span class="sxs-lookup"><span data-stu-id="b0a76-137">Name</span></span>|  
|---------------|----------|  
|<span data-ttu-id="b0a76-138">první</span><span class="sxs-lookup"><span data-stu-id="b0a76-138">1</span></span>|<span data-ttu-id="b0a76-139">Přizpůsobitelná rasy</span><span class="sxs-lookup"><span data-stu-id="b0a76-139">Adjustable Race</span></span>|  
|<span data-ttu-id="b0a76-140">879</span><span class="sxs-lookup"><span data-stu-id="b0a76-140">879</span></span>|<span data-ttu-id="b0a76-141">Stojan kol pro všechny účely</span><span class="sxs-lookup"><span data-stu-id="b0a76-141">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="b0a76-142">712</span><span class="sxs-lookup"><span data-stu-id="b0a76-142">712</span></span>|<span data-ttu-id="b0a76-143">Zakončení loga AWC</span><span class="sxs-lookup"><span data-stu-id="b0a76-143">AWC Logo Cap</span></span>|  
|<span data-ttu-id="b0a76-144">...</span><span class="sxs-lookup"><span data-stu-id="b0a76-144">...</span></span>|<span data-ttu-id="b0a76-145">...</span><span class="sxs-lookup"><span data-stu-id="b0a76-145">...</span></span>|  
  
### <a name="multiset"></a><span data-ttu-id="b0a76-146">MULTISET</span><span class="sxs-lookup"><span data-stu-id="b0a76-146">MULTISET</span></span>  
 <span data-ttu-id="b0a76-147">[MULTISET](multiset-entity-sql.md) sestaví kolekce, například:</span><span class="sxs-lookup"><span data-stu-id="b0a76-147">[MULTISET](multiset-entity-sql.md) constructs collections, such as:</span></span>  
  
 <span data-ttu-id="b0a76-148">`MULTISET(1,2,2,3)` `--same as`-`{1,2,2,3}.`</span><span class="sxs-lookup"><span data-stu-id="b0a76-148">`MULTISET(1,2,2,3)` `--same as`-`{1,2,2,3}.`</span></span>  
  
 <span data-ttu-id="b0a76-149">Příklad:</span><span class="sxs-lookup"><span data-stu-id="b0a76-149">Example:</span></span>  
  
```sql  
SELECT VALUE product FROM AdventureWorksEntities.Product AS product WHERE product.ListPrice IN MultiSet (125, 300)  
```  
  
 <span data-ttu-id="b0a76-150">Výstup:</span><span class="sxs-lookup"><span data-stu-id="b0a76-150">Output:</span></span>  
  
|<span data-ttu-id="b0a76-151">ProductID</span><span class="sxs-lookup"><span data-stu-id="b0a76-151">ProductID</span></span>|<span data-ttu-id="b0a76-152">Name</span><span class="sxs-lookup"><span data-stu-id="b0a76-152">Name</span></span>|<span data-ttu-id="b0a76-153">ProductNumber</span><span class="sxs-lookup"><span data-stu-id="b0a76-153">ProductNumber</span></span>|<span data-ttu-id="b0a76-154">...</span><span class="sxs-lookup"><span data-stu-id="b0a76-154">…</span></span>|  
|---------------|----------|-------------------|-------|  
|<span data-ttu-id="b0a76-155">842</span><span class="sxs-lookup"><span data-stu-id="b0a76-155">842</span></span>|<span data-ttu-id="b0a76-156">Touring – Panniers, velký</span><span class="sxs-lookup"><span data-stu-id="b0a76-156">Touring-Panniers, Large</span></span>|<span data-ttu-id="b0a76-157">PA – T100</span><span class="sxs-lookup"><span data-stu-id="b0a76-157">PA-T100</span></span>|<span data-ttu-id="b0a76-158">...</span><span class="sxs-lookup"><span data-stu-id="b0a76-158">…</span></span>|  
  
### <a name="object"></a><span data-ttu-id="b0a76-159">Objekt</span><span class="sxs-lookup"><span data-stu-id="b0a76-159">Object</span></span>  
 <span data-ttu-id="b0a76-160">[Konstruktor pojmenovaného typu](named-type-constructor-entity-sql.md) konstrukce (pojmenované) uživatelsky definované objekty, například `person("abc", 12)`.</span><span class="sxs-lookup"><span data-stu-id="b0a76-160">[Named Type Constructor](named-type-constructor-entity-sql.md) constructs (named) user-defined objects, such as `person("abc", 12)`.</span></span>  
  
 <span data-ttu-id="b0a76-161">Příklad:</span><span class="sxs-lookup"><span data-stu-id="b0a76-161">Example:</span></span>  
  
```sql  
SELECT VALUE AdventureWorksModel.SalesOrderDetail (o.SalesOrderDetailID, o.CarrierTrackingNumber, o.OrderQty,   
o.ProductID, o.SpecialOfferID, o.UnitPrice, o.UnitPriceDiscount,   
o.rowguid, o.ModifiedDate) FROM AdventureWorksEntities.SalesOrderDetail   
AS o  
```  
  
 <span data-ttu-id="b0a76-162">Výstup:</span><span class="sxs-lookup"><span data-stu-id="b0a76-162">Output:</span></span>  
  
|<span data-ttu-id="b0a76-163">SalesOrderDetailID</span><span class="sxs-lookup"><span data-stu-id="b0a76-163">SalesOrderDetailID</span></span>|<span data-ttu-id="b0a76-164">CarrierTrackingNumber</span><span class="sxs-lookup"><span data-stu-id="b0a76-164">CarrierTrackingNumber</span></span>|<span data-ttu-id="b0a76-165">OrderQty</span><span class="sxs-lookup"><span data-stu-id="b0a76-165">OrderQty</span></span>|<span data-ttu-id="b0a76-166">ProductID</span><span class="sxs-lookup"><span data-stu-id="b0a76-166">ProductID</span></span>|<span data-ttu-id="b0a76-167">...</span><span class="sxs-lookup"><span data-stu-id="b0a76-167">...</span></span>|  
|------------------------|---------------------------|--------------|---------------|---------|  
|<span data-ttu-id="b0a76-168">první</span><span class="sxs-lookup"><span data-stu-id="b0a76-168">1</span></span>|<span data-ttu-id="b0a76-169">4911-403C-98</span><span class="sxs-lookup"><span data-stu-id="b0a76-169">4911-403C-98</span></span>|<span data-ttu-id="b0a76-170">první</span><span class="sxs-lookup"><span data-stu-id="b0a76-170">1</span></span>|<span data-ttu-id="b0a76-171">776</span><span class="sxs-lookup"><span data-stu-id="b0a76-171">776</span></span>|<span data-ttu-id="b0a76-172">...</span><span class="sxs-lookup"><span data-stu-id="b0a76-172">...</span></span>|  
|<span data-ttu-id="b0a76-173">odst</span><span class="sxs-lookup"><span data-stu-id="b0a76-173">2</span></span>|<span data-ttu-id="b0a76-174">4911-403C-98</span><span class="sxs-lookup"><span data-stu-id="b0a76-174">4911-403C-98</span></span>|<span data-ttu-id="b0a76-175">3</span><span class="sxs-lookup"><span data-stu-id="b0a76-175">3</span></span>|<span data-ttu-id="b0a76-176">777</span><span class="sxs-lookup"><span data-stu-id="b0a76-176">777</span></span>|<span data-ttu-id="b0a76-177">...</span><span class="sxs-lookup"><span data-stu-id="b0a76-177">...</span></span>|  
|<span data-ttu-id="b0a76-178">...</span><span class="sxs-lookup"><span data-stu-id="b0a76-178">...</span></span>|<span data-ttu-id="b0a76-179">...</span><span class="sxs-lookup"><span data-stu-id="b0a76-179">...</span></span>|<span data-ttu-id="b0a76-180">...</span><span class="sxs-lookup"><span data-stu-id="b0a76-180">...</span></span>|<span data-ttu-id="b0a76-181">...</span><span class="sxs-lookup"><span data-stu-id="b0a76-181">...</span></span>|<span data-ttu-id="b0a76-182">...</span><span class="sxs-lookup"><span data-stu-id="b0a76-182">...</span></span>|  
  
## <a name="references"></a><span data-ttu-id="b0a76-183">Odkazy</span><span class="sxs-lookup"><span data-stu-id="b0a76-183">References</span></span>  
  
### <a name="ref"></a><span data-ttu-id="b0a76-184">REF</span><span class="sxs-lookup"><span data-stu-id="b0a76-184">REF</span></span>  
 <span data-ttu-id="b0a76-185">[Odkaz vytvoří odkaz](ref-entity-sql.md) na instanci typu entity.</span><span class="sxs-lookup"><span data-stu-id="b0a76-185">[REF](ref-entity-sql.md) creates a reference to an entity type instance.</span></span> <span data-ttu-id="b0a76-186">Následující dotaz například vrátí odkazy na každou entitu objednávky v sadě entit Orders:</span><span class="sxs-lookup"><span data-stu-id="b0a76-186">For example, the following query returns references to each Order entity in the Orders entity set:</span></span>  
  
```sql  
SELECT REF(o) AS OrderID FROM Orders AS o  
```  
  
 <span data-ttu-id="b0a76-187">Výstup:</span><span class="sxs-lookup"><span data-stu-id="b0a76-187">Output:</span></span>  
  
|<span data-ttu-id="b0a76-188">Hodnota</span><span class="sxs-lookup"><span data-stu-id="b0a76-188">Value</span></span>|  
|-----------|  
|<span data-ttu-id="b0a76-189">první</span><span class="sxs-lookup"><span data-stu-id="b0a76-189">1</span></span>|  
|<span data-ttu-id="b0a76-190">odst</span><span class="sxs-lookup"><span data-stu-id="b0a76-190">2</span></span>|  
|<span data-ttu-id="b0a76-191">3</span><span class="sxs-lookup"><span data-stu-id="b0a76-191">3</span></span>|  
|<span data-ttu-id="b0a76-192">...</span><span class="sxs-lookup"><span data-stu-id="b0a76-192">...</span></span>|  
  
 <span data-ttu-id="b0a76-193">Následující příklad používá operátor extrakce vlastností (.) pro přístup k vlastnosti entity.</span><span class="sxs-lookup"><span data-stu-id="b0a76-193">The following example uses the property extraction operator (.) to access a property of an entity.</span></span> <span data-ttu-id="b0a76-194">Při použití operátoru extrakce vlastností je odkaz automaticky odkázat.</span><span class="sxs-lookup"><span data-stu-id="b0a76-194">When the property extraction operator is used, the reference is automatically dereferenced.</span></span>  
  
 <span data-ttu-id="b0a76-195">Příklad:</span><span class="sxs-lookup"><span data-stu-id="b0a76-195">Example:</span></span>  
  
```sql  
SELECT VALUE REF(p).Name FROM   
    AdventureWorksEntities.Product AS p
```  
  
 <span data-ttu-id="b0a76-196">Výstup:</span><span class="sxs-lookup"><span data-stu-id="b0a76-196">Output:</span></span>  
  
|<span data-ttu-id="b0a76-197">Hodnota</span><span class="sxs-lookup"><span data-stu-id="b0a76-197">Value</span></span>|  
|-----------|  
|<span data-ttu-id="b0a76-198">Přizpůsobitelná rasy</span><span class="sxs-lookup"><span data-stu-id="b0a76-198">Adjustable Race</span></span>|  
|<span data-ttu-id="b0a76-199">Stojan kol pro všechny účely</span><span class="sxs-lookup"><span data-stu-id="b0a76-199">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="b0a76-200">Zakončení loga AWC</span><span class="sxs-lookup"><span data-stu-id="b0a76-200">AWC Logo Cap</span></span>|  
|<span data-ttu-id="b0a76-201">...</span><span class="sxs-lookup"><span data-stu-id="b0a76-201">...</span></span>|  
  
### <a name="deref"></a><span data-ttu-id="b0a76-202">DEREF</span><span class="sxs-lookup"><span data-stu-id="b0a76-202">DEREF</span></span>  
 <span data-ttu-id="b0a76-203">[DEREF](deref-entity-sql.md) odkazuje na referenční hodnotu a vytváří výsledek tohoto odkázání.</span><span class="sxs-lookup"><span data-stu-id="b0a76-203">[DEREF](deref-entity-sql.md) dereferences a reference value and produces the result of that dereference.</span></span> <span data-ttu-id="b0a76-204">Následující dotaz například generuje entity Order pro jednotlivé objednávky v sadě entit Orders: `SELECT DEREF(o2.r) FROM (SELECT REF(o) AS r FROM LOB.Orders AS o) AS o2`..</span><span class="sxs-lookup"><span data-stu-id="b0a76-204">For example, the following query produces the Order entities for each Order in the Orders entity set: `SELECT DEREF(o2.r) FROM (SELECT REF(o) AS r FROM LOB.Orders AS o) AS o2`..</span></span>  
  
 <span data-ttu-id="b0a76-205">Příklad:</span><span class="sxs-lookup"><span data-stu-id="b0a76-205">Example:</span></span>  
  
```sql  
SELECT VALUE DEREF(REF(p)).Name FROM   
    AdventureWorksEntities.Product AS p
```  
  
 <span data-ttu-id="b0a76-206">Výstup:</span><span class="sxs-lookup"><span data-stu-id="b0a76-206">Output:</span></span>  
  
|<span data-ttu-id="b0a76-207">Hodnota</span><span class="sxs-lookup"><span data-stu-id="b0a76-207">Value</span></span>|  
|-----------|  
|<span data-ttu-id="b0a76-208">Přizpůsobitelná rasy</span><span class="sxs-lookup"><span data-stu-id="b0a76-208">Adjustable Race</span></span>|  
|<span data-ttu-id="b0a76-209">Stojan kol pro všechny účely</span><span class="sxs-lookup"><span data-stu-id="b0a76-209">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="b0a76-210">Zakončení loga AWC</span><span class="sxs-lookup"><span data-stu-id="b0a76-210">AWC Logo Cap</span></span>|  
|<span data-ttu-id="b0a76-211">...</span><span class="sxs-lookup"><span data-stu-id="b0a76-211">...</span></span>|  
  
### <a name="createref-and-key"></a><span data-ttu-id="b0a76-212">CREATEREF A KLÍČ</span><span class="sxs-lookup"><span data-stu-id="b0a76-212">CREATEREF AND KEY</span></span>  
 <span data-ttu-id="b0a76-213">[CREATEREF](createref-entity-sql.md) vytvoří odkaz, který projde klíč.</span><span class="sxs-lookup"><span data-stu-id="b0a76-213">[CREATEREF](createref-entity-sql.md) creates a reference passing a key.</span></span> <span data-ttu-id="b0a76-214">[Klíč](key-entity-sql.md) extrahuje klíčovou část výrazu s odkazem na typ.</span><span class="sxs-lookup"><span data-stu-id="b0a76-214">[KEY](key-entity-sql.md) extracts the key portion of an expression with type reference.</span></span>  
  
 <span data-ttu-id="b0a76-215">Příklad:</span><span class="sxs-lookup"><span data-stu-id="b0a76-215">Example:</span></span>  
  
```sql  
SELECT VALUE Key(CreateRef(AdventureWorksEntities.Product, row(p.ProductID)))   
    FROM AdventureWorksEntities.Product AS p
```  
  
 <span data-ttu-id="b0a76-216">Výstup:</span><span class="sxs-lookup"><span data-stu-id="b0a76-216">Output:</span></span>  
  
|<span data-ttu-id="b0a76-217">ProductID</span><span class="sxs-lookup"><span data-stu-id="b0a76-217">ProductID</span></span>|  
|---------------|  
|<span data-ttu-id="b0a76-218">980</span><span class="sxs-lookup"><span data-stu-id="b0a76-218">980</span></span>|  
|<span data-ttu-id="b0a76-219">365</span><span class="sxs-lookup"><span data-stu-id="b0a76-219">365</span></span>|  
|<span data-ttu-id="b0a76-220">771</span><span class="sxs-lookup"><span data-stu-id="b0a76-220">771</span></span>|  
|<span data-ttu-id="b0a76-221">...</span><span class="sxs-lookup"><span data-stu-id="b0a76-221">...</span></span>|  
  
## <a name="functions"></a><span data-ttu-id="b0a76-222">Funkce</span><span class="sxs-lookup"><span data-stu-id="b0a76-222">Functions</span></span>  
  
### <a name="canonical"></a><span data-ttu-id="b0a76-223">Interpret</span><span class="sxs-lookup"><span data-stu-id="b0a76-223">Canonical</span></span>  
 <span data-ttu-id="b0a76-224">Obor názvů pro [kanonické funkce](canonical-functions.md) je EDM, jako v `Edm.Length("string")`.</span><span class="sxs-lookup"><span data-stu-id="b0a76-224">The namespace for [canonical functions](canonical-functions.md) is Edm, as in `Edm.Length("string")`.</span></span> <span data-ttu-id="b0a76-225">Není nutné zadávat obor názvů, pokud není importován jiný obor názvů, který obsahuje funkci se stejným názvem jako kanonická funkce.</span><span class="sxs-lookup"><span data-stu-id="b0a76-225">You do not have to specify the namespace unless another namespace is imported that contains a function with the same name as a canonical function.</span></span> <span data-ttu-id="b0a76-226">Pokud mají dva obory názvů stejnou funkci, měl by uživatel určit celé jméno.</span><span class="sxs-lookup"><span data-stu-id="b0a76-226">If two namespaces have the same function, the user should specific the full name.</span></span>  
  
 <span data-ttu-id="b0a76-227">Příklad:</span><span class="sxs-lookup"><span data-stu-id="b0a76-227">Example:</span></span>  
  
```sql  
SELECT Length(c. FirstName) AS NameLen FROM
    AdventureWorksEntities.Contact AS c   
    WHERE c.ContactID BETWEEN 10 AND 12  
```  
  
 <span data-ttu-id="b0a76-228">Výstup:</span><span class="sxs-lookup"><span data-stu-id="b0a76-228">Output:</span></span>  
  
|<span data-ttu-id="b0a76-229">NameLen</span><span class="sxs-lookup"><span data-stu-id="b0a76-229">NameLen</span></span>|  
|-------------|  
|<span data-ttu-id="b0a76-230">6</span><span class="sxs-lookup"><span data-stu-id="b0a76-230">6</span></span>|  
|<span data-ttu-id="b0a76-231">6</span><span class="sxs-lookup"><span data-stu-id="b0a76-231">6</span></span>|  
|<span data-ttu-id="b0a76-232">5</span><span class="sxs-lookup"><span data-stu-id="b0a76-232">5</span></span>|  
  
### <a name="microsoft-provider-specific"></a><span data-ttu-id="b0a76-233">Specifické pro poskytovatele Microsoftu</span><span class="sxs-lookup"><span data-stu-id="b0a76-233">Microsoft Provider-Specific</span></span>  
 <span data-ttu-id="b0a76-234">[Funkce specifické pro poskytovatele společnosti Microsoft](../sqlclient-for-ef-functions.md) jsou v oboru názvů `SqlServer`.</span><span class="sxs-lookup"><span data-stu-id="b0a76-234">[Microsoft provider-specific functions](../sqlclient-for-ef-functions.md) are in the `SqlServer` namespace.</span></span>  
  
 <span data-ttu-id="b0a76-235">Příklad:</span><span class="sxs-lookup"><span data-stu-id="b0a76-235">Example:</span></span>  
  
```sql  
SELECT SqlServer.LEN(c.EmailAddress) AS EmailLen FROM
    AdventureWorksEntities.Contact AS c WHERE   
    c.ContactID BETWEEN 10 AND 12  
```  
  
 <span data-ttu-id="b0a76-236">Výstup:</span><span class="sxs-lookup"><span data-stu-id="b0a76-236">Output:</span></span>  
  
|<span data-ttu-id="b0a76-237">EmailLen</span><span class="sxs-lookup"><span data-stu-id="b0a76-237">EmailLen</span></span>|  
|--------------|  
|<span data-ttu-id="b0a76-238">dlouhý</span><span class="sxs-lookup"><span data-stu-id="b0a76-238">27</span></span>|  
|<span data-ttu-id="b0a76-239">dlouhý</span><span class="sxs-lookup"><span data-stu-id="b0a76-239">27</span></span>|  
|<span data-ttu-id="b0a76-240">26</span><span class="sxs-lookup"><span data-stu-id="b0a76-240">26</span></span>|  
  
## <a name="namespaces"></a><span data-ttu-id="b0a76-241">Jmenné prostory</span><span class="sxs-lookup"><span data-stu-id="b0a76-241">Namespaces</span></span>  
 <span data-ttu-id="b0a76-242">[Použití](using-entity-sql.md) určuje obory názvů použité ve výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="b0a76-242">[USING](using-entity-sql.md) specifies namespaces used in a query expression.</span></span>  
  
 <span data-ttu-id="b0a76-243">Příklad:</span><span class="sxs-lookup"><span data-stu-id="b0a76-243">Example:</span></span>  
  
```sql  
using SqlServer; LOWER('AA');  
```  
  
 <span data-ttu-id="b0a76-244">Výstup:</span><span class="sxs-lookup"><span data-stu-id="b0a76-244">Output:</span></span>  
  
|<span data-ttu-id="b0a76-245">Hodnota</span><span class="sxs-lookup"><span data-stu-id="b0a76-245">Value</span></span>|  
|-----------|  
|<span data-ttu-id="b0a76-246">aa</span><span class="sxs-lookup"><span data-stu-id="b0a76-246">aa</span></span>|  
  
## <a name="paging"></a><span data-ttu-id="b0a76-247">Stránkování</span><span class="sxs-lookup"><span data-stu-id="b0a76-247">Paging</span></span>  
 <span data-ttu-id="b0a76-248">Stránkování lze vyjádřit deklarováním dílčích klauzulí [Skip](skip-entity-sql.md) a [limit](limit-entity-sql.md) na klauzuli [ORDER by](order-by-entity-sql.md) .</span><span class="sxs-lookup"><span data-stu-id="b0a76-248">Paging can be expressed by declaring a [SKIP](skip-entity-sql.md) and [LIMIT](limit-entity-sql.md) sub-clauses to the [ORDER BY](order-by-entity-sql.md) clause.</span></span>  
  
 <span data-ttu-id="b0a76-249">Příklad:</span><span class="sxs-lookup"><span data-stu-id="b0a76-249">Example:</span></span>  
  
```sql  
SELECT c.ContactID as ID, c.LastName AS Name FROM
    AdventureWorks.Contact AS c ORDER BY c.ContactID SKIP 9 LIMIT 3;  
```  
  
 <span data-ttu-id="b0a76-250">Výstup:</span><span class="sxs-lookup"><span data-stu-id="b0a76-250">Output:</span></span>  
  
|<span data-ttu-id="b0a76-251">ID</span><span class="sxs-lookup"><span data-stu-id="b0a76-251">ID</span></span>|<span data-ttu-id="b0a76-252">Name</span><span class="sxs-lookup"><span data-stu-id="b0a76-252">Name</span></span>|  
|--------|----------|  
|<span data-ttu-id="b0a76-253">10pruhový</span><span class="sxs-lookup"><span data-stu-id="b0a76-253">10</span></span>|<span data-ttu-id="b0a76-254">Adina</span><span class="sxs-lookup"><span data-stu-id="b0a76-254">Adina</span></span>|  
|<span data-ttu-id="b0a76-255">odst</span><span class="sxs-lookup"><span data-stu-id="b0a76-255">11</span></span>|<span data-ttu-id="b0a76-256">Agcaoili</span><span class="sxs-lookup"><span data-stu-id="b0a76-256">Agcaoili</span></span>|  
|<span data-ttu-id="b0a76-257">12,5</span><span class="sxs-lookup"><span data-stu-id="b0a76-257">12</span></span>|<span data-ttu-id="b0a76-258">Aguilar</span><span class="sxs-lookup"><span data-stu-id="b0a76-258">Aguilar</span></span>|  
  
## <a name="grouping"></a><span data-ttu-id="b0a76-259">Seskupování</span><span class="sxs-lookup"><span data-stu-id="b0a76-259">Grouping</span></span>  
 <span data-ttu-id="b0a76-260">[Seskupení podle](group-by-entity-sql.md) určuje skupiny, do kterých se mají umístit objekty vrácené výrazem dotazu ([Select](select-entity-sql.md)).</span><span class="sxs-lookup"><span data-stu-id="b0a76-260">[GROUPING BY](group-by-entity-sql.md) specifies groups into which objects returned by a query ([SELECT](select-entity-sql.md)) expression are to be placed.</span></span>  
  
 <span data-ttu-id="b0a76-261">Příklad:</span><span class="sxs-lookup"><span data-stu-id="b0a76-261">Example:</span></span>  
  
```sql  
SELECT VALUE name FROM AdventureWorksEntities.Product AS P
    GROUP BY P.Name HAVING MAX(P.ListPrice) > 5  
```  
  
 <span data-ttu-id="b0a76-262">Výstup:</span><span class="sxs-lookup"><span data-stu-id="b0a76-262">Output:</span></span>  
  
|<span data-ttu-id="b0a76-263">name</span><span class="sxs-lookup"><span data-stu-id="b0a76-263">name</span></span>|  
|----------|  
|<span data-ttu-id="b0a76-264">Sestavení pro horská místa</span><span class="sxs-lookup"><span data-stu-id="b0a76-264">LL Mountain Seat Assembly</span></span>|  
|<span data-ttu-id="b0a76-265">Sestavení ML horských sedadel</span><span class="sxs-lookup"><span data-stu-id="b0a76-265">ML Mountain Seat Assembly</span></span>|  
|<span data-ttu-id="b0a76-266">HL – sestavení pracovních stanic</span><span class="sxs-lookup"><span data-stu-id="b0a76-266">HL Mountain Seat Assembly</span></span>|  
|<span data-ttu-id="b0a76-267">...</span><span class="sxs-lookup"><span data-stu-id="b0a76-267">...</span></span>|  
  
## <a name="navigation"></a><span data-ttu-id="b0a76-268">Navigace</span><span class="sxs-lookup"><span data-stu-id="b0a76-268">Navigation</span></span>  
 <span data-ttu-id="b0a76-269">Operátor navigace mezi relacemi umožňuje procházet relaci z jedné entity (od konce) do jiné (do konce).</span><span class="sxs-lookup"><span data-stu-id="b0a76-269">The relationship navigation operator allows you to navigate over the relationship from one entity (from end) to another (to end).</span></span> <span data-ttu-id="b0a76-270">[Navigace](navigate-entity-sql.md) přebírá typ vztahu kvalifikovaný jako \<namespace >. název typu \<relationship >.</span><span class="sxs-lookup"><span data-stu-id="b0a76-270">[NAVIGATE](navigate-entity-sql.md) takes the relationship type qualified as \<namespace>.\<relationship type name>.</span></span> <span data-ttu-id="b0a76-271">Funkce Navigate vrátí ref @ no__t-0T >, pokud mohutnost pro končí 1.</span><span class="sxs-lookup"><span data-stu-id="b0a76-271">Navigate returns Ref\<T> if the cardinality of the to end is 1.</span></span> <span data-ttu-id="b0a76-272">Pokud mohutnost do konce má hodnotu n, vrátí se < kolekce ref @ no__t-0T > >.</span><span class="sxs-lookup"><span data-stu-id="b0a76-272">If the cardinality of the to end is n, the Collection<Ref\<T>> will be returned.</span></span>  
  
 <span data-ttu-id="b0a76-273">Příklad:</span><span class="sxs-lookup"><span data-stu-id="b0a76-273">Example:</span></span>  
  
```sql  
SELECT a.AddressID, (SELECT VALUE DEREF(v) FROM   
    NAVIGATE(a, AdventureWorksModel.FK_SalesOrderHeader_Address_BillToAddressID) AS v)   
    FROM AdventureWorksEntities.Address AS a  
```  
  
 <span data-ttu-id="b0a76-274">Výstup:</span><span class="sxs-lookup"><span data-stu-id="b0a76-274">Output:</span></span>  
  
|<span data-ttu-id="b0a76-275">AddressID</span><span class="sxs-lookup"><span data-stu-id="b0a76-275">AddressID</span></span>|  
|---------------|  
|<span data-ttu-id="b0a76-276">první</span><span class="sxs-lookup"><span data-stu-id="b0a76-276">1</span></span>|  
|<span data-ttu-id="b0a76-277">odst</span><span class="sxs-lookup"><span data-stu-id="b0a76-277">2</span></span>|  
|<span data-ttu-id="b0a76-278">3</span><span class="sxs-lookup"><span data-stu-id="b0a76-278">3</span></span>|  
|<span data-ttu-id="b0a76-279">...</span><span class="sxs-lookup"><span data-stu-id="b0a76-279">...</span></span>|  
  
## <a name="select-value-and-select"></a><span data-ttu-id="b0a76-280">VYBERTE HODNOTU A VYBERTE</span><span class="sxs-lookup"><span data-stu-id="b0a76-280">SELECT VALUE AND SELECT</span></span>  
  
### <a name="select-value"></a><span data-ttu-id="b0a76-281">VYBRAT HODNOTU</span><span class="sxs-lookup"><span data-stu-id="b0a76-281">SELECT VALUE</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="b0a76-282">poskytuje klauzuli SELECT VALUE pro přeskočení vytváření implicitních řádků.</span><span class="sxs-lookup"><span data-stu-id="b0a76-282">provides the SELECT VALUE clause to skip the implicit row construction.</span></span> <span data-ttu-id="b0a76-283">V klauzuli SELECT VALUE lze zadat pouze jednu položku.</span><span class="sxs-lookup"><span data-stu-id="b0a76-283">Only one item can be specified in a SELECT VALUE clause.</span></span> <span data-ttu-id="b0a76-284">Je-li použita taková klauzule, není kolem položek v klauzuli SELECT vytvořena obálka řádku a může být vytvořena kolekce požadovaného tvaru, například: `SELECT VALUE a`.</span><span class="sxs-lookup"><span data-stu-id="b0a76-284">When such a clause is used, no row wrapper is constructed around the items in the SELECT clause, and a collection of the desired shape can be produced, for example: `SELECT VALUE a`.</span></span>  
  
 <span data-ttu-id="b0a76-285">Příklad:</span><span class="sxs-lookup"><span data-stu-id="b0a76-285">Example:</span></span>  
  
```sql  
SELECT VALUE p.Name FROM AdventureWorksEntities.Product AS p
```  
  
 <span data-ttu-id="b0a76-286">Výstup:</span><span class="sxs-lookup"><span data-stu-id="b0a76-286">Output:</span></span>  
  
|<span data-ttu-id="b0a76-287">Name</span><span class="sxs-lookup"><span data-stu-id="b0a76-287">Name</span></span>|  
|----------|  
|<span data-ttu-id="b0a76-288">Přizpůsobitelná rasy</span><span class="sxs-lookup"><span data-stu-id="b0a76-288">Adjustable Race</span></span>|  
|<span data-ttu-id="b0a76-289">Stojan kol pro všechny účely</span><span class="sxs-lookup"><span data-stu-id="b0a76-289">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="b0a76-290">Zakončení loga AWC</span><span class="sxs-lookup"><span data-stu-id="b0a76-290">AWC Logo Cap</span></span>|  
|<span data-ttu-id="b0a76-291">...</span><span class="sxs-lookup"><span data-stu-id="b0a76-291">...</span></span>|  
  
### <a name="select"></a><span data-ttu-id="b0a76-292">SELECT</span><span class="sxs-lookup"><span data-stu-id="b0a76-292">SELECT</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="b0a76-293">poskytuje také konstruktor Row pro vytvoření libovolných řádků.</span><span class="sxs-lookup"><span data-stu-id="b0a76-293">also provides the row constructor to construct arbitrary rows.</span></span> <span data-ttu-id="b0a76-294">Vyberte možnost přebírá jeden nebo více prvků v projekci a výsledkem je datový záznam s poli, například: `SELECT a, b, c`.</span><span class="sxs-lookup"><span data-stu-id="b0a76-294">SELECT takes one or more elements in the projection and results in a data record with fields, for example: `SELECT a, b, c`.</span></span>  
  
 <span data-ttu-id="b0a76-295">Příklad:</span><span class="sxs-lookup"><span data-stu-id="b0a76-295">Example:</span></span>  
  
 <span data-ttu-id="b0a76-296">Jako výstup p vyberte p.Name, p. ProductID z AdventureWorksEntities. Product:</span><span class="sxs-lookup"><span data-stu-id="b0a76-296">SELECT p.Name, p.ProductID FROM AdventureWorksEntities.Product as p Output:</span></span>  
  
|<span data-ttu-id="b0a76-297">Name</span><span class="sxs-lookup"><span data-stu-id="b0a76-297">Name</span></span>|<span data-ttu-id="b0a76-298">ProductID</span><span class="sxs-lookup"><span data-stu-id="b0a76-298">ProductID</span></span>|  
|----------|---------------|  
|<span data-ttu-id="b0a76-299">Přizpůsobitelná rasy</span><span class="sxs-lookup"><span data-stu-id="b0a76-299">Adjustable Race</span></span>|<span data-ttu-id="b0a76-300">první</span><span class="sxs-lookup"><span data-stu-id="b0a76-300">1</span></span>|  
|<span data-ttu-id="b0a76-301">Stojan kol pro všechny účely</span><span class="sxs-lookup"><span data-stu-id="b0a76-301">All-Purpose Bike Stand</span></span>|<span data-ttu-id="b0a76-302">879</span><span class="sxs-lookup"><span data-stu-id="b0a76-302">879</span></span>|  
|<span data-ttu-id="b0a76-303">Zakončení loga AWC</span><span class="sxs-lookup"><span data-stu-id="b0a76-303">AWC Logo Cap</span></span>|<span data-ttu-id="b0a76-304">712</span><span class="sxs-lookup"><span data-stu-id="b0a76-304">712</span></span>|  
|<span data-ttu-id="b0a76-305">...</span><span class="sxs-lookup"><span data-stu-id="b0a76-305">...</span></span>|<span data-ttu-id="b0a76-306">...</span><span class="sxs-lookup"><span data-stu-id="b0a76-306">...</span></span>|  
  
## <a name="case-expression"></a><span data-ttu-id="b0a76-307">VÝRAZ CASE</span><span class="sxs-lookup"><span data-stu-id="b0a76-307">CASE EXPRESSION</span></span>  
 <span data-ttu-id="b0a76-308">[Výraz Case](case-entity-sql.md) vyhodnocuje sadu logických výrazů pro určení výsledku.</span><span class="sxs-lookup"><span data-stu-id="b0a76-308">The [case expression](case-entity-sql.md) evaluates a set of Boolean expressions to determine the result.</span></span>  
  
 <span data-ttu-id="b0a76-309">Příklad:</span><span class="sxs-lookup"><span data-stu-id="b0a76-309">Example:</span></span>  
  
```sql  
CASE WHEN AVG({25,12,11}) < 100 THEN TRUE ELSE FALSE END  
```  
  
 <span data-ttu-id="b0a76-310">Výstup:</span><span class="sxs-lookup"><span data-stu-id="b0a76-310">Output:</span></span>  
  
|<span data-ttu-id="b0a76-311">Hodnota</span><span class="sxs-lookup"><span data-stu-id="b0a76-311">Value</span></span>|  
|-----------|  
|<span data-ttu-id="b0a76-312">PODMÍNKA</span><span class="sxs-lookup"><span data-stu-id="b0a76-312">TRUE</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b0a76-313">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b0a76-313">See also</span></span>

- [<span data-ttu-id="b0a76-314">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="b0a76-314">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="b0a76-315">Přehled Entity SQL</span><span class="sxs-lookup"><span data-stu-id="b0a76-315">Entity SQL Overview</span></span>](entity-sql-overview.md)
