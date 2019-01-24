---
title: KLÍČ (Entity SQL)
ms.date: 03/30/2017
ms.assetid: cbaa97a8-c89c-4460-8c74-00474695789f
ms.openlocfilehash: 68ee7d512e0a3b5d912dc12c55be6f0135129225
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54509195"
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
  
1.  Postupujte podle pokynů v [jak: Spustit dotaz, který vrátí výsledky typu StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#KEY](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#key)]  
  
## <a name="see-also"></a>Viz také:
- [Reference k Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [CREATEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md)
- [REF](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md)
- [DEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md)
