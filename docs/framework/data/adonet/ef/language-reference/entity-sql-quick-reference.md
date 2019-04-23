---
title: Stručné reference k Entity SQL
ms.date: 03/30/2017
ms.assetid: e53dad9e-5e83-426e-abb4-be3e78e3d6dc
ms.openlocfilehash: b4e3eaf8abd82b63fa2663b47f878ecfa9584897
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59207068"
---
# <a name="entity-sql-quick-reference"></a>Stručné reference k Entity SQL
Toto téma poskytuje rychlý odkaz na [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dotazy. Dotazy v tomto tématu jsou založeny na modelu AdventureWorks Sales.  
  
## <a name="literals"></a>Literály  
  
### <a name="string"></a>String  
 Existují řetězcové literály znaků Unicode a kódování Unicode. Řetězce Unicode jsou předponou N. Například `N'hello'`.  
  
 Následuje příklad Non-Unicode řetězcového literálu:  
  
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
 V literálech datum a čas datum a čas části jsou povinné. Neexistují žádné výchozí hodnoty.  
  
 Příklad:  
  
```  
DATETIME '2006-12-25 01:01:00.000'   
--same as  
DATETIME '2006-12-25 01:01'  
```  
  
 Výstup:  
  
|Value|  
|-----------|  
|12/25/2006 1:01:00: 00|  
  
### <a name="integer"></a>Integer  
 Literály celých čísel může být typu Int32 (123), UInt32 (123U), Int64 (123L) a UInt64 (123UL).  
  
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
 Ostatní literály, které podporuje [!INCLUDE[esql](../../../../../../includes/esql-md.md)] jsou identifikátor Guid, binární soubor, Float nebo Double, Decimal, a `null`. Hodnota Null, literály v [!INCLUDE[esql](../../../../../../includes/esql-md.md)] jsou považovány za kompatibilní se každý jiný typ v konceptuálním modelu.  
  
## <a name="type-constructors"></a>Konstruktory typu  
  
### <a name="row"></a>ROW  
 [ŘÁDEK](../../../../../../docs/framework/data/adonet/ef/language-reference/row-entity-sql.md) vytvoří anonymní, typované strukturálně (záznamů) hodnotu jako v: `ROW(1 AS myNumber, ‘Name’ AS myName).`  
  
 Příklad:  
  
```  
SELECT VALUE row (product.ProductID as ProductID, product.Name   
    as ProductName) FROM AdventureWorksEntities.Product AS product  
```  
  
 Výstup:  
  
|ProductID|Název|  
|---------------|----------|  
|1|Měnitelné závodu|  
|879|Univerzální kol samostatné|  
|712|AWC Logo zakončení|  
|...|...|  
  
### <a name="multiset"></a>MULTISET  
 [MULTISET](../../../../../../docs/framework/data/adonet/ef/language-reference/multiset-entity-sql.md) konstrukce kolekcí, jako například:  
  
 `MULTISET(1,2,2,3)` `--same as`-`{1,2,2,3}.`  
  
 Příklad:  
  
```  
SELECT VALUE product FROM AdventureWorksEntities.Product AS product WHERE product.ListPrice IN MultiSet (125, 300)  
```  
  
 Výstup:  
  
|ProductID|Název|ProductNumber|…|  
|---------------|----------|-------------------|-------|  
|842|Touring-Panniers, Large|PA-T100|…|  
  
### <a name="object"></a>Objekt  
 [Konstruktor typu s názvem](../../../../../../docs/framework/data/adonet/ef/language-reference/named-type-constructor-entity-sql.md) vytvoří (pojmenované) uživatelem definované objekty, jako například `person("abc", 12)`.  
  
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
 [REF](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md) vytvoří odkaz na instanci typu entity. Například následující dotaz vrátí odkazy na jednotlivé entity pořadí v sadě entit objednávky:  
  
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
  
 Následující příklad používá vlastnost extrakce – operátor (.) pro přístup k vlastnosti entity. Při extrakci operátor vlastnost se používá, odkaz je automaticky přes ukazatel.  
  
 Příklad:  
  
```  
SELECT VALUE REF(p).Name FROM   
    AdventureWorksEntities.Product as p  
```  
  
 Výstup:  
  
|Value|  
|-----------|  
|Měnitelné závodu|  
|Univerzální kol samostatné|  
|AWC Logo zakončení|  
|...|  
  
### <a name="deref"></a>DEREF  
 [DEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md) přístupů přes ukazatel, hodnota odkazu a vytváří výsledek, který přístup přes ukazatel. Například následující dotaz vyprodukuje entity pořadí pro každé pořadí v sadě entit objednávky: `SELECT DEREF(o2.r) FROM (SELECT REF(o) AS r FROM LOB.Orders AS o) AS o2`...  
  
 Příklad:  
  
```  
SELECT VALUE DEREF(REF(p)).Name FROM   
    AdventureWorksEntities.Product as p  
```  
  
 Výstup:  
  
|Value|  
|-----------|  
|Měnitelné závodu|  
|Univerzální kol samostatné|  
|AWC Logo zakončení|  
|...|  
  
### <a name="createref-and-key"></a>CREATEREF A KLÍČ  
 [CREATEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md) vytvoří odkaz předáním klíče. [KLÍČ](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md) extrahuje část výraz s odkaz na typ klíče.  
  
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
 Obor názvů pro [kanonické funkce](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md) je Edm, stejně jako v `Edm.Length("string")`. Není nutné zadat obor názvů, pokud jiný obor názvů se importuje, který obsahuje funkce se stejným názvem jako kanonické funkce. Pokud dva obory názvů mají stejnou funkci, uživatel by měl konkrétní úplný název.  
  
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
  
### <a name="microsoft-provider-specific"></a>Specifické pro společnost Microsoft poskytovatele  
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
 Stránkování může být vyjádřena pomocí deklarace [přeskočit](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md) a [LIMIT](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md) dílčí klauzule [klauzule ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) klauzuli.  
  
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
|Sestavení místo LL Horská oblast|  
|Sestavení licence ML Horská oblast|  
|HL Mountain místo sestavení|  
|...|  
  
## <a name="navigation"></a>Navigace  
 Operátor navigace vztah umožňuje přejít nad vztah z entit (od konce) do jiného (Chcete-li ukončit). [NAVIGOVAT](../../../../../../docs/framework/data/adonet/ef/language-reference/navigate-entity-sql.md) přijímá typ vztahu kvalifikovány jako \<oboru názvů >.\< Název typu vztahu >. Přejděte vrátí Ref\<T > Pokud Kardinalita do konce je 1. Pokud Kardinalita do konce je n, kolekce < Ref\<T >> bude vrácen.  
  
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
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] poskytuje klauzule SELECT VALUE pro přeskočení konstrukce implicitní řádek. V klauzuli SELECT VALUE lze zadat pouze jednu položku. Při těchto klauzulí se používá, je vytvořen žádný řádek obálku kolem položek v klauzuli SELECT a kolekce na požadovaný tvar je možné vytvořit, například: `SELECT VALUE a`.  
  
 Příklad:  
  
