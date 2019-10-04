---
title: MÁ (Entity SQL)
ms.date: 03/30/2017
ms.assetid: b5d52d97-8372-4335-beac-2d0b79dc3707
ms.openlocfilehash: 97ed6e06241804bf2f576c910a2235b0cb570bbb
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833734"
---
# <a name="having-entity-sql"></a>MÁ (Entity SQL)
Určuje podmínku vyhledávání pro skupinu nebo agregaci.  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
[ HAVING search_condition ]  
```  
  
## <a name="arguments"></a>Arguments  
 `search_condition`  
 Určuje podmínku vyhledávání pro skupinu nebo agregaci, která má být splněna. Pokud se používá s klauzulí GROUP BY ALL, klauzule HAVING přepíše vše.  
  
## <a name="remarks"></a>Poznámky  
 Klauzule HAVING se používá k určení dodatečné podmínky filtrování na výsledku seskupení. Není-li ve výrazu dotazu zadána klauzule GROUP BY, je použita implicitní skupina s jedním množinou.  
  
> [!NOTE]
> Se dá použít jenom s příkazem [Select](select-entity-sql.md) . Pokud se nepoužije [Group by](group-by-entity-sql.md) , chová se jako klauzule WHERE.  
  
Klauzule HAVING funguje podobně jako klauzule WHERE s tím rozdílem, že se používá po operaci GROUP BY. To znamená, že klauzule HAVING může vytvořit pouze odkazy na aliasy seskupení a agregace, jak je znázorněno v následujícím příkladu:
  
```sql  
SELECT Name, SUM(o.Price * o.Quantity) AS Total FROM orderLines AS o GROUP BY o.Product AS Name  
HAVING SUM(o.Quantity) > 1  
```  
  
 Předchozí omezí skupiny jenom na ty, které obsahují víc než jeden produkt.  
  
## <a name="example"></a>Příklad  
 Následující Entity SQL dotaz používá operátory HAVING a GROUP BY k určení podmínky vyhledávání pro skupinu nebo agregaci. Dotaz je založen na modelu prodeje společnosti AdventureWorks. Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:  
  
1. Použijte postup v tématu [Postup: provedení dotazu, který vrátí výsledky PrimitiveType](../how-to-execute-a-query-that-returns-primitivetype-results.md).  
  
2. Předat následující dotaz jako argument metodě `ExecutePrimitiveTypeQuery`:  
  
 [!code-sql[DP EntityServices Concepts#HAVING](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#having)]  
  
## <a name="see-also"></a>Viz také:

- [Reference k Entity SQL](entity-sql-reference.md)
- [Výrazy dotazu](query-expressions-entity-sql.md)
