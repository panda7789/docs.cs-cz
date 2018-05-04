---
title: Sestavování dotazů SQL vnořené Entity
ms.date: 03/30/2017
ms.assetid: 685d4cd3-2c1f-419f-bb46-c9d97a351eeb
ms.openlocfilehash: 92e3153350787ef75c48ee52f1b6c68e09e15b4b
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="composing-nested-entity-sql-queries"></a>Sestavování dotazů SQL vnořené Entity
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] je bohaté funkční jazyk. Stavební blok [!INCLUDE[esql](../../../../../../includes/esql-md.md)] je výraz. Na rozdíl od konvenční SQL [!INCLUDE[esql](../../../../../../includes/esql-md.md)] není omezeno na tabulkovém výslednou sadu: [!INCLUDE[esql](../../../../../../includes/esql-md.md)] podporuje skládání složité výrazy, které může mít literály, parametrů nebo vnořené výrazy. Hodnotu ve výrazu můžete parametry nebo složené některé výrazu.  
  
## <a name="nested-expressions"></a>Vnořené výrazy  
 Výraz vnořené můžete umístit kamkoli hodnotu typu, který vrátí byla přijata. Příklad:  
  
```  
-- Returns a hierarchical collection of three elements at top-level.   
-- x must be passed in the parameter collection.  
ROW(@x, {@x}, {@x, 4, 5}, {@x, 7, 8, 9})  
  
-- Returns a hierarchical collection of one element at top-level.  
-- x must be passed in the parameter collection.  
{{{@x}}};  
```  
  
 Vnořený dotaz se může v klauzuli projekce. Příklad:  
  
```  
-- Returns a collection of rows where each row contains an Address entity.  
-- and a collection of references to its corresponding SalesOrderHeader entities.  
SELECT address, (SELECT DEREF(soh)   
                    FROM NAVIGATE(address, AdventureWorksModel.FK_SalesOrderHeader_Address_BillToAddressID) AS soh)   
                    AS salesOrderHeader FROM AdventureWorksEntities.Address AS address  
```  
  
 V [!INCLUDE[esql](../../../../../../includes/esql-md.md)], vnořené dotazy musí být uzavřena vždy v závorkách:  
  
```  
-- Pseudo-Entity SQL  
( SELECT …  
FROM … )  
UNION ALL  
( SELECT …  
FROM … );  
```  
  
 Následující příklad ukazuje, jak lze vnořit správně výrazy v [!INCLUDE[esql](../../../../../../includes/esql-md.md)]: [postupy: řazení Union z dva dotazy](http://msdn.microsoft.com/library/853c583a-eaba-4400-830d-be974e735313).  
  
## <a name="nested-queries-in-projection"></a>Vnořené dotazy v projekci  
 Vnořené dotazy v klauzuli projektu, může získat přeložit na kartézský součin dotazy na serveru. V některých back-end serverů, včetně serveru SQL Server to může způsobit tabulky databáze TempDB získat velký, který může nepříznivě ovlivnit výkon serveru.  
  
 Následuje příklad takového dotazu:  
  
```  
SELECT c, (SELECT c, (SELECT c FROM AdventureWorksModel.Vendor AS c  ) As Inner2 FROM AdventureWorksModel.JobCandidate AS c  ) As Inner1 FROM AdventureWorksModel.EmployeeDepartmentHistory AS c  
```  
  
## <a name="ordering-nested-queries"></a>Řazení vnořené dotazy  
 V rozhraní Entity Framework mohou být výraz vnořené umístěny kdekoli v dotazu. Protože Entity SQL umožňuje flexibilitu v zápis dotazů, je možné vytvořit dotaz, který obsahuje řazení vnořené dotazy. Však není zachovávané pořadí vnořený dotaz.  
  
```  
-- The following query will order the results by last name.  
SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorksModel.Contact as C1  
        ORDER BY C1.LastName  
```  
  
```  
-- In the following query, ordering of the nested query is ignored.  
SELECT C2.FirstName, C2.LastName  
    FROM (SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorksModel.Contact as C1  
        ORDER BY C1.LastName) as C2  
```  
  
## <a name="see-also"></a>Viz také  
 [Přehled Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