```  
SELECT VALUE p.Name FROM AdventureWorksEntities.Product as p  
```  
  
 Výstup:  
  
|Název|  
|----------|  
|Měnitelné závodu|  
|Univerzální kol samostatné|  
|AWC Logo zakončení|  
|...|  
  
### <a name="select"></a>SELECT  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] také poskytuje konstruktoru řádku k vytvoření libovolné řádky. Vyberte použije jeden nebo více prvků v projekci a výsledky datového záznamu vložením polí, například: `SELECT a, b, c`.  
  
 Příklad:  
  
 Vyberte p.Name, p.ProductID z AdventureWorksEntities.Product jako p výstup:  
  
|Název|ProductID|  
|----------|---------------|  
|Měnitelné závodu|1|  
|Univerzální kol samostatné|879|  
|AWC Logo zakončení|712|  
|...|...|  
  
## <a name="case-expression"></a>VÝRAZ CASE  
 [Výraz malá a velká](../../../../../../docs/framework/data/adonet/ef/language-reference/case-entity-sql.md) vyhodnotí sadu logických výrazů k určení výsledků.  
  
 Příklad:  
  
```  
CASE WHEN AVG({25,12,11}) < 100 THEN TRUE ELSE FALSE END  
```  
  
 Výstup:  
  
|Value|  
|-----------|  
|HODNOTA TRUE|  
  
## <a name="see-also"></a>Viz také:

- [Reference k Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [Přehled Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
