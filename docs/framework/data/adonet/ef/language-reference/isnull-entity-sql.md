---
title: ISNULL (Entity SQL)
ms.date: 03/30/2017
ms.assetid: dc7a0173-3664-4c90-a57b-5cbb0a8ed7ee
ms.openlocfilehash: 1b728e170968e2fbeb67eef3f8f940c64816ff0d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54528729"
---
# <a name="isnull-entity-sql"></a>ISNULL (Entity SQL)
Určuje, zda výraz dotazu je null.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
expression IS [ NOT ] NULL  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Libovolný výraz platný dotaz. Nemůže být kolekce, mají členy kolekce, nebo typ záznamu se shromažďováním dat pro vlastnosti typu.  
  
 NOT  
 Neguje modelu EDM. Výsledek logickou hodnotu je null.  
  
## <a name="return-value"></a>Návratová hodnota  
 `true` Pokud `expression` vrátí hodnotu null; v opačném případě `false`.  
  
## <a name="remarks"></a>Poznámky  
 Použití `IS NULL` k určení, zda elementu vnější spojení je null:  
  
```  
select c   
      from LOB.Customers as c left outer join LOB.Orders as o   
                              on c.ID = o.CustomerID    
      where o is not null and o.OrderQuantity = @x  
```  
  
 Použití `IS NULL` k určení, zda člen má skutečná hodnota:  
  
```  
select c from LOB.Customer as c where c.DOB is not null  
```  
  
 V následující tabulce jsou uvedeny chování `IS NULL` přes některé vzory. Všechny výjimky jsou vyvolány ze strany klienta předtím, než je volán za zprostředkovatele:  
  
|Vzor|Chování|  
|-------------|--------------|  
|NULL je NULL|Vrátí `true`.|  
|POVAŽOVAT (třída EntityType hodnotu null jako) je NULL|Vrátí `true`.|  
|POVAŽOVAT (null jako ComplexType) je NULL|Vyvolá chybu.|  
|POVAŽOVAT (null jako RowType) je NULL|Vyvolá chybu.|  
|Typ EntityType má hodnotu NULL.|Vrátí `true` nebo `false`.|  
|Typ ComplexType má hodnotu NULL.|Vyvolá chybu.|  
|RowType má hodnotu NULL.|Vyvolá chybu.|  
  
## <a name="example"></a>Příklad  
 Následující [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dotazu operátor IS NOT NULL, který se používá k určení, pokud výraz dotazu není null. Dotaz je založen na modelu Sales AdventureWorks. Kompilace a spuštění tohoto dotazu, postupujte podle těchto kroků:  
  
1.  Postupujte podle pokynů v [jak: Spustit dotaz, který vrátí výsledky typu StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#ISNULL](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#isnull)]  
  
## <a name="see-also"></a>Viz také:
- [Reference k Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
