---
title: GROUPPARTITION (Entity SQL)
ms.date: 03/30/2017
ms.assetid: d0482e9b-086c-451c-9dfa-ccb024a9efb6
ms.openlocfilehash: 9f0f917380e6422da753282216529580f87f1a1a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774722"
---
# <a name="grouppartition-entity-sql"></a>GROUPPARTITION (Entity SQL)
Vrátí kolekci hodnot argumentů, které se vykreslují mimo aktuální skupiny oddílů, ke kterému se vztahuje agregace. `GroupPartition` Agregace je agregovat na základě skupiny a nemá žádný formulář na základě kolekce.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
GROUPPARTITION( [ALL|DISTINCT] expression )  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Žádné [!INCLUDE[esql](../../../../../../includes/esql-md.md)] výrazu.  
  
## <a name="remarks"></a>Poznámky  
 Následující dotaz vytvoří seznam produktů a kolekce řádek množství objednávek za jednotlivé produkty:  
  
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
  
 `GROUPPARTITION` Operátor můžete použít ve spojení s uživatelsky definované agregační funkce.  
  
 `GROUPPARTITION` je speciální agregační operátor, který obsahuje odkaz na seskupené vstupní sady. Tento odkaz můžete je použít kdekoli v dotazu kde GROUP BY je v oboru. Například  
  
```  
select p, GroupPartition(ol.Quantity) from LOB.OrderLines as ol group by ol.Product as p  
```  
  
 Pomocí regulárních KLAUZULE GROUP jsou skryté výsledky seskupení. Výsledky můžete použít pouze v agregační funkci. Chcete-li zobrazit výsledky seskupení, budete muset můžete provádět korelaci výsledků seskupení a vstupní nastavení s použitím poddotaz. Následující dva dotazy jsou ekvivalentní:  
  
```  
select p, (select q from GroupPartition(ol.Quantity) as q) from LOB.OrderLines as ol group by ol.Product as p  
select p, (select ol.Quantity as q from LOB.OrderLines as ol2 where ol2.Product = p) from LOB.OrderLines as ol group by ol.Product as p  
```  
  
 Jak je vidět z příkladu, agregační operátor GROUPPARTITION je snazší získat odkaz na sadu po seskupení vstupů.  
  
 Operátor GROUPPARTITION můžete určit kterékoli [!INCLUDE[esql](../../../../../../includes/esql-md.md)] výraz v operátoru vstup při použití `expression` parametru.  
  
 Například všechny následující vstupní výrazy do oddílu skupiny jsou platné:  
  
```  
select groupkey, GroupPartition(b) from {1,2,3} as a inner join {4,5,6} as b on true group by a as groupkey  
select groupkey, GroupPartition(1) from {1,2,3} as a inner join {4,5,6} as b on true group by a as groupkey  
select groupkey, GroupPartition(a + b) from {1,2,3} as a inner join {4,5,6} as b on true group by a as groupkey  
select groupkey, GroupPartition({a + b}) from {1,2,3} as a inner join {4,5,6} as b on true group by a as groupkey  
select groupkey, GroupPartition({42}) from {1,2,3} as a inner join {4,5,6} as b on true group by a as groupkey  
select groupkey, GroupPartition(b > a) from {1,2,3} as a inner join {4,5,6} as b on true group by a as groupkey  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje způsob použití klauzule GROUPPARTITION s klauzulí GROUP BY. Skupiny klauzule GROUP BY `SalesOrderHeader` entity podle jejich `Contact`. Klauzule GROUPPARTITION pak projektů `TotalDue` vlastností pro každou skupinu, výsledkem je kolekce desetinná čísla.  
  
 [!code-csharp[DP EntityServices Concepts 2#Collection_GroupPartition](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#collection_grouppartition)]
