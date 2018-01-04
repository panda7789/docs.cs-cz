---
title: "KLÍČ (entita SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cbaa97a8-c89c-4460-8c74-00474695789f
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 3be9c51e48e21d76c4425401000cbfdd55f5f538
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="key-entity-sql"></a>KLÍČ (entita SQL)
Extrahuje klíč odkaz nebo výraz entity.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
KEY(createref_expression)  
```  
  
## <a name="remarks"></a>Poznámky  
 Klíč entity obsahuje hodnoty klíče ve správném pořadí zadané entity nebo odkaz na entitu. Protože několik sad entit může být založen na stejného typu, může vypadat stejným klíčem v každé sadě entit. Chcete-li získat jedinečný odkaz, použijte `REF`. Návratový typ operátor klíč je typ řádek, který obsahuje jedno pole pro každý klíč entity, ve stejném pořadí.  
  
 V následujícím příkladu se klíče operátor je předán odkaz na entitu BadOrder a vrátí část klíče tento odkaz. V takovém případě s přesně jeden pole odpovídající typ záznamu `Id` vlastnost.  
  
```  
select Key( CreateRef(LOB.BadOrders, row(o.Id)) )   
from LOB.Orders as o  
```  
  
## <a name="example"></a>Příklad  
 Následující dotaz Entity SQL pomocí operátoru klíč k extrakci část výraz obsahující odkaz na typ klíče. Dotaz je založen na modelu prodej AdventureWorks. Pro zkompilování a spuštění tohoto dotazu, postupujte takto:  
  
1.  Postupujte podle pokynů v [postup: provedení dotazu tohoto vrátí výsledky StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metoda:  
  
 [!code-csharp[DP EntityServices Concepts 2#KEY](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#key)]  
  
## <a name="see-also"></a>Viz také  
 [Reference k Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [CREATEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md)  
 [REF](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md)  
 [DEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md)
