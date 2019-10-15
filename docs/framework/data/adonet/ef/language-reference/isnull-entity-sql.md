---
title: ISNULL (Entity SQL)
ms.date: 03/30/2017
ms.assetid: dc7a0173-3664-4c90-a57b-5cbb0a8ed7ee
ms.openlocfilehash: 9066f9fb68ce2c50e9523881cfa0dd930cd0b52e
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319735"
---
# <a name="isnull-entity-sql"></a>ISNULL (Entity SQL)
Určuje, zda má výraz dotazu hodnotu null.  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
expression IS [ NOT ] NULL  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Libovolný platný výraz dotazu. Nelze vytvořit kolekci, mít členy kolekce nebo typ záznamu s vlastnostmi typu kolekce.  
  
 MĚNÍ  
 Negace datového modelu EDM. Logický výsledek hodnoty je NULL.  
  
## <a name="return-value"></a>Návratová hodnota  
 `true`, pokud `expression` vrátí hodnotu null; v opačném případě `false`.  
  
## <a name="remarks"></a>Poznámky  
 Chcete-li zjistit, zda je element vnějšího spojení null, použijte `IS NULL`:  
  
```sql  
select c   
      from LOB.Customers as c left outer join LOB.Orders as o   
                              on c.ID = o.CustomerID    
      where o is not null and o.OrderQuantity = @x  
```  
  
 Chcete-li zjistit, zda má člen skutečnou hodnotu, použijte `IS NULL`:  
  
```sql  
select c from LOB.Customer as c where c.DOB is not null  
```  
  
 Následující tabulka ukazuje chování `IS NULL` v některých vzorcích. Všechny výjimky jsou vyvolány na straně klienta před vyvoláním zprostředkovatele:  
  
|Vzor|Předvídatelně|  
|-------------|--------------|  
|hodnota null je NULL.|Vrátí `true`.|  
|ZPRACOVÁVÁ se (hodnota null jako EntityType) má hodnotu NULL.|Vrátí `true`.|  
|Považovat za (null jako ComplexType) je NULL.|Vyvolá chybu.|  
|ZPRACOVÁVÁ se (hodnota null jako RowType) je NULL.|Vyvolá chybu.|  
|EntityType má hodnotu NULL.|Vrátí `true` nebo `false`.|  
|Typ ComplexType má hodnotu NULL.|Vyvolá chybu.|  
|RowType má hodnotu NULL.|Vyvolá chybu.|  
  
## <a name="example"></a>Příklad  
 Následující dotaz [!INCLUDE[esql](../../../../../../includes/esql-md.md)] používá operátor IS NOT NULL k určení, zda výraz dotazu není null. Dotaz je založen na modelu prodeje společnosti AdventureWorks. Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:  
  
1. Použijte postup v tématu [Postup: provedení dotazu, který vrátí výsledky StructuralType](../how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Předat následující dotaz jako argument metodě `ExecuteStructuralTypeQuery`:  
  
 [!code-sql[DP EntityServices Concepts#ISNULL](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#isnull)]  
  
## <a name="see-also"></a>Viz také:

- [Reference k Entity SQL](entity-sql-reference.md)
