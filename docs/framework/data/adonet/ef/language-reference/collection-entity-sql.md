---
title: KOLEKCE (entita SQL)
ms.date: 03/30/2017
ms.assetid: 03228bfa-be3a-4ccc-82f8-eee429f85cf1
ms.openlocfilehash: 2b13d373e6c54221249b17de4fa91347cbc0f9e6
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32761630"
---
# <a name="collection-entity-sql"></a>KOLEKCE (entita SQL)
Klíčové slovo KOLEKCE se používá pouze v definici vložená funkce. Funkce kolekce jsou funkce, které pracují kolekci hodnot a Vytvoření skalární výstupu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
COLLECTION(type_definition)   
```  
  
## <a name="arguments"></a>Arguments  
 `type_definition`  
 Výraz, který vrátí kolekce podporované typy, řádky nebo odkazy.  
  
## <a name="remarks"></a>Poznámky  
 Další informace o klíčovém slově KOLEKCE najdete v tématu [definic typů](../../../../../../docs/framework/data/adonet/ef/language-reference/type-definitions-entity-sql.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje způsob použití klíčového slova KOLEKCE deklarovat kolekce desetinných míst jako argument pro vložená funkce dotazu.  
  
 [!code-csharp[DP EntityServices Concepts 2#Collection_GroupPartition](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#collection_grouppartition)]  
  
## <a name="see-also"></a>Viz také  
 [Reference k Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
