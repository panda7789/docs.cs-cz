---
title: GROUPPARTITION (Entity SQL)
ms.date: 03/30/2017
ms.assetid: d0482e9b-086c-451c-9dfa-ccb024a9efb6
ms.openlocfilehash: 19df566c254a3f3202eb3554ab43ee0d7c944181
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833754"
---
# <a name="grouppartition-entity-sql"></a>GROUPPARTITION (Entity SQL)
Vrátí kolekci hodnot argumentů, které jsou proložené z aktuálního oddílu skupiny, ke kterému se agregace vztahuje. Agregace `GroupPartition` je agregovaná podle skupin a nemá žádný formulář založený na kolekcích.  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
GROUPPARTITION( [ALL|DISTINCT] expression )  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Libovolný výraz [!INCLUDE[esql](../../../../../../includes/esql-md.md)].  
  
## <a name="remarks"></a>Poznámky  
 Následující dotaz vytvoří seznam produktů a kolekci množství řádků objednávky na jednotlivé produkty:  
  
```sql  
SELECT p, GroupPartition(ol.Quantity) FROM LOB.OrderLines AS ol
  GROUP BY ol.Product AS p
```  
  
 Následující dva dotazy jsou sémanticky stejné:  
  
```sql  
SELECT p, Sum(GroupPartition(ol.Quantity)) FROM LOB.OrderLines AS ol
  GROUP BY ol.Product AS p
SELET p, Sum(ol.Quantity) FROM LOB.OrderLines AS ol
  group by ol.Product as p  
```  
  
 Operátor `GROUPPARTITION` lze použít ve spojení s uživatelsky definovanými agregačními funkcemi.  
  
`GROUPPARTITION` je speciální agregační operátor, který obsahuje odkaz na seskupenou vstupní sadu. Tento odkaz lze použít kdekoli v dotazu, kde GROUP BY je v oboru. Příklad:
  
```sql  
SELECT p, GroupPartition(ol.Quantity) FROM LOB.OrderLines AS ol GROUP BY ol.Product AS p
```  
  
 Při běžném `GROUP BY` jsou výsledky seskupení skryté. Výsledky můžete použít jenom v agregační funkci. Chcete-li zobrazit výsledky seskupení, je třeba sladit výsledky seskupení a vstupní sady pomocí poddotazu. Následující dva dotazy jsou ekvivalentní:  
  
```sql  
SELET p, (SELECT q FROM GroupPartition(ol.Quantity) AS q) FROM LOB.OrderLines AS ol GROUP BY ol.Product AS p
SELECT p, (SELECT ol.Quantity AS q FROM LOB.OrderLines AS ol2 WHERE ol2.Product = p) FROM LOB.OrderLines AS ol GROUP BY ol.Product AS p
```  
  
 Jak je vidět v příkladu, agregační operátor GROUPPARTITION usnadňuje získání odkazu na vstupní sadu po seskupení.  
  
 Operátor GROUPPARTITION může při použití parametru `expression` zadat libovolný výraz [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ve vstupu operátoru.  
  
 Například všechny následující vstupní výrazy pro oddíl skupiny jsou platné:  
  
```sql  
SELECT groupkey, GroupPartition(b) FROM {1,2,3} AS a INNER JOIN {4,5,6} AS b ON true GROUP BY a AS groupkey
SELECT groupkey, GroupPartition(1) FROM {1,2,3} AS a INNER JOIN {4,5,6} AS b ON true GROUP BY a AS groupkey
SELECT groupkey, GroupPartition(a + b) FROM {1,2,3} AS a INNER JOIN {4,5,6} AS b ON true GROUP BY a AS groupkey
SELECT groupkey, GroupPartition({a + b}) FROM {1,2,3} AS a INNER JOIN {4,5,6} AS b ON true GROUP BY a AS groupkey  
SELECT groupkey, GroupPartition({42}) FROM {1,2,3} AS a INNER JOIN {4,5,6} AS b ON true GROUP BY a AS groupkey  
SELECT groupkey, GroupPartition(b > a) FROM {1,2,3} AS a INNER JOIN {4,5,6} AS b ON true GROUP BY a AS groupkey  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak použít klauzuli GROUPPARTITION s klauzulí GROUP BY. Skupiny klauzule GROUP BY @no__t entit-0 podle jejich `Contact`. Klauzule GROUPPARTITION @no__t pak vyhledá vlastnost-0 pro každou skupinu a výsledkem je kolekce desetinných míst.  
  
 [!code-sql[DP EntityServices Concepts#Collection_GroupPartition](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#collection_grouppartition)]
