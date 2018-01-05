---
title: "&gt;= (Větší než nebo rovno) (entita SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 70780ac4-0123-4da8-b731-8af856daffe3
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 89e24b3e1a4b707ca60d798889538eb1bcd6a3bc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="gt-greater-than-or-equal-to-entity-sql"></a>&gt;= (Větší než nebo rovno) (entita SQL)
Porovná dva výrazy a určit, zda má levý výraz hodnotu větší než nebo rovna hodnotě pravý výraz.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
expression >= expression  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Jakýkoli platný výraz. Oba výrazy musí mít implicitně převést datové typy.  
  
## <a name="result-types"></a>Typy výsledků  
 `true`Pokud levý výraz má hodnotu větší než nebo rovna hodnotě pravý výraz; v opačném `false`.  
  
## <a name="example"></a>Příklad  
 Následující dotaz Entity SQL používá > = – operátor porovnání k porovnání dvou výrazů k určení, zda levý výraz obsahuje hodnotu větší než nebo rovna hodnotě pravý výraz. Dotaz je založen na modelu prodej AdventureWorks. Pro zkompilování a spuštění tohoto dotazu, postupujte takto:  
  
1.  Postupujte podle pokynů v [postup: provedení dotazu tohoto vrátí výsledky StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metoda:  
  
 [!code-csharp[DP EntityServices Concepts 2#GREATER_OR_EQUALS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#greater_or_equals)]  
  
## <a name="see-also"></a>Viz také  
 [Reference k Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
