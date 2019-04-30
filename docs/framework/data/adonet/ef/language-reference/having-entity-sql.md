---
title: S (Entity SQL)
ms.date: 03/30/2017
ms.assetid: b5d52d97-8372-4335-beac-2d0b79dc3707
ms.openlocfilehash: 7b147a84a43677afa53f7872f8042f1cf44137cf
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774709"
---
# <a name="having-entity-sql"></a>S (Entity SQL)
Určuje podmínku hledání pro skupinu nebo agregace.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[ HAVING search_condition ]  
```  
  
## <a name="arguments"></a>Arguments  
 `search_condition`  
 Určuje pro skupinu nebo agregace pro splnění podmínky vyhledávání. Při použití s s GROUP BY ALL v klauzuli HAVING přepíše všechny.  
  
## <a name="remarks"></a>Poznámky  
 V klauzuli HAVING slouží k určení dalších podmínku filtrování pro výsledek seskupení. Klauzule GROUP BY je zadaný ve výrazu dotazu, předpokládá se implicitní skupina jedné sady.  
  
> [!NOTE]
>  HAVING jde použít jenom s [vyberte](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md) příkazu. Když [Group](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md) se nepoužívá, HAVING se chová jako klauzuli WHERE.  
  
 V klauzuli HAVING funguje jako klauzuli WHERE, s tím rozdílem, že se použije po provedení této operace GROUP BY. To znamená, že v klauzuli HAVING lze vytvořit pouze odkazy na seskupení aliasů a agregace, jak je znázorněno v následujícím příkladu.  
  
```  
SELECT Name, SUM(o.Price * o.Quantity) AS Total FROM orderLines AS o GROUP BY o.Product AS Name  
HAVING SUM(o.Quantity) > 1  
```  
  
 Předchozí skupiny omezuje jenom na ty, které obsahují více než jeden produkt.  
  
## <a name="example"></a>Příklad  
 Následující dotaz Entity SQL používá operátory HAVING a GROUP BY k zadání podmínek vyhledávání pro skupinu nebo agregace. Dotaz je založen na modelu Sales AdventureWorks. Kompilace a spuštění tohoto dotazu, postupujte podle těchto kroků:  
  
1. Postupujte podle pokynů v [jak: Spustit dotaz, který vrátí výsledky typu PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).  
  
2. Předat jako argument pro následující dotaz `ExecutePrimitiveTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#HAVING](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#having)]  
  
## <a name="see-also"></a>Viz také:

- [Reference k Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [Výrazy dotazu](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)
