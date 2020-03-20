---
title: Sestavování dotazů s vnořeným jazykem Entity SQL
ms.date: 03/30/2017
ms.assetid: 685d4cd3-2c1f-419f-bb46-c9d97a351eeb
ms.openlocfilehash: 6b2fc9a32fc30d205b9c33257bf98781cfa07499
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150386"
---
# <a name="composing-nested-entity-sql-queries"></a>Sestavování dotazů s vnořeným jazykem Entity SQL
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]je bohatý funkční jazyk. Stavebním kamenem [!INCLUDE[esql](../../../../../../includes/esql-md.md)] je výraz. Na rozdíl [!INCLUDE[esql](../../../../../../includes/esql-md.md)] od běžných SQL není omezena [!INCLUDE[esql](../../../../../../includes/esql-md.md)] na tabulkovou sadu výsledků: podporuje skládání složitých výrazů, které mohou mít literály, parametry nebo vnořené výrazy. Hodnota ve výrazu může být parametrizována nebo složena z jiného výrazu.  
  
## <a name="nested-expressions"></a>Vnořené výrazy  
 Vnořený výraz lze umístit kdekoli, kde je přijata hodnota typu, který vrátí. Například:  
  
```sql  
-- Returns a hierarchical collection of three elements at top-level.
-- x must be passed in the parameter collection.  
ROW(@x, {@x}, {@x, 4, 5}, {@x, 7, 8, 9})  
  
-- Returns a hierarchical collection of one element at top-level.  
-- x must be passed in the parameter collection.  
{{{@x}}};  
```  
  
 Vnořený dotaz lze umístit do projekční klauzule. Například:  
  
```sql  
-- Returns a collection of rows where each row contains an Address entity.  
-- and a collection of references to its corresponding SalesOrderHeader entities.  
SELECT address, (SELECT DEREF(soh)
                    FROM NAVIGATE(address, AdventureWorksModel.FK_SalesOrderHeader_Address_BillToAddressID) AS soh)
                    AS salesOrderHeader FROM AdventureWorksEntities.Address AS address  
```  
  
 V [!INCLUDE[esql](../../../../../../includes/esql-md.md)], vnořené dotazy musí být vždy uzavřeny v závorky:  
  
```sql  
-- Pseudo-Entity SQL  
( SELECT …  
FROM … )  
UNION ALL  
( SELECT …  
FROM … );  
```  
  
 Následující příklad ukazuje, jak správně vnořit výrazy do [!INCLUDE[esql](../../../../../../includes/esql-md.md)]: How [to: Order the Union of Two Queries](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896299(v=vs.100)).  
  
## <a name="nested-queries-in-projection"></a>Vnořené dotazy v projekci  
 Vnořené dotazy v klauzuli projektu může získat přeloženy do dotazů kartézského produktu na serveru. V některých serverech back-end, včetně SQL Server, to může způsobit, že tabulka TempDB získat velmi velké, což může nepříznivě ovlivnit výkon serveru.  
  
 Následuje příklad takového dotazu:  
  
```sql  
SELECT c, (SELECT c, (SELECT c FROM AdventureWorksModel.Vendor AS c  ) As Inner2 FROM AdventureWorksModel.JobCandidate AS c  ) As Inner1 FROM AdventureWorksModel.EmployeeDepartmentHistory AS c  
```  
  
## <a name="ordering-nested-queries"></a>Řazení vnořených dotazů  
 V rámci entity vnořený výraz lze umístit kdekoli v dotazu. Protože Entity SQL umožňuje velkou flexibilitu při psaní dotazů, je možné napsat dotaz, který obsahuje řazení vnořených dotazů. Pořadí vnořeného dotazu však není zachováno.  
  
```sql  
-- The following query will order the results by last name.  
SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorksModel.Contact as C1  
        ORDER BY C1.LastName  
```  
  
```sql  
-- In the following query, ordering of the nested query is ignored.  
SELECT C2.FirstName, C2.LastName  
    FROM (SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorksModel.Contact as C1  
        ORDER BY C1.LastName) as C2  
```  
  
## <a name="see-also"></a>Viz také

- [Přehled Entity SQL](entity-sql-overview.md)
