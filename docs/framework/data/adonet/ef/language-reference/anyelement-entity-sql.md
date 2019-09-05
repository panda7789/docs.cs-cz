---
title: ANYELEMENT (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 475a9ad6-8c8d-4f49-9970-af273e5360f1
ms.openlocfilehash: 4eea3d43ef6ae9ea91432ea277326526e5e91fbc
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251332"
---
# <a name="anyelement-entity-sql"></a>ANYELEMENT (Entity SQL)
Extrahuje prvek z kolekce s více hodnotami.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
ANYELEMENT ( expression )  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Libovolný platný výraz dotazu, který vrací kolekci pro extrakci prvku z.  
  
## <a name="return-value"></a>Návratová hodnota  
 Jeden prvek v kolekci nebo libovolný element, pokud má kolekce více než jeden prvek; Pokud je kolekce prázdná, vrátí `null`. Pokud `collection` je kolekce typu `Collection<T>`, pak `ANYELEMENT(collection)` je platný výraz, který je výsledkem instance typu `T`.  
  
## <a name="remarks"></a>Poznámky  
 ANYELEMENT extrahuje libovolný prvek z kolekce s více hodnotami. Například následující příklad se pokusí extrahovat prvek singleton ze sady `Customers`.  
  
```  
ANYELEMENT(Customers)  
```  
  
## <a name="example"></a>Příklad  
 Následující [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dotaz používá operátor AnyElement k extrakci prvku z kolekce s více hodnotami. Dotaz je založen na modelu prodeje společnosti AdventureWorks. Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:  
  
1. Postupujte podle pokynů v [tématu Postupy: Spustí dotaz, který vrátí výsledky](../how-to-execute-a-query-that-returns-structuraltype-results.md)StructuralType.  
  
2. Předat následující dotaz jako argument `ExecuteStructuralTypeQuery` metodě:  
  
 [!code-csharp[DP EntityServices Concepts 2#ANYELEMENT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#anyelement)]  
  
## <a name="see-also"></a>Viz také:

- [Reference k Entity SQL](entity-sql-reference.md)
- [Strukturované typy s možnou hodnotou Null](nullable-structured-types-entity-sql.md)
