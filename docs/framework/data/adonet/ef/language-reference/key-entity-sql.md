---
title: KLÍČ (Entity SQL)
ms.date: 03/30/2017
ms.assetid: cbaa97a8-c89c-4460-8c74-00474695789f
ms.openlocfilehash: 9cd3276583741f2b0261cb8a0e55f4185d20100e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59319336"
---
# <a name="key-entity-sql"></a>KLÍČ (Entity SQL)
Extrahuje klíč odkazu nebo výrazu entity.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
KEY(createref_expression)  
```  
  
## <a name="remarks"></a>Poznámky  
 Klíč entity obsahuje hodnoty klíče ve správném pořadí zadané entity nebo odkaz na entitu. Protože více sad entit může být založen na stejný typ, stejný klíč se může zobrazit v každé sadě entit. Chcete-li získat jedinečný odkaz, použijte `REF`. Návratový typ operátoru klíč je typ řádku, který obsahuje jedno pole pro každý klíč entity, ve stejném pořadí.  
  
 V následujícím příkladu operátor klíčů je předán odkaz na entitu BadOrder a vrátí část klíče tohoto odkazu. V takovém případě se přesně jeden pole odpovídající typ záznamu `Id` vlastnost.  
  
```  
select Key( CreateRef(LOB.BadOrders, row(o.Id)) )   
from LOB.Orders as o  
```  
  
## <a name="example"></a>Příklad  
 Následující dotaz Entity SQL používá operátor klíče k extrakci část výraz s odkaz na typ klíče. Dotaz je založen na modelu Sales AdventureWorks. Kompilace a spuštění tohoto dotazu, postupujte podle těchto kroků:  
  
1. Postupujte podle pokynů v [jak: Spustit dotaz, který vrátí výsledky typu StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#KEY](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#key)]  
  
## <a name="see-also"></a>Viz také:

- [Reference k Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [CREATEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md)
- [REF](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md)
- [DEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md)
