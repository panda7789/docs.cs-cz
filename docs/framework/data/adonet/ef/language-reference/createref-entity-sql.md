---
title: CREATEREF (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 489828cf-a335-4449-9360-b0d92eec5481
ms.openlocfilehash: 3659f2c0690b00e728630c6e77308ba9d424bb1b
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833924"
---
# <a name="createref-entity-sql"></a>CREATEREF (Entity SQL)
Naprefabrikované odkazy na entitu v objektu EntitySet.  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
CreateRef(entityset_identifier, row_typed_expression)  
```  
  
## <a name="arguments"></a>Arguments  
 `entityset_identifier`  
 Identifikátor EntitySet, nikoli řetězcový literál.  
  
 `row_typed_expression`  
 Výraz typu řádek, který odpovídá klíčovým vlastnostem typu entity.  
  
## <a name="remarks"></a>Poznámky  
 `row_typed_expression` musí být strukturálně ekvivalentní typu klíče pro entitu. To znamená, že musí mít stejný počet a typy polí ve stejném pořadí jako klíče entit.  
  
 V následujícím příkladu jsou Orders a BadOrders oba objekty EntitySet typu Order a ID se považuje za klíčovou vlastnost Order. Příklad ukazuje, jak můžeme vytvořit odkaz na entitu v BadOrders. Všimněte si, že odkaz může být dangling.  To znamená, že odkaz nemusí skutečně identifikovat konkrétní entitu. V těchto případech operace `DEREF` na tomto odkazu vrátí hodnotu null.  
  
```sql  
SELECT CreateRef(LOB.BadOrders, row(o.Id))
FROM LOB.Orders AS o
```  
  
## <a name="example"></a>Příklad  
 Následující Entity SQL dotaz používá operátor CREATEREF k vytvoření odkazu na entitu v sadě entit. Dotaz je založen na modelu prodeje společnosti AdventureWorks. Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:  
  
1. Použijte postup v tématu [Postup: provedení dotazu, který vrátí výsledky StructuralType](../how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Předat následující dotaz jako argument metodě `ExecuteStructuralTypeQuery`:  
  
 [!code-sql[DP EntityServices Concepts#CREATEREF](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#createref)]  
  
## <a name="see-also"></a>Viz také:

- [Reference k Entity SQL](entity-sql-reference.md)
- [DEREF](deref-entity-sql.md)
- [KEY](key-entity-sql.md)
- [REF](ref-entity-sql.md)
