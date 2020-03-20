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
# <a name="entity-sql-quick-reference"></a>Stručné reference k Entity SQL
Toto téma obsahuje [!INCLUDE[esql](../../../../../../includes/esql-md.md)] rychlý odkaz na dotazy. Dotazy v tomto tématu jsou založeny na adventureworks prodejní model.  
  
## <a name="literals"></a>Literály  
  
### <a name="string"></a>Řetězec  
 Existují literály řetězce znaků Unicode a non-Unicode. Řetězce Unicode jsou předřazeny n. Například `N'hello'`.  
  
 Následuje příklad literálu řetězce bez Unicode:  
  
```sql  
'hello'  
--same as  
"hello"  
```  
  
 Výstup:  
  
|Hodnota|  
|-----------|  
|hello|  
  
### <a name="datetime"></a>DateTime  
 V DateTime literály jsou povinné části data a času. Neexistují žádné výchozí hodnoty.  
  
 Příklad:  
  
```sql  
DATETIME '2006-12-25 01:01:00.000'
--same as  
DATETIME '2006-12-25 01:01'  
```  
  
 Výstup:  
  
|Hodnota|  
|-----------|  
|12/25/2006 1:01:00|  
  
### <a name="integer"></a>Integer  
 Celé číslo literály může být typu Int32 (123), UInt32 (123U), Int64 (123L) a UInt64 (123UL).  
  
 Příklad:  
  
```sql  
--a collection of integers  
{1, 2, 3}  
```  
  
 Výstup:  
  
|Hodnota|  
|-----------|  
|1|  
|2|  
|3|  
  
### <a name="other"></a>Ostatní  
 Další literály [!INCLUDE[esql](../../../../../../includes/esql-md.md)] podporované jsou Guid, Binary, Float/Double, `null`Decimal a . Null literály [!INCLUDE[esql](../../../../../../includes/esql-md.md)] v jsou považovány za kompatibilní s každý jiný typ v koncepční model.  
  
## <a name="type-constructors"></a>Konstruktory typu  
  
### <a name="row"></a>ROW  
 [ROW](row-entity-sql.md) vytvoří anonymní, strukturálně zadaný (záznam) hodnotu jako v:`ROW(1 AS myNumber, ‘Name’ AS myName).`  
  
 Příklad:  
  
```sql  
SELECT VALUE row (product.ProductID AS ProductID, product.Name
    AS ProductName) FROM AdventureWorksEntities.Product AS product
```  
  
 Výstup:  
  
|ProductID|Name (Název)|  
|---------------|----------|  
|1|Nastavitelná rasa|  
|879|Univerzální stojan na kola|  
|712|Víčko loga AWC|  
|...|...|  
  
### <a name="multiset"></a>MULTISET  
 [MULTISET](multiset-entity-sql.md) vytváří kolekce, jako jsou:  
  
 `MULTISET(1,2,2,3)` `--same as`-`{1,2,2,3}.`  
  
 Příklad:  
  
```sql  
SELECT VALUE product FROM AdventureWorksEntities.Product AS product WHERE product.ListPrice IN MultiSet (125, 300)  
```  
  
 Výstup:  
  
|ProductID|Name (Název)|Číslo produktu|…|  
|---------------|----------|-------------------|-------|  
|842|Touring-Kufry, Velké|PA-T100|…|  
  
### <a name="object"></a>Objekt  
 [Pojmenovaný typ konstruktoru](named-type-constructor-entity-sql.md) konstrukce (pojmenované) uživatelem `person("abc", 12)`definované objekty, například .  
  
 Příklad:  
  
```sql  
SELECT VALUE AdventureWorksModel.SalesOrderDetail (o.SalesOrderDetailID, o.CarrierTrackingNumber, o.OrderQty,
o.ProductID, o.SpecialOfferID, o.UnitPrice, o.UnitPriceDiscount,
o.rowguid, o.ModifiedDate) FROM AdventureWorksEntities.SalesOrderDetail
AS o  
```  
  
 Výstup:  
  
|SalesOrderDetailID|Číslo CarrierTrackingNumber|OrderQty|ProductID|...|  
|------------------------|---------------------------|--------------|---------------|---------|  
|1|4911-403C-98|1|776|...|  
|2|4911-403C-98|3|777|...|  
|...|...|...|...|...|  
  
