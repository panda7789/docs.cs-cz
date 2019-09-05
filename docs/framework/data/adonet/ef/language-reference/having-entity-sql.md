---
title: MÁ (Entity SQL)
ms.date: 03/30/2017
ms.assetid: b5d52d97-8372-4335-beac-2d0b79dc3707
ms.openlocfilehash: fe8a177b83932c1c7607f8444c05292c0ee29684
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250852"
---
# <a name="having-entity-sql"></a>MÁ (Entity SQL)
Určuje podmínku vyhledávání pro skupinu nebo agregaci.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[ HAVING search_condition ]  
```  
  
## <a name="arguments"></a>Arguments  
 `search_condition`  
 Určuje podmínku vyhledávání pro skupinu nebo agregaci, která má být splněna. Pokud se používá s klauzulí GROUP BY ALL, klauzule HAVING přepíše vše.  
  
## <a name="remarks"></a>Poznámky  
 Klauzule HAVING se používá k určení dodatečné podmínky filtrování na výsledku seskupení. Není-li ve výrazu dotazu zadána klauzule GROUP BY, je použita implicitní skupina s jedním množinou.  
  
> [!NOTE]
> Se dá použít jenom s příkazem [Select](select-entity-sql.md) . Pokud se nepoužije [Group by](group-by-entity-sql.md) , chová se jako klauzule WHERE.  
  
 Klauzule HAVING funguje podobně jako klauzule WHERE s tím rozdílem, že se používá po operaci GROUP BY. To znamená, že klauzule HAVING může vytvořit pouze odkazy na aliasy seskupení a agregace, jak je znázorněno v následujícím příkladu.  
  
```  
SELECT Name, SUM(o.Price * o.Quantity) AS Total FROM orderLines AS o GROUP BY o.Product AS Name  
HAVING SUM(o.Quantity) > 1  
```  
  
 Předchozí omezí skupiny jenom na ty, které obsahují víc než jeden produkt.  
  
## <a name="example"></a>Příklad  
 Následující Entity SQL dotaz používá operátory HAVING a GROUP BY k určení podmínky vyhledávání pro skupinu nebo agregaci. Dotaz je založen na modelu prodeje společnosti AdventureWorks. Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:  
  
1. Postupujte podle pokynů v [tématu Postupy: Spustí dotaz, který vrátí výsledky](../how-to-execute-a-query-that-returns-primitivetype-results.md)PrimitiveType.  
  
2. Předat následující dotaz jako argument `ExecutePrimitiveTypeQuery` metodě:  
  
 [!code-csharp[DP EntityServices Concepts 2#HAVING](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#having)]  
  
## <a name="see-also"></a>Viz také:

- [Reference k Entity SQL](entity-sql-reference.md)
- [Výrazy dotazu](query-expressions-entity-sql.md)
