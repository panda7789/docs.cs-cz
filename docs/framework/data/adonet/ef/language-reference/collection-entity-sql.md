---
title: KOLEKCE (entita SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 03228bfa-be3a-4ccc-82f8-eee429f85cf1
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 8d078749d20740cdade323edab975ce221e72cfa
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
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
 [Odkaz na entitu SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
