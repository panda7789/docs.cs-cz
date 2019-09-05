---
title: ISNULL (Entity SQL)
ms.date: 03/30/2017
ms.assetid: dc7a0173-3664-4c90-a57b-5cbb0a8ed7ee
ms.openlocfilehash: d54c350196ad1ef7cfafa6d931d9d1ad8f267177
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250561"
---
# <a name="isnull-entity-sql"></a>ISNULL (Entity SQL)
Určuje, zda má výraz dotazu hodnotu null.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
expression IS [ NOT ] NULL  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Libovolný platný výraz dotazu. Nelze vytvořit kolekci, mít členy kolekce nebo typ záznamu s vlastnostmi typu kolekce.  
  
 NOT  
 Negace datového modelu EDM. Logický výsledek hodnoty je NULL.  
  
## <a name="return-value"></a>Návratová hodnota  
 `true`Pokud `expression` vrátí hodnotu null, `false`v opačném případě.  
  
## <a name="remarks"></a>Poznámky  
 Použijte `IS NULL` k určení, zda je prvek vnějšího spojení null:  
  
```  
select c   
      from LOB.Customers as c left outer join LOB.Orders as o   
                              on c.ID = o.CustomerID    
      where o is not null and o.OrderQuantity = @x  
```  
  
 Použijte `IS NULL` k určení, zda má člen skutečnou hodnotu:  
  
```  
select c from LOB.Customer as c where c.DOB is not null  
```  
  
 Následující tabulka ukazuje chování `IS NULL` nad některými vzory. Všechny výjimky jsou vyvolány na straně klienta před vyvoláním zprostředkovatele:  
  
|Vzor|Chování|  
|-------------|--------------|  
|hodnota null je NULL.|Vrátí `true`.|  
|ZPRACOVÁVÁ se (hodnota null jako EntityType) má hodnotu NULL.|Vrátí `true`.|  
|Považovat za (null jako ComplexType) je NULL.|Vyvolá chybu.|  
|ZPRACOVÁVÁ se (hodnota null jako RowType) je NULL.|Vyvolá chybu.|  
|EntityType má hodnotu NULL.|Vrátí `true` nebo `false`.|  
|Typ ComplexType má hodnotu NULL.|Vyvolá chybu.|  
|RowType má hodnotu NULL.|Vyvolá chybu.|  
  
## <a name="example"></a>Příklad  
 Následující [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dotaz používá operátor is not null k určení, zda výraz dotazu není null. Dotaz je založen na modelu prodeje společnosti AdventureWorks. Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:  
  
1. Postupujte podle pokynů v [tématu Postupy: Spustí dotaz, který vrátí výsledky](../how-to-execute-a-query-that-returns-structuraltype-results.md)StructuralType.  
  
2. Předat následující dotaz jako argument `ExecuteStructuralTypeQuery` metodě:  
  
 [!code-csharp[DP EntityServices Concepts 2#ISNULL](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#isnull)]  
  
## <a name="see-also"></a>Viz také:

- [Reference k Entity SQL](entity-sql-reference.md)
