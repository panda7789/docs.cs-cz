---
title: Stručná referenční entity SQL
ms.date: 03/30/2017
ms.assetid: e53dad9e-5e83-426e-abb4-be3e78e3d6dc
ms.openlocfilehash: 0617ce96acaf5a6eafb2658cfe218cc8f4135f6e
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="entity-sql-quick-reference"></a>Stručná referenční entity SQL
Toto téma obsahuje Stručná referenční příručka pro [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dotazy. Dotazy v tomto tématu jsou založené na modelu prodeje společnosti AdventureWorks.  
  
## <a name="literals"></a>Literály  
  
### <a name="string"></a>String  
 Existují textové literály znak Unicode a kódování Unicode. Řetězců v kódu Unicode se přidá jako předpona s N. Například `N'hello'`.  
  
 Následuje příklad než Unicode řetězcový literál:  
  
```  
'hello'  
--same as  
"hello"  
```  
  
 Výstup:  
  
|Hodnota|  
|-----------|  
|Dobrý den|  
  
### <a name="datetime"></a>DateTime  
 V literálech datum a čas datum a čas části jsou povinné. Neexistují žádné výchozí hodnoty.  
  
 Příklad:  
  
```  
DATETIME '2006-12-25 01:01:00.000'   
--same as  
DATETIME '2006-12-25 01:01'  
```  
  
 Výstup:  
  
|Hodnota|  
|-----------|  
|12/25/2006 1:01:00: 00|  
  
### <a name="integer"></a>Integer  
 Můžou být celé číslo literály typu Int32 (123) UInt32 (123U), Int64 (123L) a UInt64 (123UL).  
  
 Příklad:  
  
```  
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
 Další literály nepodporuje [!INCLUDE[esql](../../../../../../includes/esql-md.md)] jsou identifikátor Guid, binární, typu Float/Double, Decimal, a `null`. Hodnota Null, literály v [!INCLUDE[esql](../../../../../../includes/esql-md.md)] se považují za kompatibilní s každou další typu v konceptuálním modelu.  
  
## <a name="type-constructors"></a>Konstruktory typu  
  
### <a name="row"></a>ŘÁDEK  
 [ŘÁDEK](../../../../../../docs/framework/data/adonet/ef/language-reference/row-entity-sql.md) vytvoří anonymní, strukturálně typované (záznamů) hodnotu jako v: `ROW(1 AS myNumber, ‘Name’ AS myName).`  
  
 Příklad:  
  
```  
SELECT VALUE row (product.ProductID as ProductID, product.Name   
    as ProductName) FROM AdventureWorksEntities.Product AS product  
```  
  
 Výstup:  
  
|ProductID|Název|  
|---------------|----------|  
|1|Upravit soupeření|  
|879|Všechny účely kolo úsporný režim|  
|712|AWC Logo zakončení|  
|...|...|  
  
### <a name="multiset"></a>MULTIMNOŽINA  
 [MULTIMNOŽINA](../../../../../../docs/framework/data/adonet/ef/language-reference/multiset-entity-sql.md) vytvoří kolekcí, jako například:  
  
 `MULTISET(1,2,2,3)` `--same as`-`{1,2,2,3}.`  
  
 Příklad:  
  
```  
SELECT VALUE product FROM AdventureWorksEntities.Product AS product WHERE product.ListPrice IN MultiSet (125, 300)  
```  
  
 Výstup:  
  
|ProductID|Název|ProductNumber|…|  
|---------------|----------|-------------------|-------|  
|842|Jízdních Panniers, velké|PA-T100|…|  
  
### <a name="object"></a>Objekt  
 [Konstruktor typu s názvem](../../../../../../docs/framework/data/adonet/ef/language-reference/named-type-constructor-entity-sql.md) vytvoří (s názvem) uživatelem definované objekty, například `person("abc", 12)`.  
  
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
 [REF](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md) vytvoří odkaz na typ instance entity. Například následující dotaz vrátí odkazy na každé pořadí entity v sadě entit objednávky:  
  
```  
SELECT REF(o) AS OrderID FROM Orders AS o  
```  
  
 Výstup:  
  
|Hodnota|  
|-----------|  
|1|  
|2|  
|3|  
|...|  
  
 Následující příklad používá operátor extrakce vlastnost (.) pro přístup k vlastnosti entity. Pokud operátor extrakce vlastnost se používá, je automaticky dereferenced odkaz.  
  
 Příklad:  
  
```  
SELECT VALUE REF(p).Name FROM   
    AdventureWorksEntities.Product as p  
```  
  
 Výstup:  
  
|Hodnota|  
|-----------|  
|Upravit soupeření|  
|Všechny účely kolo úsporný režim|  
|AWC Logo zakončení|  
|...|  
  
### <a name="deref"></a>DEREF  
 [DEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md) dereferences hodnota odkazu a vytváří výsledek této dereference. Například následující dotaz vytváří pořadí entity pro každé pořadí v sadě entit objednávky: `SELECT DEREF(o2.r) FROM (SELECT REF(o) AS r FROM LOB.Orders AS o) AS o2`...  
  
 Příklad:  
  
```  
SELECT VALUE DEREF(REF(p)).Name FROM   
    AdventureWorksEntities.Product as p  
```  
  
 Výstup:  
  
|Hodnota|  
|-----------|  
|Upravit soupeření|  
|Všechny účely kolo úsporný režim|  
|AWC Logo zakončení|  
|...|  
  
### <a name="createref-and-key"></a>CREATEREF A KLÍČ  
 [CREATEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md) vytvoří odkaz předávání klíč. [KLÍČ](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md) extrahuje část výraz obsahující odkaz na typ klíče.  
  
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
  
### <a name="canonical"></a>Kanonickém tvaru  
 Obor názvů pro [kanonické funkce](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md) je Edm, jako v `Edm.Length("string")`. Nemáte zadejte obor názvů, pokud jiný obor názvů je naimportována obsahující funkci se stejným názvem jako kanonické funkce. Pokud dva obory názvů mají stejnou funkci, uživatel má konkrétní úplný název.  
  
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
  
### <a name="microsoft-provider-specific"></a>Zprostředkovatel specifické pro společnost Microsoft  
 [Funkce specifické pro zprostředkovatele Microsoft](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md) v `SqlServer` oboru názvů.  
  
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
 [POMOCÍ](../../../../../../docs/framework/data/adonet/ef/language-reference/using-entity-sql.md) určuje oborů názvů používaných ve výrazu dotazu.  
  
 Příklad:  
  
```  
using SqlServer; LOWER('AA');  
```  
  
 Výstup:  
  
|Hodnota|  
|-----------|  
|aa|  
  
## <a name="paging"></a>Stránkování  
 Stránkování rozdíl lze vyjádřit pomocí deklarace [přeskočit](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md) a [LIMIT](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md) dílčí klauzule k [Order](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) klauzule.  
  
 Příklad:  
  
```  
SELECT c.ContactID as ID, c.LastName as Name FROM   
    AdventureWorks.Contact AS c ORDER BY c.ContactID SKIP 9 LIMIT 3;  
```  
  
 Výstup:  
  
|ID|Název|  
|--------|----------|  
|10|Adina|  
|11|Agcaoili|  
|12|Aguilar|  
  
## <a name="grouping"></a>Seskupování  
 [SESKUPENÍ podle](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md) Určuje skupiny, do které objektů vrácených dotazem ([vyberte](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)) výrazu mají být umístěny.  
  
 Příklad:  
  
```  
SELECT VALUE name FROM AdventureWorksEntities.Product as P   
    GROUP BY P.Name HAVING MAX(P.ListPrice) > 5  
```  
  
 Výstup:  
  
|name|  
|----------|  
|Le Horská stanici sestavení|  
|ML Horská stanici sestavení|  
|HL Horská stanici sestavení|  
|...|  
  
## <a name="navigation"></a>Navigace  
 Operátor navigační vztah můžete přejít přes vztah z jedné entity (od konce) na jiný (na konec). [NAVIGOVAT](../../../../../../docs/framework/data/adonet/ef/language-reference/navigate-entity-sql.md) trvá kvalifikovaný typ vztahu jako \<obor názvů >.\< Název typu vztahu >. Přejděte vrátí Ref\<T > Pokud mohutnost pro ukončení je 1. Pokud na kardinalitu pro ukončení je n, kolekce < Ref\<T >> bude vrácen.  
  
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
  
### <a name="select-value"></a>VYBERTE HODNOTU  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] poskytuje v klauzuli SELECT VALUE tak, aby přeskočil konstrukce implicitní řádek. V klauzuli SELECT VALUE lze zadat pouze jednu položku. Když se používá tato klauzule, sestavený žádný řádek obálku kolem položky v klauzuli SELECT a kolekce požadovaný tvar je možné vytvořit, například: `SELECT VALUE a`.  
  
 Příklad:  
  
```  
SELECT VALUE p.Name FROM AdventureWorksEntities.Product as p  
```  
  
 Výstup:  
  
|Název|  
|----------|  
|Upravit soupeření|  
|Všechny účely kolo úsporný režim|  
|AWC Logo zakončení|  
|...|  
  
### <a name="select"></a>VYBERTE  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] také poskytuje konstruktor row můžete vytvořit libovolný řádků. Vyberte trvá jeden či více elementů v projekci a má za následek záznam dat s poli, například: `SELECT a, b, c`.  
  
 Příklad:  
  
 Vyberte p.Name, p.ProductID z AdventureWorksEntities.Product jako p výstup:  
  
|Název|ProductID|  
|----------|---------------|  
|Upravit soupeření|1|  
|Všechny účely kolo úsporný režim|879|  
|AWC Logo zakončení|712|  
|...|...|  
  
## <a name="case-expression"></a>VÝRAZ CASE  
 [Případ výraz](../../../../../../docs/framework/data/adonet/ef/language-reference/case-entity-sql.md) vyhodnotí sadu logických výrazů k určení výsledku.  
  
 Příklad:  
  
```  
CASE WHEN AVG({25,12,11}) < 100 THEN TRUE ELSE FALSE END  
```  
  
 Výstup:  
  
|Hodnota|  
|-----------|  
|HODNOTA TRUE|  
  
## <a name="see-also"></a>Viz také  
 [Reference k Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [Přehled Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
