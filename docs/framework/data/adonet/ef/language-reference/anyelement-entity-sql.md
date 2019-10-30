---
title: ANYELEMENT (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 475a9ad6-8c8d-4f49-9970-af273e5360f1
ms.openlocfilehash: c0f7686f7ff3f6458637b51e29ecafe0c0ccfbc4
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040323"
---
# <a name="anyelement-entity-sql"></a>ANYELEMENT (Entity SQL)
Extrahuje prvek z kolekce s více hodnotami.  
  
## <a name="syntax"></a>Syntaxe  
  
```csharp
ANYELEMENT ( expression )  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Libovolný platný výraz dotazu, který vrací kolekci pro extrakci prvku z.  
  
## <a name="return-value"></a>Návratová hodnota  
 Jeden prvek v kolekci nebo libovolný element, pokud má kolekce více než jeden prvek; Pokud je kolekce prázdná, vrátí `null`. Pokud je `collection` kolekce typu `Collection<T>`, pak `ANYELEMENT(collection)` je platný výraz, který poskytuje instanci typu `T`.  
  
## <a name="remarks"></a>Poznámky  
 ANYELEMENT extrahuje libovolný prvek z kolekce s více hodnotami. Například následující příklad se pokusí extrahovat element singleton ze sady `Customers`.  
  
```csharp
ANYELEMENT(Customers)  
```  
  
## <a name="example"></a>Příklad  
 Následující [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dotaz používá operátor ANYELEMENT k extrakci prvku z kolekce s více hodnotami. Dotaz je založen na modelu prodeje společnosti AdventureWorks. Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:  
  
1. Použijte postup v tématu [Postup: provedení dotazu, který vrátí výsledky StructuralType](../how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Předat následující dotaz jako argument metodě `ExecuteStructuralTypeQuery`:  
  
 [!code-csharp[DP EntityServices Concepts 2#ANYELEMENT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#anyelement)]  
  
## <a name="see-also"></a>Viz také:

- [Reference k Entity SQL](entity-sql-reference.md)
- [Strukturované typy s možnou hodnotou Null](nullable-structured-types-entity-sql.md)
