---
title: "&gt;(Větší než) (Entita SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4cea865c-677c-4b06-99a1-010f2ae2394a
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 9444aec821cd9ab6a6008989de83e929ba5f6baf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="gt-greater-than-entity-sql"></a>&gt;(Větší než) (Entita SQL)
Porovná dva výrazy a určit, zda má levý výraz hodnotu větší než pravý výraz.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
expression > expression  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Jakýkoli platný výraz. Oba výrazy musí mít implicitně převést datové typy.  
  
## <a name="result-types"></a>Typy výsledků  
 `true`Pokud levý výraz obsahuje hodnotu větší než pravý výraz; v opačném `false`.  
  
## <a name="example"></a>Příklad  
 Následující dotaz Entity SQL používá > – operátor porovnání k porovnání dvou výrazů k určení, zda levý výraz obsahuje hodnotu větší než pravý výraz. Dotaz je založen na modelu prodej AdventureWorks. Pro zkompilování a spuštění tohoto dotazu, postupujte takto:  
  
1.  Postupujte podle pokynů v [postup: provedení dotazu tohoto vrátí výsledky StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metoda:  
  
 [!code-csharp[DP EntityServices Concepts 2#GREATER](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#greater)]  
  
## <a name="see-also"></a>Viz také  
 [Reference k Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
