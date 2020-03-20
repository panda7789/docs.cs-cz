---
title: ISNULL (Entita SQL)
ms.date: 03/30/2017
ms.assetid: dc7a0173-3664-4c90-a57b-5cbb0a8ed7ee
ms.openlocfilehash: b3fc2484e80b637ed5841375985f7bae476bbbf7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150197"
---
# <a name="isnull-entity-sql"></a>ISNULL (Entita SQL)
Určuje, zda je výraz dotazu null.  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
expression IS [ NOT ] NULL  
```  
  
## <a name="arguments"></a>Argumenty  
 `expression`  
 Libovolný platný výraz dotazu. Nemůže být kolekce, mají členy kolekce nebo typ záznamu s vlastnostmi typu kolekce.  
  
 NOT  
 Neguje EDM. Logický výsledek hodnoty IS NULL.  
  
## <a name="return-value"></a>Návratová hodnota  
 `true`pokud `expression` vrátí hodnotu null; v `false`opačném případě .  
  
## <a name="remarks"></a>Poznámky  
 Slouží `IS NULL` k určení, zda je prvek vnějšího spojení null:  
  
```sql  
select c
      from LOB.Customers as c left outer join LOB.Orders as o
                              on c.ID = o.CustomerID
      where o is not null and o.OrderQuantity = @x  
```  
  
 Slouží `IS NULL` k určení, zda má člen skutečnou hodnotu:  
  
```sql  
select c from LOB.Customer as c where c.DOB is not null  
```  
  
 V následující tabulce je `IS NULL` uvedeno chování nad některými vzory. Všechny výjimky jsou vyvolány ze strany klienta před zprostředkovatel získá vyvolána:  
  
|Vzor|Chování|  
|-------------|--------------|  
|null je null|Vrací objekt `true`.|  
|TREAT (null AS EntityType) JE NULL|Vrací objekt `true`.|  
|TREAT (null AS ComplexType) JE NULL|Vyvolá chybu.|  
|TREAT (null AS Type RowType) JE NULL|Vyvolá chybu.|  
|Typ entity IS NULL|Vrátí `true` `false`nebo .|  
|ComplexType IS NULL|Vyvolá chybu.|  
|Typ řádku JE NULL|Vyvolá chybu.|  
  
## <a name="example"></a>Příklad  
 Následující [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dotaz používá operátor IS NOT NULL k určení, zda výraz dotazu není null. Dotaz je založen na adventureworks prodejní model. Chcete-li tento dotaz zkompilovat a spustit, postupujte takto:  
  
1. Postupujte podle postupu v [části Postup: Spusťte dotaz, který vrací výsledky typu StructuralType](../how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Předat následující dotaz jako argument `ExecuteStructuralTypeQuery` metodě:  
  
 [!code-sql[DP EntityServices Concepts#ISNULL](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#isnull)]  
  
## <a name="see-also"></a>Viz také

- [Reference k Entity SQL](entity-sql-reference.md)
