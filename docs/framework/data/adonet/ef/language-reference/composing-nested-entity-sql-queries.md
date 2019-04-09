---
title: Sestavování dotazů s vnořeným jazykem Entity SQL
ms.date: 03/30/2017
ms.assetid: 685d4cd3-2c1f-419f-bb46-c9d97a351eeb
ms.openlocfilehash: 4d6892e96cfbc9c5ba9d389aa03588c5133c7943
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59137979"
---
# <a name="composing-nested-entity-sql-queries"></a>Sestavování dotazů s vnořeným jazykem Entity SQL
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] je bohatou jazykovou funkční. Základním pilířem pracovního [!INCLUDE[esql](../../../../../../includes/esql-md.md)] je výraz. Na rozdíl od běžných SQL [!INCLUDE[esql](../../../../../../includes/esql-md.md)] není omezena pouze na sadu tabulkovém výsledku: [!INCLUDE[esql](../../../../../../includes/esql-md.md)] podporuje vytváření složitých výrazů, které můžou mít literály, parametry nebo vnořené výrazy. Hodnotu ve výrazu můžete s parametry nebo vytvořit další výrazu.  
  
## <a name="nested-expressions"></a>Vnořené výrazy  
 Vnořený výraz může být umístěna kdekoli hodnotu typu, který vrátí je přijat. Příklad:  
  
```  
-- Returns a hierarchical collection of three elements at top-level.   
-- x must be passed in the parameter collection.  
ROW(@x, {@x}, {@x, 4, 5}, {@x, 7, 8, 9})  
  
-- Returns a hierarchical collection of one element at top-level.  
-- x must be passed in the parameter collection.  
{{{@x}}};  
```  
  
 Vnořený dotaz je možné použít v klauzuli projekce. Příklad:  
  
```  
-- Returns a collection of rows where each row contains an Address entity.  
-- and a collection of references to its corresponding SalesOrderHeader entities.  
SELECT address, (SELECT DEREF(soh)   
                    FROM NAVIGATE(address, AdventureWorksModel.FK_SalesOrderHeader_Address_BillToAddressID) AS soh)   
                    AS salesOrderHeader FROM AdventureWorksEntities.Address AS address  
```  
  
 V [!INCLUDE[esql](../../../../../../includes/esql-md.md)], vnořené dotazy musí být vždy uzavřen v závorkách:  
  
```  
-- Pseudo-Entity SQL  
( SELECT …  
FROM … )  
UNION ALL  
( SELECT …  
FROM … );  
```  
  
 Následující příklad ukazuje, jak správně vnořovat výrazy v [!INCLUDE[esql](../../../../../../includes/esql-md.md)]: [Postupy: Pořadí sjednocení dva dotazy](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896299(v=vs.100)).  
  
## <a name="nested-queries-in-projection"></a>Vnořené dotazy v projekci  
 Vnořené dotazy v klauzuli projektu může získat přeloženy do kartézský součin dotazy na serveru. V některých back-end serverů, včetně serveru SQL Server to může způsobit TempDB tabulka, která má být velmi rozsáhlé, což nepříznivě ovlivnit výkon serveru.  
  
 Následuje příklad tohoto dotazu:  
  
```  
SELECT c, (SELECT c, (SELECT c FROM AdventureWorksModel.Vendor AS c  ) As Inner2 FROM AdventureWorksModel.JobCandidate AS c  ) As Inner1 FROM AdventureWorksModel.EmployeeDepartmentHistory AS c  
```  
  
## <a name="ordering-nested-queries"></a>Řazení vnořené dotazy  
 V rozhraní Entity Framework může být vnořený výraz umístěna kdekoli v dotazu. Protože Entity SQL umožňuje velkou flexibilitu při psaní dotazů, je možné napsat dotaz, který obsahuje má za výsledek řazení vnořené dotazů. Nezachová se však pořadí vnořeného dotazu.  
  
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
  
## <a name="see-also"></a>Viz také:

- [Přehled Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