## <a name="references"></a>Odkazy  
  
### <a name="ref"></a>REF  
 [REF](ref-entity-sql.md) vytvoří odkaz na instanci typu entity. Například následující dotaz vrátí odkazy na každou entitu Objednávka v sadě entit Objednávky:  
  
```sql  
SELECT REF(o) AS OrderID FROM Orders AS o  
```  
  
 Výstup:  
  
|Hodnota|  
|-----------|  
|1|  
|2|  
|3|  
|...|  
  
 Následující příklad používá operátor extrakce vlastnosti (.) pro přístup k vlastnosti entity. Při použití operátoru extrakce vlastnosti je odkaz automaticky odkazován.  
  
 Příklad:  
  
```sql  
SELECT VALUE REF(p).Name FROM
    AdventureWorksEntities.Product AS p
```  
  
 Výstup:  
  
|Hodnota|  
|-----------|  
|Nastavitelná rasa|  
|Univerzální stojan na kola|  
|Víčko loga AWC|  
|...|  
  
### <a name="deref"></a>DEREF  
 [DEREF](deref-entity-sql.md) dereferences referenční hodnotu a vytváří výsledek tohoto dereference. Například následující dotaz vytvoří entity Objednávka pro každou objednávku `SELECT DEREF(o2.r) FROM (SELECT REF(o) AS r FROM LOB.Orders AS o) AS o2`v sadě entit Objednávky: ..  
  
 Příklad:  
  
```sql  
SELECT VALUE DEREF(REF(p)).Name FROM
    AdventureWorksEntities.Product AS p
```  
  
 Výstup:  
  
|Hodnota|  
|-----------|  
|Nastavitelná rasa|  
|Univerzální stojan na kola|  
|Víčko loga AWC|  
|...|  
  
### <a name="createref-and-key"></a>CREATEREF A KLÍČ  
 [CREATEREF](createref-entity-sql.md) vytvoří odkaz předání klíče. [KEY](key-entity-sql.md) extrahuje klíčovou část výrazu s odkazem na typ.  
  
 Příklad:  
  
```sql  
SELECT VALUE Key(CreateRef(AdventureWorksEntities.Product, row(p.ProductID)))
    FROM AdventureWorksEntities.Product AS p
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
 Obor názvů pro [kanonické funkce](canonical-functions.md) je `Edm.Length("string")`Edm, jako v . Není nutné zadávat obor názvů, pokud není importován jiný obor názvů, který obsahuje funkci se stejným názvem jako kanonická funkce. Pokud dva obory názvů mají stejnou funkci, uživatel by měl určit celé jméno.  
  
 Příklad:  
  
```sql  
SELECT Length(c. FirstName) AS NameLen FROM
    AdventureWorksEntities.Contact AS c
    WHERE c.ContactID BETWEEN 10 AND 12  
```  
  
 Výstup:  
  
|NázevLen|  
|-------------|  
|6|  
|6|  
|5|  
  
### <a name="microsoft-provider-specific"></a>Specifické pro poskytovatele společnosti Microsoft  
 [Funkce specifické pro poskytovatele](../sqlclient-for-ef-functions.md) `SqlServer` společnosti Microsoft jsou v oboru názvů.  
  
 Příklad:  
  
```sql  
SELECT SqlServer.LEN(c.EmailAddress) AS EmailLen FROM
    AdventureWorksEntities.Contact AS c WHERE
    c.ContactID BETWEEN 10 AND 12  
```  
  
 Výstup:  
  
|E-maillen|  
|--------------|  
|27|  
|27|  
|26|  
  
## <a name="namespaces"></a>Obory názvů  
 [Použití](using-entity-sql.md) určuje obory názvů používané ve výrazu dotazu.  
  
 Příklad:  
  
```sql  
using SqlServer; LOWER('AA');  
```  
  
 Výstup:  
  
|Hodnota|  
|-----------|  
|aa|  
  
## <a name="paging"></a>Stránkování  
 Stránkování lze vyjádřit deklarováním podklauzulí [SKIP](skip-entity-sql.md) a [LIMIT](limit-entity-sql.md) do klauzule [ORDER BY.](order-by-entity-sql.md)  
  
 Příklad:  
  
```sql  
SELECT c.ContactID as ID, c.LastName AS Name FROM
    AdventureWorks.Contact AS c ORDER BY c.ContactID SKIP 9 LIMIT 3;  
