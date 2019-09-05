---
title: KEY (Entity SQL)
ms.date: 03/30/2017
ms.assetid: cbaa97a8-c89c-4460-8c74-00474695789f
ms.openlocfilehash: 44ab5352c3b2a94cb210c3de775d2347d2df7fe7
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250487"
---
# <a name="key-entity-sql"></a>KEY (Entity SQL)
Extrahuje klíč odkazu nebo výrazu entity.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
KEY(createref_expression)  
```  
  
## <a name="remarks"></a>Poznámky  
 Klíč entity obsahuje hodnoty klíče ve správném pořadí v zadané entitě nebo odkazu na entitu. Vzhledem k tomu, že více sad entit může být založené na stejném typu, může se stejný klíč objevit v každé sadě entit. Chcete-li získat jedinečný odkaz, `REF`použijte. Návratový typ operátoru KEY je typ řádku, který obsahuje jedno pole pro každý klíč entity, ve stejném pořadí.  
  
 V následujícím příkladu je operátor Key předán odkaz na entitu BadOrder a vrátí klíčovou část tohoto odkazu. V takovém případě typ záznamu s přesně jedním polem odpovídajícím `Id` vlastnosti.  
  
```  
select Key( CreateRef(LOB.BadOrders, row(o.Id)) )   
from LOB.Orders as o  
```  
  
## <a name="example"></a>Příklad  
 Následující Entity SQL dotaz pomocí operátoru KEY extrahuje klíčovou část výrazu s odkazem na typ. Dotaz je založen na modelu prodeje společnosti AdventureWorks. Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:  
  
1. Postupujte podle pokynů v [tématu Postupy: Spustí dotaz, který vrátí výsledky](../how-to-execute-a-query-that-returns-structuraltype-results.md)StructuralType.  
  
2. Předat následující dotaz jako argument `ExecuteStructuralTypeQuery` metodě:  
  
 [!code-csharp[DP EntityServices Concepts 2#KEY](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#key)]  
  
## <a name="see-also"></a>Viz také:

- [Reference k Entity SQL](entity-sql-reference.md)
- [CREATEREF](createref-entity-sql.md)
- [REF](ref-entity-sql.md)
- [DEREF](deref-entity-sql.md)
