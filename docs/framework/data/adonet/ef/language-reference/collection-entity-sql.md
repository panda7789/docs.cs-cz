---
title: KOLEKCE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 03228bfa-be3a-4ccc-82f8-eee429f85cf1
ms.openlocfilehash: 8cd440571726796ee3d2c91e0d2f6b50571e8e27
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61785324"
---
# <a name="collection-entity-sql"></a>KOLEKCE (Entity SQL)
KOLEKCE – klíčové slovo se používá jenom v definici vloženou funkci. Kolekce funkcí jsou funkce, které pracují na kolekci hodnot a skalární výstup.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
COLLECTION(type_definition)   
```  
  
## <a name="arguments"></a>Arguments  
 `type_definition`  
 Výraz, který vrátí kolekci podporovaných typů, řádky nebo odkazy.  
  
## <a name="remarks"></a>Poznámky  
 Další informace o klíčovém slově KOLEKCE najdete v tématu [definice typu](../../../../../../docs/framework/data/adonet/ef/language-reference/type-definitions-entity-sql.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak pomocí klíčového slova KOLEKCE můžete deklarovat kolekce desetinná čísla jako argument pro vložená funkce dotazu.  
  
 [!code-csharp[DP EntityServices Concepts 2#Collection_GroupPartition](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#collection_grouppartition)]  
  
## <a name="see-also"></a>Viz také:

- [Reference k Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