```  
  
 Výstup:  
  
|ID|Name (Název)|  
|--------|----------|  
|10|Adina|  
|11|Agcaoili|  
|12|Aguilar|  
  
## <a name="grouping"></a>Seskupování  
 [SESKUPENÍ PODLE](group-by-entity-sql.md) určuje skupiny, do kterých mají být umístěny objekty vrácené výrazem dotazu[(SELECT).](select-entity-sql.md)  
  
 Příklad:  
  
```sql  
SELECT VALUE name FROM AdventureWorksEntities.Product AS P
    GROUP BY P.Name HAVING MAX(P.ListPrice) > 5  
```  
  
 Výstup:  
  
|jméno|  
|----------|  
|LL Montáž horských sedadel|  
|Sestava horského sedadla ML|  
|Hl Horské sídlo shromáždění|  
|...|  
  
## <a name="navigation"></a>Navigace  
 Operátor navigace vztahu umožňuje přejít přes vztah z jedné entity (z konce) do druhé (do konce). [FUNKCE NAVIGATE](navigate-entity-sql.md) přebírá typ \<vztahu kvalifikovaný jako obor názvů>. \<> název typu relace. Navigate vrátí\<Ref T> pokud mohutnost do konce je 1. Pokud mohutnost do konce je n, kolekce\<<Ref T>> budou vráceny.  
  
 Příklad:  
  
```sql  
SELECT a.AddressID, (SELECT VALUE DEREF(v) FROM
    NAVIGATE(a, AdventureWorksModel.FK_SalesOrderHeader_Address_BillToAddressID) AS v)
    FROM AdventureWorksEntities.Address AS a  
```  
  
 Výstup:  
  
|Adresní ID|  
|---------------|  
|1|  
|2|  
|3|  
|...|  
  
## <a name="select-value-and-select"></a>VYBRAT HODNOTU A VYBRAT  
  
### <a name="select-value"></a>VYBRAT HODNOTU  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]poskytuje klauzuli SELECT VALUE přeskočit implicitní konstrukci řádku. V klauzuli SELECT VALUE lze zadat pouze jednu položku. Při použití takové klauzule je vytvořen anulování řádku kolem položky v select klauzule a kolekce požadovaného tvaru lze vytvořit, například: `SELECT VALUE a`.  
  
 Příklad:  
  
```sql  
SELECT VALUE p.Name FROM AdventureWorksEntities.Product AS p
```  
  
 Výstup:  
  
|Name (Název)|  
|----------|  
|Nastavitelná rasa|  
|Univerzální stojan na kola|  
|Víčko loga AWC|  
|...|  
  
### <a name="select"></a>SELECT  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]také poskytuje konstruktor řádku pro vytvoření libovolných řádků. SELECT převezme jeden nebo více prvků v projekci a `SELECT a, b, c`výsledkem je datový záznam s poli, například: .  
  
 Příklad:  
  
 SELECT p.Name, p.ProductID from AdventureWorksEntities.Product as p Výstup:  
  
|Name (Název)|ProductID|  
|----------|---------------|  
|Nastavitelná rasa|1|  
|Univerzální stojan na kola|879|  
|Víčko loga AWC|712|  
|...|...|  
  
## <a name="case-expression"></a>VÝRAZ PŘÍPADU  
 [Výraz případu](case-entity-sql.md) vyhodnotí sadu logických výrazů k určení výsledku.  
  
 Příklad:  
  
```sql  
CASE WHEN AVG({25,12,11}) < 100 THEN TRUE ELSE FALSE END  
```  
  
 Výstup:  
  
|Hodnota|  
|-----------|  
|TRUE|  
  
## <a name="see-also"></a>Viz také

- [Reference k Entity SQL](entity-sql-reference.md)
- [Přehled Entity SQL](entity-sql-overview.md)
