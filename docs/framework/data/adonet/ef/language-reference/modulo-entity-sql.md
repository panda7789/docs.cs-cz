---
title: (Modulo) (Entita SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 243ddc4f-3c4e-41e1-a3ef-4ed39e36248b
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: a04b2972c80aff654331aeb319390b6f817374bc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="modulo-entity-sql"></a>(Modulo) (Entita SQL)
Vrátí zbytek rozdělené jiným jeden výraz.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
dividend % divisor  
```  
  
## <a name="arguments"></a>Arguments  
 `dividend`  
 Číselný výraz k rozdělení. `dividend`je jakýkoli platný výraz některého číselné datové typy.  
  
 `divisor`  
 Číselný výraz k rozdělení dělenec podle. `divisor`je jakýkoli platný výraz některého číselné datové typy.  
  
## <a name="result-types"></a>Typy výsledků  
 Edm.Int32  
  
## <a name="example"></a>Příklad  
 Následující dotaz Entity SQL používá k vrácení zbytek jeden výraz rozdělené jiným aritmetického operátoru %. Dotaz je založen na modelu prodej AdventureWorks. Pro zkompilování a spuštění tohoto dotazu, postupujte takto:  
  
1.  Postupujte podle pokynů v [postup: provedení dotazu tohoto vrátí výsledky StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metoda:  
  
 [!code-csharp[DP EntityServices Concepts 2#MODULO](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#modulo)]  
  
## <a name="see-also"></a>Viz také  
 [Reference k Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
