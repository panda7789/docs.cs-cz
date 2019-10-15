---
title: KEY (Entity SQL)
ms.date: 03/30/2017
ms.assetid: cbaa97a8-c89c-4460-8c74-00474695789f
ms.openlocfilehash: 14c0b5d273b26c71c9c63e8bbbcef863ac95a5f3
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319704"
---
# <a name="key-entity-sql"></a>KEY (Entity SQL)
Extrahuje klíč odkazu nebo výrazu entity.  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
KEY(createref_expression)  
```  
  
## <a name="remarks"></a>Poznámky  
 Klíč entity obsahuje hodnoty klíče ve správném pořadí v zadané entitě nebo odkazu na entitu. Vzhledem k tomu, že více sad entit může být založené na stejném typu, může se stejný klíč objevit v každé sadě entit. Chcete-li získat jedinečný odkaz, použijte `REF`. Návratový typ operátoru KEY je typ řádku, který obsahuje jedno pole pro každý klíč entity, ve stejném pořadí.  
  
 V následujícím příkladu je operátor Key předán odkaz na entitu BadOrder a vrátí klíčovou část tohoto odkazu. V takovém případě typ záznamu s přesně jedním polem, který odpovídá vlastnosti `Id`.  
  
```sql  
select Key( CreateRef(LOB.BadOrders, row(o.Id)) )   
from LOB.Orders as o  
```  
  
## <a name="example"></a>Příklad  
 Následující Entity SQL dotaz pomocí operátoru KEY extrahuje klíčovou část výrazu s odkazem na typ. Dotaz je založen na modelu prodeje společnosti AdventureWorks. Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:  
  
1. Použijte postup v tématu [Postup: provedení dotazu, který vrátí výsledky StructuralType](../how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Předat následující dotaz jako argument metodě `ExecuteStructuralTypeQuery`:  
  
 [!code-sql[DP EntityServices Concepts#KEY](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#key)]  
  
## <a name="see-also"></a>Viz také:

- [Reference k Entity SQL](entity-sql-reference.md)
- [CREATEREF](createref-entity-sql.md)
- [REF](ref-entity-sql.md)
- [DEREF](deref-entity-sql.md)
