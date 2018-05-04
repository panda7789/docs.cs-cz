---
title: GROUPPARTITION (entita SQL)
ms.date: 03/30/2017
ms.assetid: d0482e9b-086c-451c-9dfa-ccb024a9efb6
ms.openlocfilehash: 9f0f917380e6422da753282216529580f87f1a1a
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="grouppartition-entity-sql"></a>GROUPPARTITION (entita SQL)
Vrátí kolekci argument hodnoty, které jsou k projekci mimo aktuální oddílu skupiny, ke kterému se vztahuje na agregaci. `GroupPartition` Agregace je agregace se na základě skupiny a nemá žádný formulář na základě kolekce.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
GROUPPARTITION( [ALL|DISTINCT] expression )  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Všechny [!INCLUDE[esql](../../../../../../includes/esql-md.md)] výraz.  
  
## <a name="remarks"></a>Poznámky  
 Následující dotaz vytvoří seznam produktů a kolekce pořadí počty řádek pro každý produkt:  
  
```  
select p, GroupPartition(ol.Quantity) from LOB.OrderLines as ol  
  group by ol.Product as p  
```  
  
 Následující dva dotazy jsou sémanticky stejné:  
  
```  
select p, Sum(GroupPartition(ol.Quantity)) from LOB.OrderLines as ol  
  group by ol.Product as p  
select p, Sum(ol.Quantity) from LOB.OrderLines as ol  
  group by ol.Product as p  
```  
  
 `GROUPPARTITION` Operátor můžete použít ve spojení s uživatelem definované agregační funkce.  
  
 `GROUPPARTITION` je speciální agregační operátor, který obsahuje odkaz na sadu seskupené vstupní. Tento odkaz lze použít kdekoli v dotazu kde GROUP BY je v oboru. Například  
  
```  
select p, GroupPartition(ol.Quantity) from LOB.OrderLines as ol group by ol.Product as p  
```  
  
 S klauzulí regulární GROUP BY jsou výsledky seskupení skryté. Výsledky můžete použít pouze v agregační funkci. Chcete-li zobrazit výsledky seskupení, budete muset korelovat výsledky seskupení a vstup nastavit pomocí poddotazu. Následující dva dotazy jsou ekvivalentní:  
  
```  
select p, (select q from GroupPartition(ol.Quantity) as q) from LOB.OrderLines as ol group by ol.Product as p  
select p, (select ol.Quantity as q from LOB.OrderLines as ol2 where ol2.Product = p) from LOB.OrderLines as ol group by ol.Product as p  
```  
  
 Jak je vidět z příkladu, agregační operátor GROUPPARTITION je snazší získat odkaz na vstup nastaví po seskupení.  
  
 Operátor GROUPPARTITION můžete zadat jakýkoli [!INCLUDE[esql](../../../../../../includes/esql-md.md)] výraz v operátoru vstup při použití `expression` parametr.  
  
 Například všechny následující vstupní výrazy k oddílu skupiny jsou platné:  
  
```  
select groupkey, GroupPartition(b) from {1,2,3} as a inner join {4,5,6} as b on true group by a as groupkey  
select groupkey, GroupPartition(1) from {1,2,3} as a inner join {4,5,6} as b on true group by a as groupkey  
select groupkey, GroupPartition(a + b) from {1,2,3} as a inner join {4,5,6} as b on true group by a as groupkey  
select groupkey, GroupPartition({a + b}) from {1,2,3} as a inner join {4,5,6} as b on true group by a as groupkey  
select groupkey, GroupPartition({42}) from {1,2,3} as a inner join {4,5,6} as b on true group by a as groupkey  
select groupkey, GroupPartition(b > a) from {1,2,3} as a inner join {4,5,6} as b on true group by a as groupkey  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak použít klauzuli GROUPPARTITION s klauzulí GROUP BY. Skupiny klauzule GROUP BY `SalesOrderHeader` entity podle jejich `Contact`. Klauzule GROUPPARTITION pak projekty `TotalDue` vlastnosti pro každou skupinu, výsledkem je kolekce desetinných míst.  
  
 [!code-csharp[DP EntityServices Concepts 2#Collection_GroupPartition](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#collection_grouppartition)]
