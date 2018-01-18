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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: f77989d367509c9d3526bfbdf8ebd50e7d9fc524
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
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
