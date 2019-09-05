---
title: Stručné reference k Entity SQL
ms.date: 03/30/2017
ms.assetid: e53dad9e-5e83-426e-abb4-be3e78e3d6dc
ms.openlocfilehash: 7780359d981b130118cb73d4892f3dcb4b6e2e7d
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251031"
---
# <a name="entity-sql-quick-reference"></a>Stručné reference k Entity SQL
V tomto tématu najdete stručný přehled [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dotazů. Dotazy v tomto tématu jsou založené na modelu prodeje společnosti AdventureWorks.  
  
## <a name="literals"></a>Literály  
  
### <a name="string"></a>String  
 Existují řetězcové literály znaků Unicode a non-Unicode. K řetězcům Unicode jsou předpony N. Například `N'hello'`.  
  
 Následuje příklad řetězcového literálu, který není Unicode:  
  
```  
'hello'  
--same as  
"hello"  
```  
  
 Výstup:  
  
|Value|  
|-----------|  
|Dobrý den|  
  
### <a name="datetime"></a>DateTime  
 V literálech DateTime jsou části data a času povinné. Neexistují žádné výchozí hodnoty.  
  
 Příklad:  
  
```  
DATETIME '2006-12-25 01:01:00.000'   
--same as  
DATETIME '2006-12-25 01:01'  
```  
  
 Výstup:  
  
|Value|  
|-----------|  
|12/25/2006 1:01:00 DOP.|  
  
### <a name="integer"></a>Integer  
 Celočíselné literály můžou být typu Int32 (123), UInt32 (123U), Int64 (123L) a UInt64 (123UL).  
  
 Příklad:  
  
```  
--a collection of integers  
{1, 2, 3}  
```  
  
 Výstup:  
  
|Value|  
|-----------|  
|1|  
|2|  
|3|  
  
### <a name="other"></a>Ostatní  
 Jiné literály podporované nástrojem [!INCLUDE[esql](../../../../../../includes/esql-md.md)] jsou GUID, binary, float/Double, Decimal a. `null` Literály null v [!INCLUDE[esql](../../../../../../includes/esql-md.md)] jsou považovány za kompatibilní s každým jiným typem v koncepčním modelu.  
  
## <a name="type-constructors"></a>Konstruktory typů  
  
### <a name="row"></a>ROW  
 [Řádek](row-entity-sql.md) vytvoří anonymní, strukturálně napsané (záznam) hodnoty jako v:`ROW(1 AS myNumber, ‘Name’ AS myName).`  
  
 Příklad:  
  
```  
SELECT VALUE row (product.ProductID as ProductID, product.Name   
    as ProductName) FROM AdventureWorksEntities.Product AS product  
```  
  
 Výstup:  
  
|ProductID|Name|  
|---------------|----------|  
|1|Přizpůsobitelná rasy|  
|879|Stojan kol pro všechny účely|  
|712|Zakončení loga AWC|  
|...|...|  
  
### <a name="multiset"></a>MULTISET  
 [MULTISET](multiset-entity-sql.md) sestaví kolekce, například:  
  
 `MULTISET(1,2,2,3)` `--same as`-`{1,2,2,3}.`  
  
 Příklad:  
  
```  
SELECT VALUE product FROM AdventureWorksEntities.Product AS product WHERE product.ListPrice IN MultiSet (125, 300)  
```  
  
 Výstup:  
  
|ProductID|Název|ProductNumber|…|  
|---------------|----------|-------------------|-------|  
|842|Touring – Panniers, velký|PA-T100|…|  
  
### <a name="object"></a>Objekt  
 [Konstruktor pojmenovaného typu](named-type-constructor-entity-sql.md) konstrukce (pojmenované) uživatelsky definované objekty, například `person("abc", 12)`.  
  
 Příklad:  
  
```  
SELECT VALUE AdventureWorksModel.SalesOrderDetail (o.SalesOrderDetailID, o.CarrierTrackingNumber, o.OrderQty,   
o.ProductID, o.SpecialOfferID, o.UnitPrice, o.UnitPriceDiscount,   
o.rowguid, o.ModifiedDate) FROM AdventureWorksEntities.SalesOrderDetail   
AS o  
```  
  
 Výstup:  
  
|SalesOrderDetailID|CarrierTrackingNumber|OrderQty|ProductID|...|  
|------------------------|---------------------------|--------------|---------------|---------|  
|1|4911-403C-98|1|776|...|  
|2|4911-403C-98|3|777|...|  
|...|...|...|...|...|  
  
## <a name="references"></a>Odkazy  
  
### <a name="ref"></a>REF  
 [Odkaz vytvoří odkaz](ref-entity-sql.md) na instanci typu entity. Následující dotaz například vrátí odkazy na každou entitu objednávky v sadě entit Orders:  
  
```  
SELECT REF(o) AS OrderID FROM Orders AS o  
```  
  
 Výstup:  
  
|Value|  
|-----------|  
|1|  
|2|  
|3|  
|...|  
  
 Následující příklad používá operátor extrakce vlastností (.) pro přístup k vlastnosti entity. Při použití operátoru extrakce vlastností je odkaz automaticky odkázat.  
  
 Příklad:  
  
```  
SELECT VALUE REF(p).Name FROM   
    AdventureWorksEntities.Product as p  
```  
  
 Výstup:  
  
|Value|  
|-----------|  
|Přizpůsobitelná rasy|  
|Stojan kol pro všechny účely|  
|Zakončení loga AWC|  
|...|  
  
### <a name="deref"></a>DEREF  
 [DEREF](deref-entity-sql.md) odkazuje na referenční hodnotu a vytváří výsledek tohoto odkázání. Následující dotaz například vytváří entity objednávek pro jednotlivé objednávky v sadě entit Orders: `SELECT DEREF(o2.r) FROM (SELECT REF(o) AS r FROM LOB.Orders AS o) AS o2`..  
  
 Příklad:  
  
```  
SELECT VALUE DEREF(REF(p)).Name FROM   
    AdventureWorksEntities.Product as p  
```  
  
 Výstup:  
  
|Value|  
|-----------|  
|Přizpůsobitelná rasy|  
|Stojan kol pro všechny účely|  
|Zakončení loga AWC|  
|...|  
  
### <a name="createref-and-key"></a>CREATEREF A KLÍČ  
 [CREATEREF](createref-entity-sql.md) vytvoří odkaz, který projde klíč. [Klíč](key-entity-sql.md) extrahuje klíčovou část výrazu s odkazem na typ.  
  
 Příklad:  
  
```  
SELECT VALUE Key(CreateRef(AdventureWorksEntities.Product, row(p.ProductID)))   
    FROM AdventureWorksEntities.Product as p  
```  
  
 Výstup:  
  
|ProductID|  
|---------------|  
|980|  
|365|  
|771|  
|...|  
  
## <a name="functions"></a>Funkce  
  
### <a name="canonical"></a>Canonical  
 Obor názvů pro [kanonické funkce](canonical-functions.md) je EDM, jako `Edm.Length("string")`v. Není nutné zadávat obor názvů, pokud není importován jiný obor názvů, který obsahuje funkci se stejným názvem jako kanonická funkce. Pokud mají dva obory názvů stejnou funkci, měl by uživatel určit celé jméno.  
  
 Příklad:  
  
```  
SELECT Length(c. FirstName) As NameLen FROM   
    AdventureWorksEntities.Contact AS c   
    WHERE c.ContactID BETWEEN 10 AND 12  
```  
  
 Výstup:  
  
|NameLen|  
|-------------|  
|6|  
|6|  
|5|  
  
### <a name="microsoft-provider-specific"></a>Specifické pro poskytovatele Microsoftu  
 [Funkce specifické pro poskytovatele společnosti Microsoft](../sqlclient-for-ef-functions.md) jsou v `SqlServer` oboru názvů.  
  
 Příklad:  
  
```  
SELECT SqlServer.LEN(c.EmailAddress) As EmailLen FROM   
    AdventureWorksEntities.Contact AS c WHERE   
    c.ContactID BETWEEN 10 AND 12  
```  
  
 Výstup:  
  
|EmailLen|  
|--------------|  
|27|  
|27|  
|26|  
  
## <a name="namespaces"></a>Jmenné prostory  
 [Použití](using-entity-sql.md) určuje obory názvů použité ve výrazu dotazu.  
  
 Příklad:  
  
```  
using SqlServer; LOWER('AA');  
```  
  
 Výstup:  
  
|Value|  
|-----------|  
|aa|  
  
## <a name="paging"></a>Stránkování  
 Stránkování lze vyjádřit deklarováním dílčích klauzulí [Skip](skip-entity-sql.md) a [limit](limit-entity-sql.md) na klauzuli [ORDER by](order-by-entity-sql.md) .  
  
 Příklad:  
  
```  
SELECT c.ContactID as ID, c.LastName as Name FROM   
    AdventureWorks.Contact AS c ORDER BY c.ContactID SKIP 9 LIMIT 3;  
```  
  
 Výstup:  
  
|id|Name|  
|--------|----------|  
|10|Adina|  
|11|Agcaoili|  
|12|Aguilar|  
  
## <a name="grouping"></a>Seskupování  
 [Seskupení podle](group-by-entity-sql.md) určuje skupiny, do kterých se mají umístit objekty vrácené výrazem dotazu ([Select](select-entity-sql.md)).  
  
 Příklad:  
  
```  
SELECT VALUE name FROM AdventureWorksEntities.Product as P   
    GROUP BY P.Name HAVING MAX(P.ListPrice) > 5  
```  
  
 Výstup:  
  
|name|  
|----------|  
|Sestavení pro horská místa|  
|Sestavení ML horských sedadel|  
|HL – sestavení pracovních stanic|  
|...|  
  
## <a name="navigation"></a>Navigace  
 Operátor navigace mezi relacemi umožňuje procházet relaci z jedné entity (od konce) do jiné (do konce). [Navigace](navigate-entity-sql.md) bere typ vztahu kvalifikovaný jako \<obor názvů >.\< název typu vztahu >. Funkce Navigate vrátí\<ref T >, pokud mohutnost má končit 1. Pokud mohutnost do konce má hodnotu n, vrátí se kolekce < ref\<T > >.  
  
 Příklad:  
  
```  
SELECT a.AddressID, (SELECT VALUE DEREF(v) FROM   
    NAVIGATE(a, AdventureWorksModel.FK_SalesOrderHeader_Address_BillToAddressID) AS v)   
    FROM AdventureWorksEntities.Address AS a  
```  
  
 Výstup:  
  
|AddressID|  
|---------------|  
|1|  
|2|  
|3|  
|...|  
  
## <a name="select-value-and-select"></a>VYBERTE HODNOTU A VYBERTE  
  
### <a name="select-value"></a>VYBRAT HODNOTU  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]poskytuje klauzuli SELECT VALUE pro přeskočení vytváření implicitních řádků. V klauzuli SELECT VALUE lze zadat pouze jednu položku. Je-li použita taková klauzule, není kolem položek v klauzuli SELECT vytvořena obálka řádku a může být vytvořena kolekce požadovaného tvaru, například: `SELECT VALUE a`.  
  
 Příklad:  
  
```  
SELECT VALUE p.Name FROM AdventureWorksEntities.Product as p  
```  
  
 Výstup:  
  
|Name|  
|----------|  
|Přizpůsobitelná rasy|  
|Stojan kol pro všechny účely|  
|Zakončení loga AWC|  
|...|  
  
### <a name="select"></a>SELECT  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]také poskytuje konstruktor Row pro vytvoření libovolných řádků. Vyberte možnost přebírá jeden nebo více prvků v projekci a výsledkem je datový záznam s poli, například: `SELECT a, b, c`.  
  
 Příklad:  
  
 Jako výstup p vyberte p.Name, p. ProductID z AdventureWorksEntities. Product:  
  
|Name|ProductID|  
|----------|---------------|  
|Přizpůsobitelná rasy|1|  
|Stojan kol pro všechny účely|879|  
|Zakončení loga AWC|712|  
|...|...|  
  
## <a name="case-expression"></a>VÝRAZ CASE  
 [Výraz Case](case-entity-sql.md) vyhodnocuje sadu logických výrazů pro určení výsledku.  
  
 Příklad:  
  
```  
CASE WHEN AVG({25,12,11}) < 100 THEN TRUE ELSE FALSE END  
```  
  
 Výstup:  
  
|Value|  
|-----------|  
|PODMÍNKA|  
  
## <a name="see-also"></a>Viz také:

- [Reference k Entity SQL](entity-sql-reference.md)
- [Přehled Entity SQL](entity-sql-overview.md)
