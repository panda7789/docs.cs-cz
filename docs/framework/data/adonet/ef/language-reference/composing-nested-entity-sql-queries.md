---
title: Sestavování dotazů s vnořeným jazykem Entity SQL
ms.date: 03/30/2017
ms.assetid: 685d4cd3-2c1f-419f-bb46-c9d97a351eeb
ms.openlocfilehash: 0ab92c1e41c89f141c3cbd37be3e1e18e64d9666
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833918"
---
# <a name="composing-nested-entity-sql-queries"></a>Sestavování dotazů s vnořeným jazykem Entity SQL
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] je bohatě funkční jazyk. Stavebním blokem [!INCLUDE[esql](../../../../../../includes/esql-md.md)] je výraz. Na rozdíl od konvenčního SQL [!INCLUDE[esql](../../../../../../includes/esql-md.md)] není omezen na tabulkovou sadu výsledků: [!INCLUDE[esql](../../../../../../includes/esql-md.md)] podporuje sestavování složitých výrazů, které mohou mít literály, parametry nebo vnořené výrazy. Hodnota ve výrazu může být Parametrizovaná nebo složená z nějakého jiného výrazu.  
  
## <a name="nested-expressions"></a>Vnořené výrazy  
 Vnořený výraz lze umístit kamkoli na libovolnou hodnotu typu, který vrátí. Příklad:  
  
```sql  
-- Returns a hierarchical collection of three elements at top-level.   
-- x must be passed in the parameter collection.  
ROW(@x, {@x}, {@x, 4, 5}, {@x, 7, 8, 9})  
  
-- Returns a hierarchical collection of one element at top-level.  
-- x must be passed in the parameter collection.  
{{{@x}}};  
```  
  
 Vnořený dotaz může být umístěn v klauzuli projekce. Příklad:  
  
```sql  
-- Returns a collection of rows where each row contains an Address entity.  
-- and a collection of references to its corresponding SalesOrderHeader entities.  
SELECT address, (SELECT DEREF(soh)   
                    FROM NAVIGATE(address, AdventureWorksModel.FK_SalesOrderHeader_Address_BillToAddressID) AS soh)   
                    AS salesOrderHeader FROM AdventureWorksEntities.Address AS address  
```  
  
 V [!INCLUDE[esql](../../../../../../includes/esql-md.md)] musí být vnořené dotazy vždy uzavřeny v závorkách:  
  
```sql  
-- Pseudo-Entity SQL  
( SELECT …  
FROM … )  
UNION ALL  
( SELECT …  
FROM … );  
```  
  
 Následující příklad ukazuje, jak správně vnořovat výrazy v [!INCLUDE[esql](../../../../../../includes/esql-md.md)]: [Postup: seřazení sjednocení dvou dotazů](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896299(v=vs.100)).  
  
## <a name="nested-queries-in-projection"></a>Vnořené dotazy v projekci  
 Vnořené dotazy v klauzuli Project mohou být přeloženy do Kartézskémch dotazů na produkt na serveru. V některých back-end serverech, včetně serveru SQL, to může způsobit, že by tabulka TempDB byla velmi velká, což může negativně ovlivnit výkon serveru.  
  
 Následuje příklad takového dotazu:  
  
```sql  
SELECT c, (SELECT c, (SELECT c FROM AdventureWorksModel.Vendor AS c  ) As Inner2 FROM AdventureWorksModel.JobCandidate AS c  ) As Inner1 FROM AdventureWorksModel.EmployeeDepartmentHistory AS c  
```  
  
## <a name="ordering-nested-queries"></a>Řazení vnořených dotazů  
 V Entity Framework vnořený výraz může být umístěn kdekoli v dotazu. Vzhledem k tomu, že Entity SQL umožňuje při psaní dotazů značnou flexibilitu, je možné napsat dotaz, který obsahuje řazení vnořených dotazů. Pořadí vnořeného dotazu se ale nezachová.  
  
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
  
## <a name="see-also"></a>Viz také:

- [Přehled Entity SQL](entity-sql-overview.md)
