---
title: "MULTIMNOŽINA (entita SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eb90a377-e47a-43a5-b308-e993b6d611e6
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 2dff0e0ac2d9d0e705cdd6eedcf32f7919164b89
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="multiset-entity-sql"></a>MULTIMNOŽINA (entita SQL)
Vytvoří instanci multimnožina ze seznamu hodnot. Všechny hodnoty ve MULTISET konstruktor musí být kompatibilní typu `T`. Prázdný multiset konstruktory nejsou povoleny.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
MULTISET ( expression [{, expression }] )  
or  
{ expression [{, expression }] }  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Žádný platný seznam hodnot.  
  
## <a name="return-value"></a>Návratová hodnota  
 Kolekci typu MULTIMNOŽINA\<T >.  
  
## <a name="remarks"></a>Poznámky  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]poskytuje tři druhy konstruktory: řádek konstruktory, objekt konstruktorů a konstruktorů multiset (nebo kolekce). Další informace najdete v tématu [vytváření typů](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md).  
  
 Multimnožinové konstruktoru vytvoří instanci multimnožina ze seznamu hodnot. Všechny hodnoty v konstruktoru musí být kompatibilní.  
  
 Například následující výraz vytvoří multimnožina celých čísel.  
  
 `MULTISET(1, 2, 3)`  
  
 `{1, 2, 3}`  
  
> [!NOTE]
>  Vnořené multiset literály jsou podporována pouze v případě mutiset zabalení má jeden prvek multiset; například `{{1, 2, 3}}`. Když multimnožina zabalení má více elementů multiset (například `{{1, 2}, {3, 4}}`), nejsou podporovány literály vnořené multiset.  
  
## <a name="example"></a>Příklad  
 Následující dotaz Entity SQL pomocí operátoru MULTIMNOŽINA vytvořit instanci multimnožina ze seznamu hodnot. Dotaz je založen na modelu prodej AdventureWorks. Pro zkompilování a spuštění tohoto dotazu, postupujte takto:  
  
1.  Postupujte podle pokynů v [postup: provedení dotazu tohoto vrátí výsledky StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metoda:  
  
 [!code-csharp[DP EntityServices Concepts 2#MULTISET](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#multiset)]  
  
## <a name="see-also"></a>Viz také  
 [Vytváření typů](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md)  
 [Reference k Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
