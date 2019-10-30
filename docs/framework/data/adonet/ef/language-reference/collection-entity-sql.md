---
title: KOLEKCE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 03228bfa-be3a-4ccc-82f8-eee429f85cf1
ms.openlocfilehash: 5a1af1aab8a084b19e48fbdbb159d7ddd8a8dd7c
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039909"
---
# <a name="collection-entity-sql"></a>KOLEKCE (Entity SQL)
Klíčové slovo COLLECTION se používá pouze v definici vložené funkce. Funkce kolekce jsou funkce, které pracují s kolekcí hodnot a tvoří skalární výstup.  
  
## <a name="syntax"></a>Syntaxe  
  
```csharp  
COLLECTION(type_definition)
```  
  
## <a name="arguments"></a>Arguments  
 `type_definition`  
 Výraz, který vrací kolekci podporovaných typů, řádků nebo odkazů.  
  
## <a name="remarks"></a>Poznámky  
 Další informace o klíčovém slově COLLECTION naleznete v tématu [definice typů](type-definitions-entity-sql.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak použít klíčové slovo COLLECTION k deklaraci kolekce desetinných míst jako argumentu pro vloženou funkci dotazu.  
  
 [!code-csharp[DP EntityServices Concepts 2#Collection_GroupPartition](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#collection_grouppartition)]  
  
## <a name="see-also"></a>Viz také:

- [Reference k Entity SQL](entity-sql-reference.md)
