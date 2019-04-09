---
title: ANYELEMENT (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 475a9ad6-8c8d-4f49-9970-af273e5360f1
ms.openlocfilehash: 4dcbb80a9a850d193bfa88265a27a43c26869afe
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59196150"
---
# <a name="anyelement-entity-sql"></a>ANYELEMENT (Entity SQL)
Extrahuje element z kolekce s více hodnotami.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
ANYELEMENT ( expression )  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Libovolný platný dotaz výraz, který vrátí kolekce k extrakci prvek z.  
  
## <a name="return-value"></a>Návratová hodnota  
 Jeden prvek v kolekci nebo libovolný element, pokud kolekce obsahuje více než jednu; Pokud kolekce je prázdná, vrátí `null`. Pokud `collection` je kolekce typu `Collection<T>`, pak `ANYELEMENT(collection)` je platný výraz, který vrací instanci typu `T`.  
  
## <a name="remarks"></a>Poznámky  
 ANYELEMENT extrahuje libovolný element z kolekce s více hodnotami. Například následující příklad pokusí extrahovat prvek jednotlivý prvek ze sady `Customers`.  
  
```  
ANYELEMENT(Customers)  
```  
  
## <a name="example"></a>Příklad  
 Následující [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dotaz používá operátora ANYELEMENT extrahovat element z kolekce s více hodnotami. Dotaz je založen na modelu Sales AdventureWorks. Kompilace a spuštění tohoto dotazu, postupujte podle těchto kroků:  
  
1.  Postupujte podle pokynů v [jak: Spustit dotaz, který vrátí výsledky typu StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#ANYELEMENT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#anyelement)]  
  
## <a name="see-also"></a>Viz také:

- [Reference k Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [Strukturované typy s možnou hodnotou Null](../../../../../../docs/framework/data/adonet/ef/language-reference/nullable-structured-types-entity-sql.md)
